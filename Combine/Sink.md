# Sink

### Sink?

`Sink`는 사전적인 뜻으로는 **(침몰하다, 가라앉다, 빠지다)** 라는 뜻이 있습니다

Combine에서 `Sink` 는 `빠지다` 라는 의미가 제일 비슷할 것 같습니다

* ### subscriber가 publisher에게 빠진다고 의미적으로 생각하시면 좋을 것 같습니다

<img width="791" alt="스크린샷 2022-03-16 오후 3 16 50" src="https://user-images.githubusercontent.com/81547954/158528257-b24e7a67-12ba-4a25-b755-d9d14737c0b9.png">

* 애플 개발자 문서를 보면 `sink`란 `클로저 기반`의 동작이 있는 `subscriber`를 `절대 실패하지 않게` 하는 `publisher`와 연결하는 것이라고 합니다

* 그렇기 때문에 `에러 타입`은 `Never` 일때만 가능하다고 합니다

<img width="762" alt="스크린샷 2022-03-16 오후 4 00 09" src="https://user-images.githubusercontent.com/81547954/158534241-fda4847b-8df3-489e-affc-078c7b0781e7.png">


## Return Value

* 수신 된 값의 할당을 종료할 때 사용하는 Cancellable 인스턴스를 리턴합니다 결과를 Deallocation 한다면 subscription stream을 해제하게 됩니다

## Parameter

* receiveValue : 값을 받을 때 실행하는 클로저 입니다

### 참고 : https://minosaekki.tistory.com/45
