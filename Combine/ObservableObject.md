# ObservableObject

### ObservableObject?

SwiftUI를 공부하시다 보면 한번쯤 보신적이 있으실거에요

ObservableObject는 **필수구현을 하지않는 프로토콜이고 Combine에 속해있고 클래스에서만 사용가능**해요

ObservableObject를 준수한 클래스는 `objectWillChange`라는 프로퍼티를 사용핤 수 있어요(ObservableObjectPublisher 타입)
objectWillChange.send()를 사용하기 위함이에요

이 `send()`함수는 **변경된 사항이 있다고 알려주는 거**에요

<br>

가지고있는 변수가 적으면 send()함수를 몇번 해줘서 간단하게할 수 있겠지만

변수도 많고 수정 되는부븐이 많고 복잡하다면 하나하나 신경쓰기 힘들어지겠죠

그럴때 `@Published` 속성래퍼를 이용하면 됩니다

해당 변수가 변경되면 자동으로 objectWillChange.send()를 호출해줘요

<br>

여러분도 아시다시피 SwiftUI의 View는 class가 아니라 struct지요

다시말하자면 해당 뷰에대한 참조를 가지고 있을 수 가없어요

<br>

**어? 그러면 리스트가 일부만 변경되었을때 항상 그 뷰들을 새로 그리나요??**

**SwiftUI는 매번 그리는것을 피하기위해서 최선을 다한다**고해요

뷰를 랜더, 즉 그리는 단계에 있어서는 성능 최적화하는 동작이있고 **필요할 때만 그린다**고해요

### 참조: https://nsios.tistory.com/120
