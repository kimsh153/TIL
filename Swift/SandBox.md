# SandBox

### SandBox?

SandBox? SandBox는 크리에이터 소속사 아닌가? 라고 생각하신분들 반성하십시요!

이번에 공부하는 SandBox는 **보호된 영역 안에서 프로그램을 작동시키는 보안 모델**입니다

어어? 벌써 나가시지 마시고 한번 들어보세요!

### 근데 iOS랑 무슨 관련인가요?

iOS의 모든 앱들이 이 SandBox 모델을 따르기 때문입니다

![image](https://user-images.githubusercontent.com/81547954/178443797-d8b68437-8515-45f2-acad-35eaa4523af3.png)

iOS는 기본적으로 앱 마다 별도의 **파일을 생성하여 공유**되지 않도록 한다. 외부의 공격으로부터 앱이 손상된 경우,
**시스템과 사용자 데이터의 피해를 최소화**한다.

추가로 앱스토어를 통해 배포되는 **모든 앱들은 App SandBox를 적용**해야 한다. 다른 곳으로 유통하는 앱도 마찬가지!

다들 iOS 보안이 좋다는 소리 한번쯤 들으셨죠? 그 이유가 바로 App SandBox를 적용했기 때문입니다!

참고: https://velog.io/@gnwjd309/iOS-sandbox
