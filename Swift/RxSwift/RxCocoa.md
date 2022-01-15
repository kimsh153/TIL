# RxCocoa

### RxCocoa?

* RxCocoa란 기존 Cocoa Framework에 Rx기능을 합친 RxSwift기반 라이브러리입니다.
* RxSwift와 별도로 추가해주어야 사용할 수가 있습니다.
* RxCocoa는 단방향성을 갖고 있다.
* Producer는 값을 생성하고, Consumer는 값을 처리합니다.

![image](https://user-images.githubusercontent.com/81547954/149351981-bf23928f-e67b-4278-ba2e-f775b1342cdf.png)

### ObserverType, ObservableType

`ObserverType`: **값을 주입시킬 수 있는 타입**

`ObservableType`: **값을 관찰할 수 있는 타입**

### ControlProperty?

`subject`와 같이 프로퍼티에 **새 값을 주입**시킬 수 있고(ObserverType) **값의 변화도 관찰**할 수 있는 타입(ObservableType).

`ControlProperty`는 **ControlPropertyType을 준수**하고, `ControlPropertyType`은 **ObservableType과 ObserverType을 준수**합니다.

### Binder

Binder는 ObserverType을 따릅니다

Binder는 옵저버 타입으로 3가지 특징이 있습니다.

첫번째로 반드시 메인스케쥴러에서 실행됩니다

두번째로 에러 이벤트를 따로 방출하지 않고 로그로만 출력됩니다

세번째로는 옵저버타입이기 때문에 새로운 값을 전달할 수 있지만 구독자를 추가할 수는 없습니다

### Bind

Binder Observer를 사용해서 UI와 Observable을 하나로 묶는 행위입니다

쉽게 설명하면 Observable이 이벤트를 방출하고 subscribe를 통해 관찰을 했습니다

그런데 bind는 옵저버블과 관찰하는 옵저버를 그냥 하나로 묶어버리는 것입니다

### Traits

Traits는 UI 처리에 특화된 Observable 입니다.
RxCocoa가 제공하는 Traits는 4가지가 있습니다

* ControlProperty : 컨트롤에 data를 binding 하기 위해 사용합니다
* ControlEvent : 컨트롤의 event를 수신하기 위해 사용합니다
* Driver : error를 방출하지 않고 메인스레드에서 처리됩니다
* Signal : Driver와 거의 동일하나 자원을 공유하지 않습니다.

RxCocoa에서 Traits는 4가지 특징을 갖습니다

* error를 방출하지 않습니다
* 메인 스케줄러에서 observe 됩니다
* 메인 스케줄러에서 subscribe 됩니다
* Signal을 제외한 나머지 Traits들은 자원을 공유합니다


### 참고 :  <br> 1. https://velog.io/@hansangjin96/iOS-RxCocoa%EB%9E%80<br> 2. https://duwjdtn11.tistory.com/628 <br> 3. https://fomaios.tistory.com/entry/RxCocoa-bind%EB%9E%80
