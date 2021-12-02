# Extension

`Extension`은 **확장**이라는 뜻을 가지고 있다. 그래서 Extension이 하는 일은 **기존 클래스, 구조체, 열거형 타입또는 프로토콜 유형**에 **새로운 기능**을 추가하는 일을 한다. &nbsp;기존 소스코드에서 접근하지 못하는 타입들을 확장할 수 있다.

Swift에서 Extension은 다음 기능을 수행할 수 있다.
* 계산 속성과 계산 정적 속성 추가
* 인스턴스 메소드와 타입 메소드 정의
* 새로운 이니셜라이저 제공
* 서브스크립트 정의
* 새로운 중첩 타입 정의와 사용
* 기존 타입에 프로토콜 적용하기
```
확장은 타입에 새로운 기능을 추가할 수 있지만 기존 기능을 오버라이드 할 수 없다.
```

## Extension Syntax(확장 문법)
```extension``` 키워드로 확장을 선언합니다.
```swift
extension SomeType {
  // new functionality to add to SomeType goes here
}
```
