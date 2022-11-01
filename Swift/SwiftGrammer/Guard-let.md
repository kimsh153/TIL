# Guard let

### guard let?

guard 안의 조건문이 참(true)이 아니면 코드가 계속 실행되고, 거짓(false)일 경우에는 else문의 코드를 실행합니다

또한, else 내부 코드에는 return, break, continue, throw 등의 "제어문 전환 명령어"를 사용해야 합니다

```swift
func guardExapmple(_ testBool: Bool?) {
    guard let bool = testBool, bool else {
        print("참이 아니다.")
        return
    }
    
    print("result bool :: \(bool)")
}
```

코드를 보면 guard문 안에 조건이 2가지 있습니다

첫 번째로 guard let bool 변수에 testBool 변수를 담아주었고 두 번째로 bool 입니다

`guardExample(true)`를 실행하면 조건문이 참으로 들어가기 때문에 `print("result bool :: \(bool")`가 실행되게 됩니다

반대로 `guardExample(false)`를 실행하면 조건문이 참이 아니기 때문에 else문을 실행하게 되어 `print("참이 아니다")`가 실행되고 return이 됩니다

### 참고: https://dvlpr-chan.tistory.com/12
