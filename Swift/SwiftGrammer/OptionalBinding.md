# OptionalBinding

### OptionalBinding?
옵셔널 바인딩은 옵셔널을 안전하게 처리하는 방법입니다

옵셔널 값은 랩에 쌓여 있어서, 사용하기 위해서는 unwrapping하는 과정이 필요합니다

<br>

!키워드를 사용하여 forced unwrapping을 할 수 있습니다

하지만 이 경우에는 crash가 발생할 위험이 있으므로 (옵셔널이 nil값을 가질 때)

사용에 주의해야 합니다

<hr>

if문, while문, guard문에서 사용합니다

기본 syntax입니다

> syntax: 구문

```swift
//if 문
if let name: Type = OptionalExpression {
    Statements
}

//while문
while let name: Type = OptionalExpression {
    Statements
}

//guard문
guard let name: Type = OptionalExpression else {
    Statements
    //바인딩에 실패할 경우 else블록이 실행된다
}
```

Binding은 옵셔널 표현식을 평가하여, 값을 리턴할 수 있으면 (즉, 값이 저장되어 있으면) unwrapping되어서 상수에 저장됩니다

값을 리턴하는 경우에만 (값을 저장하는 경우에만) unwrapping하기 때문에 crash의 위험이 없습니다

### 참고: https://swycha.tistory.com/6
