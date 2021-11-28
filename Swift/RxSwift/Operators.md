# Operators

### Operators(연산자) RxSwift에서 지원하는 연산자는 기본 Swift에 기본 연산자와 다른 연산자입니다.

## Observable 생성 연산자
### 새로운 Observable을 만드는 연사자들입니다
* ``Create`` : 직접적인 코드 구현을 통해 옵저버 메서드를 호출하여 Observable을 생성한다.
* ``Defer`` : 옵저버가 구독하기 전까지는 Observable 생성을 지연하고 구독이 시작되면 옵저버 별로 새로운 Observable을 생성한다.
* ``Empty``/``Never``/``Throw`` : 아주 정확하고 제한된 행동을 하는 Observable을 생성한다.
* ``From``/ : 다른 객체나 자료 구조를 Observable로 변환한다.
* ``Interval`` : 특정 시간별로 연속된 정수형을 배출하는 Observable을 생성한다.
* ``Just`` : 객체 하나 또는 객채집합을 Observable로 변환한다. 변환된 Observable은 원본 객체들을 발행한다.
* ``Range`` : 연속된 범위(Range)의 정수를 발행하는 Observable을 생성한다.
* ``Repeat`` : 특정 항목이나 연속된 항목들을 반복적으로 배출하는 Observable을 생성한다.
* ``Start`` : 함수의 실행 결과를 배출하는 Observable을 생성한다.
* ``Timer`` : 지정된 시간이 지나고 난 후 항목을 하나 배출하는 Observable을 생성한다.
