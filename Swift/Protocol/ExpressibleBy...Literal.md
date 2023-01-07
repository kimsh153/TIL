# ExpressibleBy...Literal

### ExpressibleBy...Literal?

다른 프로젝트를 뜯어보던중 발견하게 된 enum의 프로토콜로 써져있던 ExpressibleByStringLiteral을 발견하게 되었습니다

새로운 프로토콜을 발견하여 한번 찾아보게 되었습니다

들어가기에 앞서 Swift에는 Literal이라는 것이 있습니다

### Literal?

Literal이란, **value 타입의 소스 코드 표현**입니다

```swift
let number: Int8 = 39
```
이런식으로 Int8이라고 명시해주면 39의 타입은 Int8이라고 추론하게 됩니다

```swift
let number = 39
```
위 코드처럼 명시를 해주지 않으면 **Swift는 default type을 보고 타입을 결정**하게 됩니다

따라서 number의 타입은 integer literal의 default type인 Int형이 됩니다

<br>

근데 integer literal의 default type은 Int형인데 어떻게 타입을 명시적으로 선언한다고 해서 Int -> Int8로 타입을 바꿀 수 있었을까요?

바로 그때 사용한것이 ExpressibleBy...Literal프로토콜 입니다!

### 참고: https://phillip5094.tistory.com/5
