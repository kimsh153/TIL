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
func tableView(_ tableiView: UITableView, didSelectRowAt indexPath: 

참고 : https://zeddios.medium.com/coordinator-pattern-bf4a1bc46930
