# lazy

### lazy는 지연을 뜻합니다. 인스턴스가 초기화 되는 시점에 초기화가 되는게 아니라 속성에 처음 접근하는 시점에서 초기화됩니다.
> 코드 선언 방법
```swift
lazy var iOS: String = { }()
```
### lazy를 왜 사용하는가? <br> lazy변수는 처음 사용되기 전까지 연산이 되지 않기 때문에 메모리를 효율적으로 쓸 수 있습니다. 
### 예를 들어 유튜브의 영상들을 누르기 전에 전부 가져와 버리면 그만큼 딜레이가 생길 수 있습니다. 그래서 <br> 처음 사용되기 전까지 로드되지 않다가 영상을 보려고 클릭하면 해당 영상을 서버로부터 로드되는 것 입니다.

참고자료:https://baked-corn.tistory.com/45