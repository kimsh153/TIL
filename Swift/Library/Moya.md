# Moya

![diagram](https://user-images.githubusercontent.com/81547954/165767944-9bea0e7f-80c8-4caa-b7b4-91de0e7b436e.png)

### Moya라이브러리가 왜 만들어졌나

iOS에서 네트워킹을 구현하는 가장 기본적인 방법은`URLSession`을 사용하는 것입니다

`URLSession`은 로우레벨의 코드를 작성할 수 있고,

다른 프레임워크를 사용할 필요가 없다는 장점이 있지만,

사용이 복잡하고 코드의 가독성이 좋지 않아서 `Foundation Networking`을 기반으로한 인터페이스를 제공해 

네트워킹 작업을 단순화 해주는 라이브러리인 `Alamofire`를 많이 사용합니다

> 로우레벨이란? 컴퓨터가 이해하기 쉽게 작성된 프로그래밍 언어이다 예를 들어 기계어와 어샘블리어같은것이 있다

> Foundation 

### URLSession의 장단점
**장점**
* 로우레벨의 코드 작성
* 다른 프레임워크 사용 X

**단점**
* 사용이 복잡함
* 코드의 가독성이 떨어짐

### Alamfire
`URLSession`의 단점을 보완한 네트워킹 작업 라이브러리

**단점**

* 유지보수 및 유닛테스트가 힘듬

### Moya

Alamofire의 단점을 보완한 네트워킹 작업 라이브러리

* Network Layer를 템플릿화 하여 재사용성을 높힘
* 개발자가 request, response에만 신경쓰도록 해줌

### Moya 설치

CocoaPods으로 설명하겠습니다

```swift
pod 'Moya'

또는

pod 'Moya', '~> 15.0'

또는

pod 'Moya/RxSwift', '~> 15.0'

또는

pod 'Moya/ReactiveSwift', '~> 15.0'

또는

pod 'Moya/Combine', '~> 15.0'
```

### Moya 코드 작성

`Moya`에서 제공해주는 <a href="https://github.com/Moya/Moya/blob/master/docs/Examples/Basic.md">템플릿</a>을 이용하면 좋습니다

그러면 `Moya`를 통해 네트워킹을 하기위해 <a href="http://www.icndb.com/">ICNDb.com</a> 이 사이트는 랜덤한 조크를 리턴해주는 api입니다

### API target enum

새로운 파일을 하나 만들고 `JokeAPI.swift`

enum을 하나 선언해서 사용될 target들을 작성합니다

```swift
// JokeAPI.swift
import Moya

enum JokeAPI {
    case randomJokes(_ firstName: String? = nil, _ lastName: String? = nil)
}
```
이 예제에서는 이름을 파라미터로 받아 조크의 이름을 만들어주는 target을 하나만 사용하겠습니다

### TargetType 구현

`Moya`는 `MoyaProvider<TargetType>`으로 request를 수행하기 때문에,

위에서 정의한 API가 `TargetType` 프로토콜을 구현해야합니다

<br>

extension을 만들어 `TargetType`프로토콜을 체택하면,

아래와 같은 프로파티들을 구현 해야합니다

* baseURL: 서버의 endpoint 도메인(url)
* path: 도메인 뒤에 추가 될 path(/users, /documents, ...)
* method: HTTP method(GET, POST, ...)
* sampleData: 테스트용 Mock Data
* task: request에 사용될 파라미터 .requestPlain: no param, .requestParametrs(parameter:,encoding:)
* headers: HTTP Header

```swift
extension JokeAPI: TargetType {
    var baseURL: URL {
        return URL(string: "https://api.icndb.com")!
    }
    
    var path: String {
        switch self {
        case .randomJokes(_, _):
            return "/jokes/random"
        }
    }
    
    var method: Moya.Method {
        switch self {
        case .randomJokes(_, _):
            return .get
        }
    }
    
    var sampleData: Data {
        switch self {
        case .randomJokes(let firstName, let lastName):
            let firstName = firstName
            let lastName = lastName
            
            return Data(
                """
                {
                    "type": "success",
                    "value": {
                        "id": 107,
                        "joke": "\(firstName)\(lastName) can retrieve anything from /dev/null."
                    }
                }
                """.utf8
            )
        }
    }
    
    var task: Task {
        switch self {
        case .randomJokes(let firstName, let lastName):
            let params: [String: Any] = [
                "firstName": firstName,
                "lastName": lastName
            ]
            return .requestParameters(parameters: params, encoding: URLEncoding.queryString)
        }
    }
    
    var headers: [String : String]? {
        return ["Content-type": "application/json"]
    }
}
```

위에처럼 `switch`문을 통해 여러 target에 맞는 프로퍼티들을 정의해줄 수 있습니다

### 3.Request 보내고 Response 받아서 처리하기

이제 위에서 정의한 `TargetType`을 이용해 request를 보내는 코드를 작성하겠습니다

response 시 받는 JSON의 형태는 아래와 같습니다

```
{
    "type": "success",
    "value": {
        "id": 268,
        "joke": "Time waits for no man. Unless that man is John Doe."
    }
}
```

이와 대응되는 Decodable struct를 정의합니다 

model을 짜는 작업을 합니다

```swift
struct Joke: Decodable {
    var type: String
    var value: Value
    
    struct Value: Decodable {
        var id: Int
        var joke: String
    }
}
```

이제 request를 보내고 받은 response를 text view에 표시해보도록 하겠습니다

```swift
class ViewController: UIViewController {
    @IBOutlet var jokeTextView: UITextView!
    
    override func viewDidLoad() {
        super.viewDidLoad()
        
        let provider = MoyaProvider<JokeAPI>()
        provider.request(.randomJokes("GilDong", "Hong")) { (result) in
            switch result {
            case let .success(response):
                let result = try? response.map(Joke.self)
                self.jokeTextView.text = result?.value.joke
            case let .failure(error):
                print(error.localizedDescription)
            }
        }
    }
}
```

**네트워크 요청을 `Moya`를 통해 처리하면 enum을 활용해 안전한 방식으로 캡슐화된 요청을 할 수 있다는 장점이 있고, 코드를 직관적이고 쉽게 작성할 수 있다는 장점이 있습니다**

### 참고 : https://velog.io/@dlskawns96/iOS-Moya%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%9C-%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%82%B9-Swift-Http-%ED%86%B5%EC%8B%A0
