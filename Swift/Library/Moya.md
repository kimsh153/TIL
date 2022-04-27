# Moya

### Moya라이브러리가 왜 만들어졌나

iOS에서 네트워킹을 구현하는 가장 기본적인 방법은`URLSession`을 사용하는 것입니다

`URLSession`은 로우레벨의 코드를 작성할 수 있고,
다른 프레임워크를 사용할 필요가 없다는 장점이 있지만,
사용이 복잡하고 코드의 가독성이 좋지 않아서 Foundation Networking을 기반으로한 인터페이스를 제공해 네트워킹 작업을 단순화 해주는 라이브러리인 `Alamofire`를 많이 사용합니다

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

`Moya`는 `MoyaProvider<TargetType>`으로 request를 수행하기 때문에,

정의한 API가 `TargetType` 프로토콜을 구현해야합니다

<br>

extension을 만들어 `TargetType`프로토콜을 체택하면,

아래와 같은 프로파티들을 구현 해야합니다

* baseURL: 서버의 endpoint 도메인
* path: 도메인 뒤에 추가 될 path(/users, /documents, ...)
* method: HTTP method(GET, POST, ...)
* sampleData: 테스트용 Mock Data
* task: request에 사용될 파라미터 .requestPlain: no param, .requestParametrs(parameter:,encoding:)
* headers: HTTP Header

### 설치법

**Cocoapod**

```
pod 'Moya'
```

### 참고 : https://velog.io/@dlskawns96/iOS-Moya%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%9C-%EB%84%A4%ED%8A%B8%EC%9B%8C%ED%82%B9-Swift-Http-%ED%86%B5%EC%8B%A0
