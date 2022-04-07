# RxFlow

## RxFlow?

iOS를 개발을 하면서 화면을 구성하는 방법과 **화면에서 화면간 이동하는 방법**은 다양합니다.

* App을 설계 할 때 
* 하나의 피쳐,하나의 화면 단위에서의 문제를 해결할때 
* 보여지는(Presnt)영역과, 화면(View)를 구현하기 위한 영역을 설계할 때

MVC,MVP,MVVM,ReactorKit등의 아키텍쳐나 아키텍쳐 프레임을 사용해서 해결하곤 합니다.

**그 외의 영억 중에 화면의 연결에 대한 부분의 문제점**을 해결하기 위해 `Coordinator`,`Router`등등의 Pattern을 사용합니다.

* RxFlow는 Coordinator Pattern 기반의 구현체입니다
* RxFlow는 화면간의 연결, DI(의존성 분리)를 해결한 것입니다.

### 이렇게 RxFlow를 이용하여 화면 연결에 대한 부분의 문제점을 해결하고 DI(의존성 분리)를 해결하기 위하여 사용됩니다.

> RxFlow 정의
```
RxFlow is a navigation framework for iOS applications 
based on a Reactive Flow Coordinator pattern
```
> 구글번역기
```
RxFlow는 Reactive Flow Coordinator 패턴을 기반으로 하는 iOS 애플리케이션용 탐색 프레임워크입니다.
```
라고 합니다.

### RxFlow가 목표로 하는것 

* 스토리보드를 유닛 단위로 쪼개서 **UIViewController의 재사용성**을 키웁니다.
* 네비게이션의 **흐름(context)에 맞게 UIViewController를 다른 방식으로 보여줄** 수 있습니다.
*  **의존성 주입(Dependency Injection)** 을 쉽게 구현할 수 있습니다
> 의존성 주입(DI)
* UIViewController에 있는 **모든 네비게이션 매커니즘을 삭제**합니다.
* **반응형 프로그래밍(Reactive Programming) 사용을 촉진**합니다.
* 네비게이션에서 일어나는 대부분의 케이스를 처리하면서 **선언형**으로 표현할 수 있습니다.
* 어플리케이션을 **네비게이션의 논리적인 블록**으로 나눌 수 있습니다.
이렇게 RxFlow가 목표하는 사항이 많습니다.

### RxFlow의 이해를 도와주는 6가지 키워드

![image](https://user-images.githubusercontent.com/81547954/146878411-5ad0d58c-4027-4e32-b56f-74ea9278bb8c.png)

1.`Flow`는 Controller의 생성과 의존성 주입 그리고 화면 이동처리 등의 개발자가 구현해 주어야되는 핵심 공간이 되는 부분입니다.

2.`Step`은 enum 입니다. 어떤 화면으로 이동할거야의 상태 값의 정의 부분입니다.

3.`Stepper`는 2번의 Step을 발생시킬 수 있는 Protocol(Interface)입니다. 원하는 인스턴스에 종속성을 부여하면 됩니다.

4.`Presentable`은 Root가 되는 UIViewController라고 생각하면 됩니다. Coordinator도 무엇을 컨트롤해야되는지, 알아야 제어할것입니다.

5.`Flowable`은 Coordinator에게 구체적으로 4번의 Presentable과 3번의 Stepper가 어떻게 조합되고 역할을 하는 지를 알려주는 것을 설정해 줍니다.

6.`Coordinator`는 이 조합들을 잘 섞어주는 역할만을 하는 조정자,진행자의 역할만 합니다.

![image](https://user-images.githubusercontent.com/81547954/146878471-167a42ad-8496-481b-8379-d256e407c4a7.png)

참고 : https://medium.com/@jang.wangsu/ios-swift-rxflow-%EB%A5%BC-%EC%86%8C%EA%B0%9C%ED%95%A9%EB%8B%88%EB%8B%A4-e433838aa32b
