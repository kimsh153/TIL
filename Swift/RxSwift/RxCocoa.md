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

### 참고 :  <br> 1. https://velog.io/@hansangjin96/iOS-RxCocoa%EB%9E%80<br> 2.https://duwjdtn11.tistory.com/628
