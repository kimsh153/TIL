# Alamofire

### Alamofire?

> Alamofire는 스위프트 기반 HTTP 네트워킹 라이브러리입니다

다시 말하면

> **Alamofir는 HTTP 네트워킹 작업을 할 때 자주쓰는 코드나 함수를 더 쉽게 사용할 수 있게 만든 것**

iOS는 기본적으로 제공하는 HTTP통신 방법이 여러가지가 있습니다

그 중에 URLSession을 이용한 방법을 알아보고 가겠습니다

URLSession은 기본적으로 

```swift
var request = URLRequest(url: URL(string: "https://api.github.com/users")!)
request.httpMethod = "GET"
URLSession.shared.dataTask(with: request) { (data, response, error) in }
```

이러한 형태로 요청이 가능합니다

그리고 GET말고 POST로 바뀌면 아래와 같이 파라미터들을 넘길 수 있습니다

```swift
var request = URLRequest(url: URL(string: "https://api.github.com/users")!)
request.httpMethod = "POST"
let params = ["id":id, "password":password] as Dictionary

do{
  try request.httpBody = JSONSerialization.data(withJSONObject: params, options: [])
} catch {
  return
}

URLSession.shared.dataTask(with: request) { (data, response, error) in }
```

그리고 여기서 Header를 추가하게 된다면 아래와 같이 추가해줘야합니다

```swift
request.addValue("application/json", HTTPHeaderField: "Content-Type")
request.addValue("application/json", forHTTPHeaderField: "Accept")
```

그리고 성공 실패 케이스도 나눠야합니다

```swift
// 요청받기
var request = URLRequest(url: URL(string: "https://api.github.com/users")!)
request.httpMethod = "POST"
let params = ["id":id, "password":password] as Dictionary

do {
  try request.httpBody = JSONSerialization.data(withJSONObject: params, options: [])
} catch {
  return
}

// Header 추가
request.addValue("application/json", forHTTPHeaderField: "Content-Type")
request.addValue("application/json", forHTTPHeaderField: "Accept")

// 성공 실패 구분
URLSession.shared.dataTask(with: request, completionHandler: {(data, response, error) -> Void in
  if let response = response as? HTTPURLResponse, 200...299 ~= response.statusCode {
    // success
  } else {
    // failure
    }
})
```

이런식의 코드는 가동석은 물론이며, 조금의 설정만 바꾸면 많은 것이 변경되어야 해서 여러모로 불편한점이 있습니다

**이러한 불편한 점을 개선한 라이브러리가 `Alamofire`입니다**

### Alamofire 설치법

**CocoaPods**

```
pod 'Alamofire'
```

### https://www.zehye.kr/ios/2020/04/01/12iOS_alamofire/
