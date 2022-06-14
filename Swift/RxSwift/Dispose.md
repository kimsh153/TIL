# Dispose

### Dispose?

observable을 구독하는 변수가 있다고 가정을 하면 구독하는 매서드인 subscribe() 매서드는 disposable을 반환합니다

```swift
let observable = Observable.of(1, 2, 3)

let subscription = observable.subscribe { print($0) }
```

dispose()를 활용하면 원하는 시점에 구독을 해지할 수 있습니다

```swift
subscription.dispose()
```

### 참고: https://jinsangjin.tistory.com/112
