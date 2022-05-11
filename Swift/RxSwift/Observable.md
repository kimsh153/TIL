# Observable

`Observable`은 `Observer`에게 `event`를 보내주고 Observer으로부터 `subscribe`를 받아옵니다

Observable의 가장 중요한것은 **이벤트**를 **비동기적**으로 생성하는 기능 이라는것입니다 그리고 계속해서 이벤트를 생성하는데 이러한 과정을 `Emit`이라고 합니다

* 비동기 : 동시에 일어나지 않는다를 의미합니다 요청과 결과가 동시에 일어나지 않을거라는 약속

Observable은 각각의 이벤트들은 숫자나 커스텀한 인스턴스등과 같은 값을 가질 수 있고, 또는 탭과 같은 제스처일 수도 있습니다

### sequence 란?

Observable == Observable sequence == sequence

![image](https://user-images.githubusercontent.com/81547954/167864285-14f95770-9bfa-4f28-9fb2-c2537a45bcc0.png)
> Observable's life cycle

![image](https://user-images.githubusercontent.com/81547954/167864296-d6f47fd9-2af8-4881-9a18-d587ee1ed1de.png)
> "Observable" 결과 사건들은 "sequence"라고 할 수 있음

Observable을 만드는 코드는 다양하게 있습니다

클로저 형식이며 다양한 값(onNext, onCompleted, ...)을 생성할 수 있는 `create` 방법입니다

```swift
Observable<Int>.create { (observer) -> Disposable in
    observer.on(.next(0))
    observer.onNext(1)
    
    observer.onCompleted()
    
    return Disposables.create()
}
```

오직 array타입만 처리하며 각각 요소들을 하나씩 "emit"하는 기능 `from`입니다

```swift
Observable.from([0, 1])
```

타입 추론을 이용하며 "Sequence"생성하는 `of`입니다

```swift
Observable.of([1,2,3])
```

오직 하나의 요소를 포함하는 "Sequence"생성하는 `just`입니다

```swift
Observable.just([1, 2, 3])
```

### 참고: https://ios-development.tistory.com/97
