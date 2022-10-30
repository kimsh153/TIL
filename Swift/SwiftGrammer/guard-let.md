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

### 참고: https://dvlpr-chan.tistory.com/12
