# Swinject

### Swinject란

* Swinject는 Swift의 의존성 주입(DI) Framework중 하나입니다

> Swinject는 Swift용 경량 종속성 주입 프레임워크입니다
>
> DI(Dependency Injection)는 종속성을 해결하기 위해 IoC(Inversion of Control)를 구현하는 소프트웨어 디자인 패턴입니다
>
> 패턴에서 Swinject는 앱을 느슨하게 결합된 구성 요소로 분할하여 더 쉽게 개발, 테스트 및 유지 관리할 수 있도록 도와줍니다
>
> Swinject는 Swift 일반 유형 시스템과 앱의 종속성을 간단하고 유창하게 정의하는 일급 함수로 구동됩니다

라고 `Swinject` 리드미에 쓰여있습니다

### DI

Dependency Injection(의존성 주입)은 코드 자체의 중속성이 아닌, 다른 객체에 의해 제공되도록 코드를 구성하는 접근법입니다

이 방식으로 코드를 정렬하면 Test 및 Refactoring이 가능한 약하게 결합된 구성 요소(Components)의 코드베이스가 생성됩니다

3rd Party Library없이 DI를 구현할 수 있지만, Swinject는 DI 프레임워크에서 널리 사용되는 패턴인 DI Container를 사용합니다. 이 패턴유형은 코드의 복잡성이 증가하더라도 중속성의 dependecies를 단순하게 유지합니다.

> 3rd Party Library : 프로그래밍을 도와주는 plug_in 이나 library 등을 만드는 회사, 제 3자로써 중간다리 역할을 하는 것

<a href="https://github.com/kimsh153/TIL/blob/master/Swift/DI.md" target="_blank">DI 정리</a>

### Swinject 사용법

**pod 파일 추가**
```swift
pod 'Swinject'
```

제일먼저 의존성 주입은 Class 외부에서 해야합니다

바로 앱의 설정을 관리해주는 **AppDelegate 파일에서 의존성 주입을 시켜주면 됩니다**

```swift
import Swinject
```

그 다음 **의존성을 위한 서비스를 등록하고 가져와서 사용한다!**

이 개념의 원칙을 잘 기억해보겠습니다

```swift
let container = Container()
container.register(Animal.self) { _ in Dog(name: "MOMO") }
container.register(Person.self) { r in
    PetOwner(pet: r.resolve(Animal.self)!)
}
```

* 의존성을 주입해주는 큰 틀인 컨테이너를 생성합니다
* 해당 컨테이너에 주입시켜줄 의존성의 서비스를 등록합니다

```swift
let person = container.resolve(Person.self)!
person.play() // prints "I'm playing with MOMO."
```
* resolve를 이용해 사용할 서비스 인스턴스를 가져옵니다

아직은 이해하기 쉽지 않지만 한가지는 알 수 있습니다

#### `register로 등록을 하고 resolve로 사용한다`

실제로 AppDelegate에서 등록하고 사용한다면 이렇게 해볼 수 있을것입니다
```swift
let container = Container()
container.register(FirstViewModel.self) { r in FirstViewModel() }
container.register(SecondViewModel.self) { r in SecondViewModel() }

container.register(FirstViewController.self) { r in
    let controller = FirstViewController()
    controller.viewModel = r.resolve(FirstViewModel.self)
    
    return controller
}
container.register(SecondViewController.self) { r in
    let controller = SecondViewController()
    controller.viewModel = r.resolve(SecondViewModel.self)
    
    return controller
}

self.window?.rootViewController = container.resolve(FirstViewController.self)
```
AppDelegate에서 하나의 컨테이너를 만들고 여러 의존성을 주입시키고 사용함으로 **앱 전체의 의존성을 편리하게 관리할 수 있습니다**

### 참고 : https://velog.io/@velmash/Swinject, https://green1229.tistory.com/163
### 3rd Party Library참고 : https://vivabin.tistory.com/2
