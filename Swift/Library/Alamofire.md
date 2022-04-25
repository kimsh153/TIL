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

그럼 한번 확인해 보기위해 Alamofire를 이용하여 위에 코드와 똑같은 로직을 짜보겠습니다

```swift
Alamofire.request("https://api.github.com/users", method: .get, parameters: [:], encoding: URLEncoding.default, headers: ["Content-Type":"application/json", "Accept":"application/json"])
            .validate(statusCode: 200..<300)
            .responseJSON { (response) in
            if let JSON = response.result.value
            {
                print(JSON)
            }
        }
```
이게 끝입니다!

**위에서 일일이 추가 하던 것과는 다르게 확연히 다른 차이를 볼 수 있습니다**

**훨씬 간결해서 보기도 편합니다**

뿐만 아니라

**request가 성공인지 실패인지를 필터를 하는 `validate(statusCode:200..<300)`로 200~299사이의 statusCode결과만 받아올 수 있는 간편한 기능도 지원합니다**

이제는 다른 예제를 통해 GET메서드 어떤식으로 작성하는지 하나씩 뜯어보겠습니다

이번 예제는 JSON 샘플 데이터를 제공하는 사이트를 통해 데이터를 가져와 보겠습니다

> https://jsonplaceholder.typicode.com/todos/1

```swift
let url = "https://jsonplaceholder.typicode.com/todos/1"
AF.request(url,
           method: .get,
           parameters, nil,
           encoding: URLEncoding.default,
           headers: ["Content-Type":"application/json", "Accept":"application/json"]),
      .validate(statusCode: 200..<300)
      .responseJSON { (json) in
          print(json)
    }
```

### https://www.zehye.kr/ios/2020/04/01/12iOS_alamofire/
