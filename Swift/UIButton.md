# UIButton
### UIButton은 버튼을 만드는 클래스입니다.

> 코드 구현
```swift
let/var 변수명 = UIButton()
```
> 버튼 보이게만 하기
```swift
import UIKit
class ViewController : UIViewController {


    lazy var button : UIButton = {
        let button = UIButton()
        button.frame = CGRect(x: 100, y: 100, width: 200, height: 200)
        button.backgroundColor = .black
        button.setTitle("Button", for: .normal)
        return button
    }()

   override func viewDidLoad() {
        super.viewDidLoad()
        view.addSubView(button)
   }
   
}
```
