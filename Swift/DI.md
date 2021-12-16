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

#### 참고 : https://medium.com/@jang.wangsu/di-dependency-injection-%EC%9D%B4%EB%9E%80-1b12fdefec4f
