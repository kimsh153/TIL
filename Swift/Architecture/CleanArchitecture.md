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

![image](https://user-images.githubusercontent.com/81547954/163290926-6bf2cfac-92ec-4011-9654-835d4f15120a.png)

클린 아키텍쳐의 다이어그램입니다

<br>

### The Dependency Rule

<hr>

저 원은 소프트웨어의 각각의 다른 영역들을 나타내는겁니다

<br>

outer circles - **mechanisms**

inner circles - **정책**

이 아키텍쳐를 작동시키는 가장 우선적인 규칙은 Dependency Rule 입니다

<br>

### Dependency Rule

* 소스코드 중속성은 안쪽으로만 향할 수 있음
* inner circles 안에 있는 것들은 outer circles에 대해 아무것도 알 수 없음
* 특히, outer circles에 선언된 이름은 inner circles에서 언급해서는 안됩니다 (함수, 클래스 등등)

```
한마디로 요약하자면!! "outer circles이 inner circles에 영향 안미쳤으면 좋겠음!" 입니다
```
![image](https://user-images.githubusercontent.com/81547954/163291004-1ea6c200-c72a-4511-bc27-69aee3003cf2.png)


이제부터 Clean Architecture를 어떻게 쓰는지 설명하겠습니다

### Entities

![image](https://user-images.githubusercontent.com/81547954/163291057-c6142c89-dc5b-444f-8351-d65c02aa91a0.png)

엔티티는 "Enterprise wide business rules"을 캡슐화하는것 입니다

외부 변화가 있을 때 변경될 가능성이 가장 적습니다 

**일반적으로 가장 높은 수준의 규칙**을 캡슐화 합니다

엔티티는 `데이터 구조 및 함수 집합`이라고 생각하시면 됩니다

### Use Cases

![image](https://user-images.githubusercontent.com/81547954/163291071-c58fe74f-cdf2-4e4a-98d2-bd3802e0885f.png)

유스케이스는 "**시스템의 동작을 사용자의 입장에서 표현한 시나리오**"에요

또한 

유스케이스는 시스템의 유즈케이스를 캡슐화하고 구현합니다 그리고 도메인 계층의 분리로 소스코드 변경 안정성(stability)이 높아집니다

```
Use cases는 엔티티와의 데이터 흐름을 조정하고,

해당 엔티티가 Use cases의 목표를 달성하도록 "지시"하는 역할을 합니다
```

<hr>

**엔티티는 Use cases에 대해 전혀 알지 못합니다**

하지만

**Use cases는 엔티티를 알고있습니다**

또한

`Use cases`가 `DB,UI 같은 외부 환경`의 **변경으로 인해 영향을 받지 않아야** 합니다

왜냐하면

`Use cases`는 뜻 대로 `Use cases`이기 때문에 **데이터가 어디에 저장**되어있든 **외부 프레임워크가 바뀌든** 상관없는겁니다

하지만

앱 전체의 작동 방식 변경은 `Use cases`에 영향을 미칠 수 있습니다

사용자의 시나리오가 바뀐다는 뜻이기 때문입니다

<hr>

### Interface Adapters

![image](https://user-images.githubusercontent.com/81547954/163291151-9ee861c4-e736-4d68-ac48-811d9e9e0f63.png)

다음은 초록 원입니다

초록색 원 안에는 `Controllers`, `Gateways`, `Presenters`라고 쓰여있습니다

이들을 `Interface Adapters`또는 `Presentation Layer`라고 합니다

이 계층은 `Entities`, `Use cases`에 가장 편리한 format에서 DB등과 같은 외부 프레임워크에 가장 편리한 format으로 변환되는 곳입니다

즉 DB는 이 초록색 원까지만 알아야합니다 Use cases, Entities에 있는 코드들은 DB에 대해 아는것이 1도 없어야 합니다

<hr>

Frameworks and Drivers

자 이제 가장 바깥쪽의 원을 공부해봅시다

![image](https://user-images.githubusercontent.com/81547954/163296434-902daa9b-05f8-4a92-b4e3-0769b744961c.png)

이 계층에는 일반적으로 DB, 프레임워크 같은 것들로 구성이 됩니다

### 참고 : https://zeddios.tistory.com/1065, <br> https://medium.com/@justfaceit/clean-architecture%EB%8A%94-%EB%AA%A8%EB%B0%94%EC%9D%BC-%EA%B0%9C%EB%B0%9C%EC%9D%84-%EC%96%B4%EB%96%BB%EA%B2%8C-%EB%8F%84%EC%99%80%EC%A3%BC%EB%8A%94%EA%B0%80-1-%EA%B2%BD%EA%B3%84%EC%84%A0-%EA%B3%84%EC%B8%B5%EC%9D%84-%EC%A0%95%EC%9D%98%ED%95%B4%EC%A4%80%EB%8B%A4-b77496744616
