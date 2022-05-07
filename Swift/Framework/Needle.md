# Needle

### Needle란

Needle은 Swift의 의존성 주입(DI) 시스템입니다

* Cleaning, Swinject와 같은 DI(dependency injection) 프레임워크지만! 계층적으로 DI 구조를 작성하도록 유도하고 있습니다
* 다른 DI 프레임워크와 달리 제공되는 커멘드 라인 툴을 통해서 런타임이 아닌 컴파일 타임에서 잘못된 DI 계층에 대해서 지적을 해줍니다
* 컴파일과 동시에 계층적으로 그려진 DI 코드를 자동으로 생성해줍니다

**Needle은 다른 DI framework랑은 다르게 컴파일 타임에서 잘못된 DI 계층을 지적해주는 포인트와 코드를 자동으로 생성해주는 즉**

**매번 새로운 객체를 추가할 때마다 register 해주는 코드를 작성하는 번거로움이 필요없는 점이 있습니다**

### https://github.com/uber/needle, https://medium.com/daangn/%EB%AA%A8%EB%93%88%ED%99%94%ED%95%98%EA%B3%A0-needle-%EC%A0%81%EC%9A%A9%ED%95%B4%EB%B3%B4%EA%B8%B0-bd5e9f3c450b
