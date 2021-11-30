# Optional

### Optional은 변수의 값이 nil일때 사용합니다 <br><br> Optional은 "?"를 이용하여 표현이 가능합니다
```swift
var name : String?
print(name) // nil

name = "내 이름"
print(name) // Optional("내 이름")
```
### Optional은 옵셔널로 정의한 변수와 옵셔널이 아닌 변수와는 다릅니다.
```swift
var name : String? = "내 이름"
var id : String = name // 컴파일 에러
```
### 위와 같이 **id**는 옵셔널로 사용된 변수가 아니기 때문에 무조건 값이 들어와야 하지만 name은 옵셔널로 정의한 변수이므로 실제 코드가 실행되기 전까지는 값이 있는지 없는지 알 수 없습니다. <br><br> 따라서 Swift 컴파일러는 안전을 위해 **id** 에는 옵셔널로 정의한 변수를 대입할 수 없게 만들었습니다.

### Optional은 기본적으로 Wrap이 되어있는 상태입니다. wrap이 되어있는 변수는 값이 있다고 하더라도 바로 value가 출력되지 않습니다.
```swift
var optionalString : String? = "Hello"
print(optionalString) // Optional("Hello")
```
### 이러한 경우는 저희가 원하는 출력이 아니기 때문에 저희는 wrap을 풀어줘야합니다.<br><br> unwrap을 해주는 !(exclamation mark), 즉 느낌표가 있습니다. 앞에 ?와 다르게 무조건 변수가 있는 상황이 보장된 경우 "!"를 사용합니다.
```swift
var optionalString : String? = "Hello"
print(optionalString!) // Hello
```
### 드디어 우리가 원하는 결과가 나왔습니다!
