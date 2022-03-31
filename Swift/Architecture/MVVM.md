# MVVM(Model  - View - ViewModel)

### MVVM

* MVVM은 마틴 파울러의 Presentation 모델 패턴에서 파생된 디자인 패턴입니다
* MVVM 패턴의 목표는 비즈니스 로직과 프레젠테이션 로직을 UI로부터 분리하는 것
* 비즈니스 로직과 프레젠테이션 로직을 UI로부터 분리하게 되면, 테스트, 유지 보수, 재사용이 쉬워집니다

## 'M'VVM의 Model

* MVVM아키텍쳐에서 Model은 데이터 구조를 정의하고 ViewModel에게 결과를 알려줍니다.

## M'V'VM의 View(ViewController)

* 흔히 사용하는 ViewController에 코드를 작성합니다.
* View는 사용자의 사용작용을 통해 이벤트가 일어나면 ViewModel에게 알려주며
*  ViewModel이 업데이트 요청한 데이터를 보여줍니다

## MV'VM'의 ViewModel

* 사용자의 상호작용을 view가 보내주면 그에 맞은 이벤트를 처리하고
*  Model의 Read Update Delete를 담당합니다.

### MVVM을 잘 나타내는 이미지

<img width="558" alt="MVVM" src="https://user-images.githubusercontent.com/81547954/140432641-7eea15ca-0727-43cb-afe5-5f158ee8931c.png">

### 기존의 View는 단순히 유저 인터페이스를 표시하기 위한 로직만을 담당하고, 그외에는 매소드 호출 정도만 있는게 이상적이다.
### ViewModel은 기존의 UIKit을 import 할 필요도 없이 데이터 update 및 뷰 요소를 업데이트 한다.
### Model은 데이터 구조를 갖고 있다.

### 이러한 MVVM 패턴의 장점은 View-Model-ViewController 모두 독립적으로 테스트가 가능하게 되는 것 입니다.


### 출처: https://42kchoi.tistory.com/292, https://velog.io/@k7120792/Model-View-ViewModel-Pattern
