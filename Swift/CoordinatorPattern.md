# CoordinatorPattern

### Coordinator?

Coordinator는 움직임을 조정하는 사람 - Zedd 이라고 말하고 있습니다.

## CoordinatorPattern?

`CoordinatorPattern`은 화면들(ViewControllers)의 계층을 관리하는 것, 화면간의 연결을 해결하는 중요한 개념이므로 ios에서 매우 유용한 패턴

일단 Coordinator의 시작부터 알고 가곗습니다.

CoordinatorPattern은 2015년, Soroush Khanlou가 The Coordinator라는 글을 쓰면서 소개됩니다.'

이때 Khanlou는

> Khanlou: Massive View Controller의 가장 큰 문제 중 하나는 
> **flow logic(흐름 로직) 및 business logic이 얽혀있다는 것이다!**

라고 생각합니다.

다음은 Khanlou가 예로 든 코드를 Zedd분꼐서 Swift로 컨버팅해주셧습니다.
```swift
func tableView(_ tableView: UITableView, didSelectRowAt indexPath: IndexPath) {
    let object = self.dataSource[indexPath]
    let detailViewController = SKDetailViewController(with: object)
    self.navigationController?.present(detailViewController, animated: true, completion: nil)
}
```

TableViewCell을 클릭하면 호출되는 **didSelectRowAt**메소드입니다.

단 3줄입니다.

**1.객체를 가져옵니다.**
<br>
**2.ViewController를 만듭니다.**
<br>
**3.ViewController를 보여줍니다.**

간단한 앱에서는 아무 문제없이 완벽하게 동작합니다.

하지만 앱이 복잡해짐에 따라, ViewController가 새로운 방식 또는 새로운 위치에서 사용될 수 있습니다.

위에서 만든 DetailViewController가 저렇게 한번만 쓰이는게 아니라 다른 곳에서도 만들어지고 다시 보여질 수 도 있는 경우도 있기 때문입니다.

복잡한 앱에서 위 코드를 다시 살펴보기로 하겠습니다

```swift
func tableView(_ tableView: UITableView, didSelectRowAt indexPath: IndexPath) {
    let object = self.dataSource[indexPath]
    let detailViewController = SKDetailViewController(with: object)
    self.navigationController?.present(detailViewController, animated: true, completion: nil)
}
```

**1.객체를 가져옵니다.**
-> 첫번째 줄은 괜찮습니다. datasource는 viewController의 논리적인 자식이며, 참조해야하는 객체를 요청하고 있습니다.

**2.ViewController를 만듭니다.**
-> 여기서부터 문제가 생기기 시작합니다. ViewController는 flow의 다음 단계를 "**인식**"하게 됩니다.

**3.ViewController를 보여줍니다.**
-> 여기서부터는 완전히 벗어나는 곳입니다. ViewController는 이제 부모까지 잡습니다.
**부모 ViewController에게 해야할 일에 대한 정확한 메세지를 보내고 있습니다.**
**(한마디로 부모에게 이래라 저래라 하고 있다는 겁니다.)**

더 큰 문제는 이러한 flow logic이 여러 **ViewController에 분산**되어 있을 수 있다는 겁니다.

Khanlou는 이렇게 생각했습니다.

> Khanlou : ViewController 기본 클래스는 UI로 시작되며
> (UIViewController), View객체이고, 사용자 흐름을 처리하는것은 범위(scope)를 벗어난다!

Khanlou는 ViewController를 높은 수준의 객체로 관리하게 되면 많은 이점을 얻는다는 것을 알게 됩니다.

이 높은 수준의 객체의 역할은 모든 ViewController를 모으고(marshal)관리하는 것입니다.

Khanlou는 이 높은 수준의 객체를 **Coordinators 또는 Directors**라고 부르기로 합니다.

그리고 이 패턴을 제대로 실행하려면 전체 앱을 direct하는 high-level coordinator가 필요하다고 합니다.

**AppDelegate(SceneDelegate)는 AppCoordinator를 유지하며, 모든 Coordinator에는 일련의 하위 Coordinator가 있습니다.**

더 자세한 내용은

<a href="https://khanlou.com/2015/01/the-coordinator/">The Coordinator</a>

<a href="https://khanlou.com/2015/10/coordinators-redux/">Coordinators Redux</a>

를 참고하세요

### Coordinator가 훌륭한 이유
**1.각 ViewController의 고립.**

ViewController의 데이터를 표시하는 방법 이외에는 아무것도 모르며, 어떤일이 발생할 때마다 대리자(Delegate)에게 알리지만 Delegate가 누군지는 알 수 없습니다.

예전같았으면 ViewController에서 분기문을 통해 분기했어야 한다면 이제는 ViewController가 조건을 검사할 필요가 없어졌습니다.

**2.ViewController의 재사용**

ViewController는 어떤 context로 표시될지 버튼이 어떤 용도로 사용될지에 대해 아무것도 가정하지 않고 있습니다.

앱의 iPad 버전을 작성하는 경우 Coordinator만 교체해야하며 모든 ViewController를 재사용 할 수 있습니다.

**3.앱의 모든 작업과 하위 작업은 전용 캡슐화 방법을 제공.**

**4.Coordinator는 display-binding을 side effects와 분리.**

ViewController를 표시할 때 ViewController가 데이터를 엉망으로 만들지 여부에 대해 걱정할 필요가 없어집니다.

읽기 및 디스플레이어만 할 수 있으며 데이터를 쓰거나 손상시키지 않습니다.

* side effects : 어떤 함수를 호출했을 때, 그 함수의 반환값 이외에 호출된 함수 밖에서 프로그램의 상태변화가 발생하면 이를 Side Effect라합니다. 

**5.Coordinator는 완전히 제어할 수 있는 객체.**

viewDidLoad가 호출 될 때 까지 기다리지 않고 전적으로 show를 제어할 수 있습니다.

호출을 받는 대신 호출을 시작합니다.

참고 : https://zeddios.medium.com/coordinator-pattern-bf4a1bc46930, <br> https://mike123789-dev.tistory.com/entry/%ED%95%A8%EC%88%98%ED%98%95-%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D%EC%97%90-%EB%8C%80%ED%95%98%EC%97%ACfeat-Swift
