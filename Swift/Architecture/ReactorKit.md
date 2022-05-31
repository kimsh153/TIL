# ReactorKit

### ReactorKit?

ReactorKit은 반응형 및 단방향 Swift 애플리케이션 아키텍처입니다

### ReactorKit 개념

* RxSwift의 강점인 비동기 처리에 편리한 코드
* API를 통해 앱에서 연속적인 페이지 로드할 때 이전 페이지를 기록해놓아야 하듯이, 이전 페이지를 기록하는 \`**상태**\` 컴포넌트가 따로 관리되게끔 설계된 구조
* \`**상태**\` 라는 컴포넌트 추상화 개념이 적용되어 있고, 컴포넌트 간 결합도가 낮기 때문에 테스트하기에 용이한 구조
* MVVM과 같은 아키텍처는 규격화된게 없어서 개발자, 회사마다 모두 달라 일관적이지 않은 반면에 ReactorKit은 형식이 갖추어진 형태

### 데이터 흐름

![image](https://user-images.githubusercontent.com/81547954/159207895-9e4156e2-72c9-442b-8810-62537f7ebb69.png)

<br>

ReatorKit에는 `뷰(View)`와 `리액터(Reactor)`라는 개념이 존재합니다

### View

`View`는 **상태를 표현**합니다(View Controller나 Cell도 모두 뷰에 해당합니다)

`View`는 사용자 인터랙션을 추상화하여 리액터에 전달하고, 리액터에서 전달받은 상태를 각각의 뷰 컴포넌트에 바인드합니다

`View`는 비즈니스 로직을 수행하지 않습니다

### Reactor

`Reactor`는 View의 **상태를 관리**합니다

`Reactor`는 View에서 액션을 전달받으면 비즈니스 로직을 수행한 뒤 상태를 변경하여 다시 View에 전달합니다

`Reactor`는 UI 레이어에서 독립적이기 때문에 비교적 테스트하기 쉽습니다

### View 코드 작성

`View`프로토콜을 적용하면 뷰를 정의할 수 있습니다 `DisposeBag` 속성과 `bind(reactor:)` 메서드를 필수로 정의해야 합니다

```swift
import ReactorKit
import RxSwift

class UserViewController: UIViewController, View {
  var disposeBag = DisposeBag()

  func bind(reactor: UserViewReactor) {
  }
}
```

이 프로토콜을 정의하면 `reactor` 속성이 자동으로 생성됩니다 이 속성에 새로운 값이 지정되면 `bind(reactor:)` 매서드가 자동으로 호출됩니다

이곳에는 사용자 인터랙션을 바인드하거나, 리액터의 상태를 각각의 뷰 컴퓨넌트에 바인드하는 코드를 작성합니다

```swift
func bind(reactor: UserViewReactor) {
  // Action
  self.followButton.rx.tap
    .map { Reactor.Action.follow }
    .bind(to: reactor.action)
    .disposed(by: self.disposeBag)

  // State
  reactor.state.map { $0.isFollowing }
    .distinctUntilChanged()
    .bind(to: self.followButton.rx.isSelected)
    .disposed(by: self.disposeBag)
}
```

### Reactor 코드 작성

리액터를 정의하기 위해서는 `Reactor`프로토콜을 사용합니다

사용자 인터랙션을 표현하는`Action`과 뷰의 상태를 표현하는 `State`, 그리고 상태를 변경하는 가장 작은 단위인 `Mutation`을 클래스 내부에 필수로 정의해야 합니다

또한 가장 첫 상태를 나타내는 `initialState`가 필요합니다

```swift
import ReactorKit
import RxSwift

final class UserViewReactor: Reactor {
  enum Action {
    case follow
  }

  enum Mutation {
    case setFollowing(Bool)
  }

  enum State {
    var isFollowing: Bool
  }

  let initialState: State = State(isFollowing: false)
}
```

Action이나 State와 달리 Mutation은 리액터 클래스 밖으로 노출되지 않습니다

대신 클래스 내부에서 Action과 State를 연결하는 역할을 수행합니다

Action이 리액터에 전달되면 두 단계를 거쳐서 뷰의 상태를 변경합니다

![image](https://user-images.githubusercontent.com/81547954/171071915-3fa68c63-5fe0-49d5-9588-0742ccd254a9.png)

`mutate()` 함수에서는 Action 스트림을 Mutation 스트림으로 변환하는 역할을 합니다

이곳에서 네트워킹이나 비동기로직 등의 사이드 이펙트를 처리합니다

그 결과로 Mutation을 방출하면 그 값이 `reduce()` 함수로 전달됩니다

`reduce()`함수는 이전 상태와 Mutation을 받아서 다음 상태를 반환합니다

```swift
func mutate(action: Action) -> Observable<Mutation> {
  switch action {
    case .follow:
      return UserService.follow()
        .map { Mutation.setFollowing(true) }
        .catchErrorJustReturn(Mutation.setFollowing(false))

    case .unfollow:
      return UserService.unfollow()
        .map { Mutation.setFollowing(false) }
        .catchErrorJustReturn(Mutation.setFollowing(true))
  }
}

func reduce(state: State, mutation: Mutation) -> State {
  var newState = state
  switch mutation {
  case let setFollowing(isFollowing):
    newState.isFollowing = isFollowing
  }
  return newState
}
```

### 참고 : https://github.com/ReactorKit/ReactorKit, https://medium.com/styleshare/reactorkit-%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0-c7b52fbb131a, https://ios-development.tistory.com/782
