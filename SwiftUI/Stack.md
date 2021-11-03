# Stack

### Stack(스택)은 수직(Vertical)으로 View를 쌓는 VStack, 수평(Horizontal)으로 View를 쌓는 HStack 수평과 수직값을 갖지만 View를 겹쳐서 쌓아 올리는 ZStack이 있습니다

> VStack은 세로로 스택을 쌓는 것 입니다 
```swift
VStack{
  Text("Hello")
  Text("Hello")
  Text("Hello")
}
// Hello
// Hello
// Hello
```
* VStack의 텍스트 크키가 다르면 중앙으로 텍스트가 정렬됩니다
> HStack은 가로로 스택을 쌓는 것 입니다
```swift
HStack{
  Text("Hello")
  Text("Hello")
  Text("Hello")
}
// Hello Hello Hello
```
### alignment로 정렬 기준을 설정할 수 있습니다.
```swift
VStack(alignment: .leading)
```
### spacing로 간격을 설정할 수 있습니다.
```swift
VStack(spacing: 20)
```

> ZStack은 뷰를 겹쳐서 표현할때 사용합니다
```swift
ZStack{
      Color.yellow.edgesIgnoringSafeArea(.all)
      Color.red.frame(width:300,height: 300)
      Color.blue.frame(width:200,height: 200)
}
```
### Spacer()는 선언하면 별도의 옵션을 주지 않는 이상 가능한 모든 영역을 차지하게 됩니다
```swift
VStack{
  Text("Hello")
  Spacer()
// 'Hello       '
```
```swift
VStack {
  Spacer()
  Text("Hello")
// '       Hello'
```

자료: https://medium.com/harrythegreat/swiftui-%ED%8A%9C%ED%86%A0%EB%A6%AC%EC%96%BC-3%ED%8E%B8-%EC%8A%A4%ED%83%9D%EB%8B%A4%EB%A3%A8%EA%B8%B0-e385bff93aa9
