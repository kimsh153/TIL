# Closure

### Clousre란?
* 클로저는 사용자의 코드 안에서 전달되어 사용할 수 있는 로직을 가진 중괄호"{}"로 구분된 코드의 블럭이며, 일급 객체의 역할을 할 수 있습니다
* 일급 객체는 전달 인자를 보낼 수 있고 변수/상수 등으로 저장하거나 전달할 수 있으며, 함수의 반환 값이 될 수도 있습니다
* 다른 언어의 람다(lambdas)와 비슷합니다

### 전역 함수(global functions)와 중첩 함수(nested function)은 실제 클로저의 특별한 경우입니다

### 클로저는 다음 세가지 형태 중 하나를 갖습니다
* 전역 함수 : 이름이 있고 어떤 값도 캡쳐하지 않는 클로저
* 중첩 함수 : 이름이 있고 관련한 함수로 부터 값을 캡쳐 할 수 있는 클로저
* 클로저 표현 : 경량화 된 문법으로 쓰여지고 관련된 문맥(context)으로터 값을 캡쳐할 수 있는 이름이 없는 클로저

### Swift에서 클로저 표현은 최적화 되어서 간결하고 명확합니다. 이 최적화에는 다음과 같은 내용을 포함합니다.
* 문맥(context)에서 인자 타입(parameter type)과 반환 타입(return type)의 추론
* 단일 표현 크르로저에서의 암시적 변환
* 축약된 인자 이름
* 후위 클로저 문법

### 아직 뭔소리인지 이해가 잘 되지 않지만 차근차근 이해해 보겠습니다.

## 클로저 표현

클로저 표현은 코드의 명확성과 의도를 잃지 않지만 문법을 축약해 사용할 수있는 다양한 문법의 최적화 방법을 제공합니다

클로저에 대해 설명하기위해 배열값을 정렬하는 메소드(sorted(by:))와 클로저를 이용하여 정렬을 해보겠습니다
```swift
let names = ["Chris", "Alex", "Ewa", "Barry", "Daniella"]
```
`sorted(by:) 메소드`는 배열의 콘텐츠와 같은 타입을 갖고 두개의 인자를 갖는 클로저를 인자로 사용합니다 

name의 콘텐츠는 String 타입이므로 (String, String) -> Bool 의 타입의 클로저를 사용해야 합니다 

클로저를 제공하는 일반적인 방법은 함수를 하나 만드는 것 입니다 

위 타입((String, String) -> Bool)을 만족 시키는 함수를 하나 만들면 정렬에 인자로 넣을 수 있는 클로저를 만들 수 있습니다

```swift
func backward(_ s1: String, _ s2: String) -> Bool {
  return s1 > s2
}
var reversedNames = names.sorted(by: backward)
// reversedNames를 출력할 시 옆과 같이 뜹니다 ["Ewa", "Daniella", "Chris", "Barry", "Alex"]
```
backword 클로저를 만들고 그것을 names.sorted(by:backward)에 넣으면 원본 배열의 순서가 바뀐 배열을 정렬 결과로 얻을 수 있습니다

방금 쓴 코드들을 앞으로 클로저의 다양한 문법 및 상요에 대해 알면서 더 짧게 쓸 수 있습니다

### 클로저 표현 문법 (Closure Expression Syntax)

클로저 표현 문법은 일반적으로 아래의 형태를 띱니다

```swift
{ (parameters) -> return type in 
    statements
}
```
인자로 넣을 `parameters`, 인자 값으로 처리할 내용을 기술하는 `statements` 그리고 `return type`입니다 

앞의 `backward`클로저를 이용해 배열을 정렬하는 코드는 클로저 표현을 이용해 다음과 같이 바꿀 수 있습니다

```swift
reversedNames = names.sorted(by: { (s1: String, s2: String) -> Bool in
    return s1 > s2
})
```

### 후위 클로저(Trailing Closures)

만약 함수의 마지막 인자로 클로저를 넣고 그 클로저가 길다면 후위 클로저를 사용할 수 있습니다

```swift
func exampleClosure(closure: () -> Void) {
  // function body
}
```

위 클로저의 인자 값 입력 부분과 반화 형 부분을 생략해 다음과 같이 표현할 수 있고

```swift
func exampleClosure(closure: {
  // closure's body
}
```

이것을 후위 클로저로 표현하면 아래와 같이 표현할 수 있습니다

함수를 대괄호 ({,} ) 로 묶어 그 안에 처리할 내용을 적으면 됩니다

모르고 사용하셨다면 이런 일반적인 전역함수 형태가 사실 클로저를 사용하고 있던 것이었습니다

```swift
func exampleClosure() {
  // trailing closure's body
}
```

### 출처 : https://jusung.gitbook.io/the-swift-language-guide/language-guide/07-closures
