# PublishSubject

### PublishSubject는 subscribe 된 시점 이후부터 발생한 이벤트를 전달합니다

```swift
let disposeBag = DisposeBag()

let subject = PublishSubject<String>()
```
### 위의 코드의 <>은 타입 파라미터를 String으로 해준다는 이야기입니다. 그러면 문자열이 포함된 Next이벤트를 받아서 다른 옵저버에게 전달 할 수 있습니다. <br><br> 생성자를 호출할 때는 파라미터를 전달하지 않습니다. 이 Subject는 비어있는 상태로 생성됩니다. 바꿔말해 Subject가 생성되는 시점에는 내부에 아무런 이벤트가 존재하지 않습니다. 그래서 생성 직후 옵저버가 구독을 시작하면 아무런 이벤트도 전달되지 않습니다.
### \*Subject는 옵저버블인 동시에 옵저버입니다.\* &nbsp; 다른 소스로부터 이벤트를 전달 받을 수 있고 다른 옵저버로 이벤트를 전달할 수 있기 때문입니다.

#### 출처:https://www.youtube.com/watch?v=rlnbOzx-r-0&list=PLziSvys01Oek7ANk4rzOYobnUU_FTu5ns&index=3
