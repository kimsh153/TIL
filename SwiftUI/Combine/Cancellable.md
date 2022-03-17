# Cancellable

### Cancellabel?

`Cancellabel`은 `프로토콜`입니다

`Cancellabel의 정의`는 `activity` 또는 `action`이 `취소(cancellation)`를 `지원`함을 나타내는 프로토콜입니다

* ### 쉽게 말하면 이걸 채택하면 취소가 가능하다는 말입니다

`cancel()` 을 호출하면 할당 된 모든 리소스가 해제됩니다

## AnyCancellable

AnyCancellable?

갑자기 왜? **AnyCancellable**로 넘어가지 라고 하실 수도 있습니다

하지만! `Sink`를 공부해 보신분들은 다들 한번 쯤 보셨을거라고 생각이 드는데요

#### 바로

<img width="762" alt="스크린샷 2022-03-16 오후 4 00 09" src="https://user-images.githubusercontent.com/81547954/158534241-fda4847b-8df3-489e-affc-078c7b0781e7.png">

`Sink의 result`에서 보셨을 겁니다

그리고 `AnyCancellable` 이 Cancellabel을 프로토콜로 채택하는 `class` 여서 같이 배워보려고 합니다

`AnyCancellable` 은 **취소** 되었을 때, **제공된 closure를 실행**하는 `type-erasing cancellable object` 입니다

**Subscriber 구현**에서는 이 타입을 사용해서 **caller가 publisher를 취소** 할 수 있지만, **Subscription 객체를 사용하여 item을 요청** 할 수 없는 **"cancellation token"** 을 제공할 수 있습니다

`AnyCancellable` 인스턴스는 `deinitialized` 될 때 자동으로 cancel()을 호출합니다

### 참고 : https://zeddios.tistory.com/981, https://milyo-codingstories.tistory.com/46
