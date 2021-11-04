# Text
### Text()를 사용해서 화면에 글씨를 띄울수 있습니다
```swift
Text("Green")
```
### SwiftUI는 .로 Text를 수정할 수 있습니다
```swift
var body: some View {
  Text("Green")
    .font(.body)
    .fontWeight(.medium)
    .foregroundColor(.green)
}
```
### .font(.body),.fontWeight(.medium),.foregroundColor(.green)은 modifier입니다

