# guard

### guard?

`guard` 문은 뭔가를 검사하여 그 다음에 오는 코드들을 실행할지 말지 결정하는것입니다

if문과 다르게 else를 항상 달아야 합니다

```swift
func guardInFunc (string: String?) {
    guard string != nil else {return}
    print(string!, "second. param", separator: "")
}
guardInFunc("test")
guardInFunc(nil)
```
위의 코드는 **nil 입력을 가드하는 함수**입니다

**nil값이 들어오면** else문을 실행하므로 **print가 실행되지않고 리턴**됩니다

### 참고: https://zetal.tistory.com/entry/swift-guard
