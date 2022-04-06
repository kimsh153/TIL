# CleanArchitecture

### CleanArchitecture?

CleanArchitecture를 설명하기 전에 CleanArchitecture이전에 나온 아키텍쳐들은 다들 유사한것이 있었습니다

<br>

다들 `같은 목표`를가지고 있고 `소프트웨어를 계층(layer)로 나눠서 관심사를 분리`합니다

<br>

#### 이렇게 만들면 소프트웨어들은

<hr>

1.**Independent of Frameworks** 아키텍쳐는 소프트웨어 라이브러리의 존재에 의존하지 않음

2.**Testable** 비즈니스 로직은 UI, DB, 웹 서버 또는 기타 외부 요소 없이 테스트 할 수 있음

3.**Independent of UI** UI는 시스템을 변경하지 않고도 쉽게 변경 가능 (ex. 비즈니스 로직을 바꾸지 않고 웹 UI를 콘솔 UI로 변경가능)

4.**Independent of Database** 비즈니스 로직이 DB에 바인딩 되지 않음

5.**Independent of any external agency** 비즈니스 로직은 외부 세계;;(outside world에 대해 전혀 알지 못함
<hr>

<br>

이렇게 됩니다

<br>

#### 이런 `아키텍쳐들을 단일 아이디어로 통합`한것이 `클린 아키텍쳐`입니다

### 참고 : https://zeddios.tistory.com/1065, <br> https://medium.com/@justfaceit/clean-architecture%EB%8A%94-%EB%AA%A8%EB%B0%94%EC%9D%BC-%EA%B0%9C%EB%B0%9C%EC%9D%84-%EC%96%B4%EB%96%BB%EA%B2%8C-%EB%8F%84%EC%99%80%EC%A3%BC%EB%8A%94%EA%B0%80-1-%EA%B2%BD%EA%B3%84%EC%84%A0-%EA%B3%84%EC%B8%B5%EC%9D%84-%EC%A0%95%EC%9D%98%ED%95%B4%EC%A4%80%EB%8B%A4-b77496744616
