# Subject

### Subject?

`Subject`는 `Publisher`의 일종입니다 

<img width="488" alt="스크린샷 2022-03-16 오전 8 10 00" src="https://user-images.githubusercontent.com/81547954/158487016-8ab71fc1-c70a-4430-8aa4-5ada69cfc2b8.png">

`Subject`는 `Publisher` protocal을 체택한걸 볼 수 있습니다

`Subject`와 `Publisher`의 차이점은 값을 외부에서 값을 방출할 수 있다는 점입니다

<hr>

### Subject를 정의해보면

> ### **send(\_:)를** 통해 **stream**에 값을 주입할 수 있는 **publisher**

`Publisher`는 외부에서 값을 던질 수 없고 `Publisher` 내부에서 생성되어 나오는 값들만 받아서 처리했습니다

![1_nHfRUNLtQZTuI2-uo6sYyA](https://user-images.githubusercontent.com/81547954/161383953-1f3029b0-dd4b-494e-ad33-3e7ccba5d76c.png)
> https://sujinnaljin.medium.com/combine-subject-a974340cb582

하지만 `publisher` 가 아닌 `subject`를 사용하면 `send(_:)` 를 통해 외부에서도 값을 주입할 수 있게 해줍니다

* `send(_:)` 는 `Subject` protocol에 정의되어 있습니다

![1_Lb-eLQn1Oib_jnF1Yi6LlA](https://user-images.githubusercontent.com/81547954/161384036-90a5765c-c4a5-4c64-9927-9729c75b0c9c.png)
> https://sujinnaljin.medium.com/combine-subject-a974340cb582

Subject의 종류는 크게 `PassthroughSubject`와 `CurrentValueSubject`로 나뉩니다!

먼저 PassthroughSubject에 대해 알아보겠습니다

### PassthroughSubject

<img width="687" alt="스크린샷 2022-05-21 오후 5 24 41" src="https://user-images.githubusercontent.com/81547954/169643005-d7f27948-ae98-4704-891e-1c51cc6a47c7.png"> > https://sujinnaljin.medium.com/combine-subject-a974340cb582

에제를 바로 보겠습니다

```swift
// 1. String과 Never 타입의 PassthroughSubject 객체를 생성합니다
let subject = PassthroughSubject<String, Never>()

// 2.sink 를 이용하여 subscription1을 생성합니다
let subscription1 = subject
	.sink(
    	receiveCompletion: { completion in
      		print("Received completion (1)", completion)
    	},
    	receiveValue: { value in
      		print("Received value (1)", value)
    	}
  	)
// 3.sink 를 이용하여 subscription2을 생성합니다
let subscription2 = subject
	.sink(
    	receiveCompletion: { completion in
      		print("Received completion (2)", completion)
    	},
    	receiveValue: { value in
      		print("Received value (2)", value)
    	}
  	)
//4. 값을 보냅니다
subject.send("Hello")
subject.send("World")
```

이렇게 `PassthroughSubject`를 사용하면 `send(_:)`를 통해 필요에 따라 새로운 값을 게시할 수 있습니다

`broadcast`니까 해당 `subject`를 구독하고 있는 모든 `subscriber`에게 값을 보내게 되니 출력은 이런식으로 되게 됩니다

```
Received value (1) Hello
Received value (2) Hello
Received value (1) World
Received value (2) World
```

### 참고 : https://sujinnaljin.medium.com/combine-subject-a974340cb582, https://zeddios.tistory.com/965
