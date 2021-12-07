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
## Observable 변환 연산자
### Observable이 배출한 항목들을 변환하는 연산자들입니다.
* ``Buffer`` : Observable로부터 정기적으로 항목들을 수집하고 묶음으로 만든 후에 묶음 안에 있는 항목들을 한번에 하나씩 배출하지 않고 수집된 묶음 단위로 배출한다.
* ``FlatMap`` : 하나의 Observable이 발행하는 항목들을 여러개의 Observable로 변환하고, 항목들의 배출을 차례차례 줄 세워 하나의 Observable로 전달한다.
* ``GroupBy`` : 원본 Observable이 배출하는 항목들을 키(Key) 별로 묶은 후 Observable에 담는다. 이렇게 키 별로 만들어진 Observable들은 자기가 담고 있는 묶음의 항목들을 배출한다.
* ``Map`` : Observable이 배출한 항목에 함수를 적용한다.
* ``Scan`` : Observable이 배출한 항목에 연속적으로 함수를 적용하고 실행한 후 성공적으로 실행된 함수의 리턴 값을 발행한다.
* ``Window``: 정기적으로 Observable의 항목들을 더 작은 단위의 Observable 윈도우로 나눈 후에, 한번에 하나씩 항목들을 발행하는 대신 작게 나눠진 윈도우 단위로 항목들을 배출한다.
