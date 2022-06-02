# Optional Chaining

### Optional Chaining

옵셔널 체이닝은 옵셔널일 수 있는 인스턴스 내부의 프로퍼티, 메소드, 서브스크립트를 매번 nil 체크를 하지않고 최종적으로 원하는 값, 혹은 nil 인지 판단하는 방법입니다

여러개를 함께 연결 할수 있고, 연결된 어떤 링크라도 nil이면, nil이 됩니다

하나의 링크라도 옵셔널이면 nil 값이 나옵니다

```swift
// Family 클래스 내부에 Child 옵셔널타입 변수가 존재합니다
class Family {
  var child: Child?
}

// Child 클래스 내부에 String 옵셔널타입 변수가 존재합니다
class Child {
  var name: String?
}

// family 인스턴스의 child 프로퍼티는 옵셔널타입 이므로 child뒤에 ? 를 표시합니다
var family = Family()
fmaily.child?.name = "c"

let name = family.child?.name
print(name) // 출력: nil

/*
family.child?.name 프로퍼티가 "벨류값"로 할당 되었더라도
family의 child 프로퍼티는 옵셔널 타입이기 때문에 nil이 출력됩니다
*/
```

### 만약 강제 언래핑을 한다면?

```swift
let name = family.child!.name
print(name)
/* error: Unexpectedly found nil while unwrapping an Optional value
name값이 nil 값인데 강제 언래핑을 하면 에러가 납니다 */
```

### 모든 링크에 인스턴스 참조 진행 후

```swift
// Family, Child 클래스 인스턴스 참조
var family = Family()
var child = Child()
child.name = "벨류값"


// family의 child 프로퍼티에 child 인스턴스 참조
family.child = child
let name = family.child?.name
print(name)
/* 출력: Optional("벨류값") nil 값이 아닌 옵셔널값이 출력이 되었다
   클래스 내부 프로퍼티에 인스턴스를 모두 참조 시켰지만
   Family의 child 프로퍼티는 옵셔널타입이므로 옵셔널 해제를 진행해야 한다
*/
```

### 옵셔널체이닝 진행 후

```swift
// 옵셔널 체이닝
if let name = family,child?.name {
  print(name)
} else {
  print("이름이 존재하지 않습니다")
}
/* 출력: 벨류값
   if let문을 사용해서 값이 있을 때 옵셔널 해제를 해주었습니다*/
```

중위 연산자를 사용해서 nil 값일때 들어갈 값을 지정해 준다면 옵셔널을 해제할 수 있습니다

```swift
var name = family.child?.name ?? "이름이 존재하지 않습니다"
print(name)
// 출력: 벨류값

// 중위 연산자로 nil일 경우 사용할 값을 출력하기위해 nil로 만듭니다
family.child?.name = nil
name = family.child?.name ?? "이름이 존재하지 않습니다"
print(name) // 출력: 이름이 존재하지 않습니다
```

### 참고: https://zetal.tistory.com/entry/swift-%EA%B8%B0%EC%B4%88%EB%AC%B8%EB%B2%95-4-%EC%98%B5%EC%85%94%EB%84%90
