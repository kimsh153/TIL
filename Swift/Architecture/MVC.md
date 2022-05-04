# MVC

### MVC란?

MVC는 iOS App Design Pattern 입니다

MVC는 (Model View Controller)의 약자입니다

![image](https://user-images.githubusercontent.com/81547954/166243023-29335363-5cd5-4695-a72f-62c410ac7651.png)

### Model

먼저 **M**VC에서 `Model`에 대해 알아보겠습니다

* Model에서는 `Data`와 `Logic`을 담당합니다 

* Model은 나의 앱이 정확히 **"무엇"을 할 지** 작성하는 곳 입니다

* Model에는 **Business Logic 을 담당하는 함수들이 정의되고, 처리되는 데이터(클래스, 구조체 등)와 내부 알고리즘이 정의**됩니다

### View

M**V**C에서 `View`에 대해 알아보겠습니다

* View에서는 `User Interface`를 담당합니다

* View는 사용자에게 **"보여지는"** 영역입니다

* View에는 **Storyboard 파일을 비롯해서 인터페이스를 구축하는 영역**입니다

### Controller

MV**C**에서 `Controller`에 대해 알아보겠습니다

* Controller에서는 `Mediator`를 담당하고 있습니다

* Controller는 `Model`과 `View` **사이의 다리**라고 보시면 됩니다 

* Controller는 Model 이 가지고 있는 데이터를 **"어떻게"** 할 것인지 명령을 내립니다

`View`에서 `input events`를 보내면 `Controller`는 이를 받아서 `Model`에 요청을 만들어 보냅니다

`Model`에는 `Data`나 `Logic`이 있어서 이를 처리해 `Controller`에 처리한 `Data`를 보냅니다

마지막으로 `Controller`는 이를 받아 해석하고 `View`에게 관련 부분을 보내서 `View`에서 `User Interface`를 처리합니다

정리하자면 `View`와 `Model`은 다이렉트로 절대 소통하지 못하고, `Controller`를 통해야만 가능합니다

### https://sochubert.github.io/swift/mvc/, https://velog.io/@kevinkim2586/iOS-Swift-%EA%B3%B5%EB%B6%80-6-MVC-Design-Pattern-%EB%B0%8F-%EC%A0%81%EC%9A%A9
