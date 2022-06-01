# RxSwift

### RxSwift란?
RxSwift는 관찰 가능한 연속성(순차적)형태와 함수형태의 연산자를 이용해서 비동기&이벤트를 위한 코드로 구성하고 있는 라이브러리입니다

### RxSwift를 왜 사용하는 걸까?

#### 1.반응형 패러다임이 제공하는 명확함
* 비동기를 동기화가 된것처럼 사용할 수 있습니다

#### 2.일관성이 없는 비동기 코드를 해결
* 어떤 곳에서는 DispatchQueue, 어떤 곳에서는 OperationQueue...
* 하나의 비동기 코드로 개발이 가능합니다

#### 3. 확장 불가능한 아키텍처 패턴을 해결
* 일관성이 없는 비동기 코드를 작성하게 되어 서로 다르게 구현한 로직을 조합하거나 확장하기에 어려운 부분을 해결하였습니다
* Rx로 일관된 코드를 작성하면서 아키텍처의 확장이 가능합니다

#### 4. 콜백지옥에서 벗어나기 좋음
* 자세한건 https://www.youtube.com/watch?v=jCT-eUaD-d4 참고

#### 5. Rx에겐 뭔가 특별한 것이 있다

### 설치

**Cocoapod**

```swift
pod "RxSwift"
```

### 참고: https://ios-development.tistory.com/95, https://medium.com/@jang.wangsu/ios-swift-rxswift-%EC%99%9C-%EC%82%AC%EC%9A%A9%ED%95%98%EB%A9%B4-%EC%A2%8B%EC%9D%84%EA%B9%8C%EC%9A%94-5c9995f47bab
