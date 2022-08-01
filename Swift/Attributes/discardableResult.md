# discardableResult

### discardableResult? 

`discardable`는 **"버릴 수 없는"** 이라는 의미를 가지고 있습니다

`@discardableResult`의 기능은 return 값을 사용하지 않아도 warning 메세지를 나오지 않도록 설정해줍니다

글로만 설명하지 말고 바로 사용방법을 보시겠습니다!

### @discardableResult를 사용방법

* Warning메세지: "Result of call to 'returnFunction(count:)' is unused"

<img width="839" alt="스크린샷 2022-07-22 오후 9 09 44" src="https://user-images.githubusercontent.com/81547954/180436293-9c7c9d2c-5391-48ce-96a2-dd2ae8be0217.png">

위의 사진을 보시면 returnFunction(count: 30)에서 경고메시지를 띄웁니다

경고 메세지를 지우기 위해 returnFunction 함수 위에  @discardableResult를 쓰면!

<img width="453" alt="스크린샷 2022-07-22 오후 9 13 38" src="https://user-images.githubusercontent.com/81547954/180436912-1d5d16e7-1343-475f-b9e2-32ed9bfba8b3.png">

이런식으로 경고 메세지가 사진것을 보실 수 있습니다!

### 참고: https://ios-development.tistory.com/343
