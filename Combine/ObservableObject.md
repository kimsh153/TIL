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

> https://nsios.tistory.com/120 <- 여기에서 나온 예시를 기준으로 설명하겠습니다

예를 들어

ForEach를 이용해서 뷰를 10개를 그린뒤 한개의 뷰만 변경해서

새로 그릴때 참조를 할 수 없기때문에 10개를 또 새로그리면? 너무 낭비겠죠

그래서 필요한 것만 새로 그려주는 방식이 ObservableObject입니다

<br>

이를 테스트한 예시를 한번 보겠습니다

init에 print를 찍으면 모든 뷰 10개의 출력을 볼수 있고

뷰가 그려질때 랜덤색을 주기로 했는데

하나의 뷰만 변경할때 하나의 뷰만 변하는 걸 볼수있어요

감시대상 클래스 변수에는 @ObservedObject를 선언하고 그 변수의 class에 ObservableObject를 준수해주고

변경됨을 알릴 변수에는 @Publisher을 선언한는 방식으로 사용해요

```swift
struct TestView: View {
	// 감시대상 클래스
    @ObservedObject var viewModel: ViewModel = ViewModel(count: 10)
    
    var body: some View {
        ForEach(0..<viewModel.models.count) { index in
            RandomView(id: index, model: viewModel.models[index]).onTapGesture {
                let changeNum = Int.random(in: 0...100)
                viewModel.models[index].id = changeNum
                print("tap change: \(changeNum)")
            }
        }
    }
}

struct RandomView: View {
    let color: [Color] = [.red, .black, .blue, .gray, .green]
    var id: Int // Identifiable test
    var model: Model
    var body: some View {
        Text("\(model.id)")
            .foregroundColor(color.randomElement()!)
    }
    
    init(id: Int, model: Model) {
        self.id = id
        self.model = model
        print("init")
    }
}

class ViewModel: ObservableObject {
	// 변경을 감지할 변수
    @Published var models: [Model] = []
    
    init(count: Int) {
        for _ in 0..<count {
            models.append(Model(id: Int.random(in: 0...100)))
        }
    }
}

struct Model {
	// Identifiable test
    var id: Int
}
```
#### 출처: https://nsios.tistory.com/120

<img src="https://user-images.githubusercontent.com/81547954/201528429-1b7c33a3-5d98-41f8-a5ca-a4f5df2642eb.png" width=300>

하나의 텍스트를 클릭하면 하나의 텍스트의 색만 변하는걸 볼 수 있어요

모든 뷰가 다시그려진다면 모든 텍스트의 색이 랜덤으로 변해야 하지만 그렇지않을걸 알 수 있죠

### 참조: https://nsios.tistory.com/120
