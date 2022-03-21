# ReactorKit

### ReactorKit?

**ReactorKit은 반응형 단방향 앱을 위한 프레임워크**로, **StyleShare와 Kakao를 비롯한 여러 기업에서 사용하고 있는 기술**입니다
<hr>

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

### 참고 : https://ios-development.tistory.com/782, https://medium.com/styleshare/reactorkit-%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0-c7b52fbb131a
