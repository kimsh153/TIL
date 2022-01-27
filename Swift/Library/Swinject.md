# Swinject

### Swinject란

* Swinject는 Swift의 의존성 주입(DI) Framework중 하나입니다

### DI

Dependency Injection(의존성 주입)은 코드 자체의 중속성이 아닌, 다른 객체에 의해 제공되도록 코드를 구성하는 접근법입니다. 이 방식으로 코드를 정렬하면 Test 및 Refactoring이 가능한 약하게 결합된 구성 요소(Components)의 코드베이스가 생성됩니다.

3rd Party Library없이 DI를 구현할 수 있지만, Swinject는 DI 프레임워크에서 널리 사용되는 패턴인 DI Container를 사용합니다. 이 패턴유형은 코드의 복잡성이 증가하더라도 중속성의 dependecies를 단순하게 유지합니다.

> 3rd Party Library : 프로그래밍을 도와주는 plug_in 이나 library 등을 만드는 회사, 제 3자로써 중간다리 역할을 하는 것

<a href="https://github.com/kimsh153/TIL/blob/master/Swift/DI.md" target="_blank">DI 정리</a>

### 사용법

**pod 파일 추가**
```swift
pod 'Swinject'
```


### 참고 : https://velog.io/@velmash/Swinject, https://green1229.tistory.com/163
### 3rd Party Library참고 : https://vivabin.tistory.com/2
