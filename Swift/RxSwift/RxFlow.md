# RxFlow

## RxFlow?

iOS를 개발을 하면서 화면을 구성하는 방법과 **화면에서 화면간 이동하는 방법**은 다양합니다.

* App을 설계 할 때 
* 하나의 피쳐,하나의 화면 단위에서의 문제를 해결할때 
* 보여지는(Presnt)영역과, 화면(View)를 구현하기 위한 영역을 설계할 때

MVC,MVP,MVVM,ReactorKit등의 아키텍쳐나 아키텍쳐 프레임을 사용해서 해결하곤 합니다.

**그 외의 영억 중에 화면의 연결에 대한 부분의 문제점**을 해결하기 위해 `Coordinator`,`Router`,`Pattern` 등을 사용합니다.

* RxFlow는 Coordinator Pattern 기반의 구현체입니다
* RxFlow는 화면간의 연결, DI(의존성 분리)를 해결한 것입니다.

### 이렇게 RxFlow를 이용하여 화면 연결에 대한 부분의 문제점을 해결하고 DI(의존성 분리)를 해결하기 위하여 사용됩니다.

> RxFlow 정의
```
RxFlow is a navigation framework for iOS applications 
based on a Reactive Flow Coordinator pattern
```
구글번역기
```
RxFlow는 Reactive Flow Coordinator 패턴을 기반으로 하는 iOS 애플리케이션용 탐색 프레임워크입니다.
```
라고 합니다.
