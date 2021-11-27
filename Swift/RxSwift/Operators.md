# Operators

### Operators(연산자) RxSwift에서 지원하는 연산자는 기본 Swift에 기본 연산자와 다른 연산자입니다.

## Observable 생성 연산자
### 새로운 Observable을 만드는 연사자들입니다
* ``Create`` : 직접적인 코드 구현을 통해 옵저버 메서드를 호출하여 Observable을 생성한다.
* ``Defer`` : 옵저버가 구독하기 전까지는 Observable 생성을 지연하고 구독이 시작되면 옵저버 별로 새로운 Observable을 생성한다
* ``Empty``/``Never``/``Throw`` : 아주 정확하고 제한된 행동을 하는 Observable을 생성한다
