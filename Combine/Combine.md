# Combine

### Combine?

Combine은 시간의 흐름에 따라 값을 처리하기 위한 Declarative Swift API를 제공하는 프레임워크입니다

또한 Combine은 Apple에서 제작했기에 install할 필요가 없습니다

Combine은 RxSwift와 비슷하다 생각하시면 편합니다

하지만 **Combine은 애플에서 RxSwift의 역할을 위해 만든 퍼스트파티 프레임워크**입니다

> RxSwift는 서드파티 프레임워크입니다

\* 퍼스트 파티(first party): 하드웨어 생산자가 직접 소프트웨어를 개발하면 보통 퍼스트파티라고 합니다
> 출처: https://m.etnews.com/200302200212

\* 서드 파티(3rd party): Plugin(플러그인), Lib(라이브러리), Framework(프레임워크)등을 말합니다
> 출처: https://drehzr.tistory.com/913


#### Combine의 계층

![image](https://user-images.githubusercontent.com/81547954/158089094-500e6cdb-3b50-46bc-91fa-6d72aa62940f.png)

> 출처 : https://www.hohyeonmoon.com/blog/combine-introduction/

<hr>

### Combine의 장점

* Combine은 System Level에서 구현되어 있어 애플이 아닌 다른 사용자는 사용하지 못하는 부분도 사용할 수 있습니다

* IBAction이나 delegate 같은 엣 방식을 사용하는 것보다 자동 구현이 더 많습니다

* 중첩된 클로저 같은 가독성이 안 좋은 기술을 제거하여 코드를 유지보수하기 쉽게 해줍니다

* Combine프레임워크는 코드 퀄리티를 높이는데 도움을 줍니다

<hr>

### Asynchronous(비동기) 프로그래밍

Combine은 Asynchronous(비동기) 프로그래밍을 더 쉽고 안전하게 할 수 있게 해줍니다

애플은 Asynchronous 프로그래밍을 이미 다음과 같은 것들에서 사용 중입니다.
* NotificationCenter(알림 센터)
* Delegate pattern
* Grand Central Dispatch
* Closures(클로저)


### 참고 : https://www.hohyeonmoon.com/blog/combine-introduction/
