# Then

### Then은 closure를 사용해서 원하는 인스턴스를 생성해서 처리를 해주는 것이라고 합니다.
말로 설명하는것보다 코드로 설명하는게 더 빠를거 같아서 코드로 설명하겠습니다.

### Then쓰기 전 코드
```swift
let label : UILabel = {
  let label = UILabel()
  lable.textAlignment = .center
  label.textColor = .black
  label.text = "Hello, world!"
  return label
}()
```

### Then쓴 후 코드
```swift
let label = UILable().then {
  $0.textAlignment = .center
  $0.textColor = .black
  $0.text = "Hello, world!"
}
```

이렇게 코드가 간단하고 쉽고 짧고 효율적으로 바뀌게 됩니다.

## install하는법

**cocoapod을 기준으로 말하겠습니다.**

```swift
pod 'Then'
```
