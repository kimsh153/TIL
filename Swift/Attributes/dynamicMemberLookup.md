# dynamicMemberLookup

### dynamicMemberLookup?

이 속성을 클래스, 구조, 열거형 또는 프로토콜에 적용하여 유형의 인스턴스를 호출 가능한 함수로 처리합니다

이 말은 밑에서 자세히 설명하겠습니다

그 전에

### dynamicMemberLookup 특징

<a href="https://github.com/apple/swift-evolution/blob/master/proposals/0195-dynamic-member-lookup.md">SE-0195</a>에서 처음 소개 되었습니다 Swift 4.2에서 구현되었습니다

class, struct, enum, protocol에 사용 가능합니다

subscript (dynamicMemberLookUp :) 메소드를 구현해야합니다

dynamicMemberLookUp을 해석 해보면 

동적 멤버 조회인데 

동적으로 멤버를 조회한다 라는 의미를 가진 것 같습니다

1. 만약 dynamicMemberLookup을 "사용"하는 타입이 있다면,
 
2. 이 타입은 런타임시 확인되는 임의의 "name"에 대해 

3. "dot" syntax를 사용할 수 있도록 제공해준다.

### 참고: https://zeddios.tistory.com/1224
