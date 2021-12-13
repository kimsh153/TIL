# Observable

`Observable`은 `Observer`에게 `event`를 보내주고 Observer으로부터 `subscribe`를 받아옵니다.

Observable의 가장 중요한것은 **이벤트**를 **비동기적**으로 생성하는 기능 이라는것입니다. 그리고 계속해서 이벤트를 생성하는데 이러한 과정을 `Emit`이라고 합니다.

* 비동기 : 동시에 일어나지 않는다를 의미합니다. 요청과 결과가 동시에 일어나지 않을거라는 약속

Observalbe은 각각의 이벤트들은 숫자나 커스텀한 인스턴스등과 같은 값을 가질 수 있고, 또는 탭과 같은 제스처일 수도 있습니다

Observalbe을 만드는 코드는 두가지가 있습니다.<br>
하나는 수동적으로 `create`하여 만드는 방법입니다.

```swift
Observable<Int>.create { (observer) -> Disposable in
    observer.on(.next(0))
    observer.onNext(1)
    
    observer.onCompleted()
    
    return Disposables.create()
}
```

그리고 하나는 `from`자동적으로 만들어 주는 방법입니다.

```swift
Observable.from([0, 1])
```
