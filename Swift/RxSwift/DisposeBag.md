# DisposeBag

### DisposeBag

dispose()는 구독하는 것 마다 별도로 관리를 해줘야하는 번거로움이 있습니다

disposeBag을 활용하면 여러개의 구독을 한번에 해제할 수 있습니다

subscribe가 반환하는 disposable이 disposeBag에 담기고 disposeBag이 해제될때 disposable이 모두 해제되는 것입니다

```swift
let disposeBag = DisposeBag()
let observable = Observable.of(1, 2, 3)

let subscription = observable
		.subscribe { print($0) }
                .disposed(by: disposeBag)
```

### DisposeBag은 언제 해제될까요

**1.var bag = nil 처럼 직접 해제<Br>**
**2.class가 deinit 되면서 자동 해제**

### 참고: https://jinsangjin.tistory.com/112
