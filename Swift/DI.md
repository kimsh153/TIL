# DI 

### DI(Dependency Injection) 의존성 주입
DI는 표준을 정의 할 수 있고, 정의된 표준을 바탕으로 같은 설계를 하게 해줍니다.

DI를 알기위해 의존성 주입이라는 용어부터 알아보도록 합시다.

### 의존?
의지하여 생활하거나 존재하는 일.(출처 : 구글 사전)

### 의존성?
의존 관계를 가지는 일을 말합니다.
```swift
import UIKit

class AClass {
    var number : Int = 1
}

/// AClass와 의존관계가 있는 클래스
class BClass {
    /// 내부에 변수로 AClass를 사용함
    var internalVariable = AClass()
}

let b = BClass()
print(b.internalVariable.number)
```
위에 그림 처럼 B클래스에서

A 클래스를 내붕에 변수로 사용하게 됨으로써

**B 클래스는 A 클래스에 의존관계가 생기게 됩니다.**

### 주입?
내부가 아니라 **외부에서 객체를 생성해서 넣어주는 것**을 주입한다고 합니다.

```swift
import UIKit

class BClass {
    var number: Int
    
    init(WithNumber number: Int) {
        self.number = number
    }
    
    func setNumber(number: Int) {
        self.number = number
    }
}

/// 외부에서 객체를 생성해서 넣습니다.
let b = BClass(WithNumber: Int(3))
print(b.number)

/// 외부에서 객체를 생성해서 넣습니다.
b.setNumber(number : Int(5))
print(b.number)
```

Int(3),Int(5)를 외부에서 생성해서 함수를 통해 넣어주고 있는것을 볼 수 있습니다.

이렇게 객체를 외부에서 넣어주는 것을 주입한다고 합니다.

그럼 

### 의존성 + 주입?
내부에서 만든 변수를 외부에서 넣어주게 하면 됩니다.
```swift
import UIKit

class AClass {
    var number: Int = 1
}

class BClass {
    /// 내부에 변수로 AClass를 사용할 것임
    var internalVariable: AClass
    
    init(WithExternalVariable variable : AClass) {
        // 외부에서 AClass 객체를 받습니다.
        self.internalVariable = variable
    }
}

/// 외부에서 AClass 를 BClass에 주입합니다.
/// 제어의 주체가 외부에 있습니다.
let b = BClass(WithExternalVariable: AClass())
print(b.internalVariable.number)
```
이렇게 의존성주입을 해줍니다.
**그런데 DI는 의존성주입만을 말하는게 아닙니다.**

### 의존성 분리
위에서는 단순하게 의존성 주입의 용어만 이해해보려고 확인하였던 것입니다.

DI는 의존성을 분리시켜 사용합니다.

의존성 주입(DI)은 알겠는데 의존성 분리는 어떻게 할까요?

의존성 분리를 의존관계 역전의 원칙?으로 의존관계를 분리시킵니다.

> 좀 더 자세히
```
객체 지향 프로그래밍에서 의존관계 역전 원칙은 소프트웨어 모듈들을 분리하는 특정 형식을 지칭한다.
이 원칙을 따르면, 상위 계층(정책 결정)이 하위 계층(세부 사항)에 의존하는 전통적인 의존관계를
반전(역전)시킴으로써 상위 계층이 하위 계층의 구현으로부터 독립되게 할 수 있다. 
이 원칙은 다음과 같은 내용을 담고 있다.
```
(출처 : 위키백과) https://ko.wikipedia.org/wiki/%EC%9D%98%EC%A1%B4%EA%B4%80%EA%B3%84_%EC%97%AD%EC%A0%84_%EC%9B%90%EC%B9%99

상위계층이 하위계층에 의존하게 되는 상황에서 protocol을 이용하여 의존성을 낮출 수 있습니다.

```swift
import UIKit

/// 의존 관계를 독립시킬 인터페이스
protocol DependencyIndependentInterface : AnyObject {
    var number : Int { get set }
}

/// 그냥 평범하지만 위의 인터페이스에 의존관계가 있는 클래스
class AClass : DependencyIndependentInterface {
    var number = 1
}

/// AClass와 의존관계가 있는 클래스
class BClass {
    /// 내부에 변수로 AClass를 사용할 것임
    var internalVariable : DependencyIndependentInterface
    
    init(WithExternalVariable variable : DependencyIndependentInterface) {
        // 외부에서 AClass 객체를 받습니다.
        self.iternalVariable = variable
    }
}

/// 외부에서 AClass 를 BClass에 주입합니다.
/// 제어의 주체가 외부에 있습니다.
let b = BClass(WithExternalVariable : AClass())
print(b.internalVariable.number)

```

이렇게 하면 제어의 주체가 Protocol(Interface)에게 있습니다.

### IOC
`IOC`는 `Inversion Of Control`의 약어이며, 제어의 주제가 역적되는 패턴입니다.

#### 참고 : https://medium.com/@jang.wangsu/di-dependency-injection-%EC%9D%B4%EB%9E%80-1b12fdefec4f
