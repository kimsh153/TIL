# Equatable

### Equatable?

일단 <a href="https://developer.apple.com/documentation/swift/equatable">애플공식문서</a>를 통해 Equatable에 대해 알아보겠습니다

<img width="467" alt="스크린샷 2022-04-01 오전 8 04 47" src="https://user-images.githubusercontent.com/81547954/161163677-94eab28b-c45a-4d5e-a431-fa999e7d9256.png">

설명 맨 위에 `Equatable` 는 **프로토콜**이라고 쓰여있습니다
<br><br>
#### Equatable의 정의도 살펴보면

`Equatable` 는 **값이 같은지 어떤지를 비교**할 수 있는 타입이라고 쓰여있습니다

<br>
어떤의미인지 자세히 설명드리겠습니다

```
Equatable 프로토콜을 준수하는 타입은 등호 연산자 (==) 또는 같지 않음 연산자 (!=)를 사용하여 동등성을 비교할 수 있습니다
```

Swift 표준 라이브러리 대부분 **기본 데이터타입은 Equatable를 따릅니다**

그 말은 **Equatable 프로토콜은 어떤 "타입"이 채택할 수 있다는 것**을 알 수 있습니다 타입에는 클래스, 구조체, enum 등이 있습니다

**Int와 String, Double, Bool, Float타입 모두 Equatable 프로토콜을 따르고 있습니다**

<hr>

**만약 클래스나 구조체의 인스턴스끼리 비교를 하고싶으면**

```swift
class A : Equatable {
    var Num : Int
    
    init(_ Num :Int) {
        self.Num = Num
    }
    
    public static func ==(lhs: A, rhs: A) -> Bool {
        return lhs.Num == rhs.Num
    }
}
```

이런식으로 클래스에 `Equatable` 프로토콜을 채택하여 **클래스나 구조체에 인스턴스를 비교**할 수 있습니다

### 참고 : https://zeddios.tistory.com/227, https://developer.apple.com/documentation/swift/equatable
