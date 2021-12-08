# Tuist

``Tuist``는 프로젝트 관리 도구 입니다.

#### Tuist install하는 방법
* 여기 나오는 코드는 전부 iterm에서 실행합니다.
```
$ bash <(curl -Ls https://install.tuist.io)
```

#### 프로젝트 생성
```
$ mkdir MyApp
$ cd MyAPP
$ tuist init --platform ios
```
tuist init을 하면 아래와 같은 파일들이 자동으로 생성됩니다.

<img width="272" alt="스크린샷 2021-12-08 오후 10 29 10" src="https://user-images.githubusercontent.com/81547954/145216537-7566bcdb-b592-4a3e-a2be-9d36ef4b6ed0.png">


프로젝트 파일을 만들기 위해 ``tuist generate``를 사용하겠습니다.

```
$ tuist generate
```
위 명령어를 사용하면 xcodeproj와 xcworkspace를 생성합니다.

<img width="262" alt="스크린샷 2021-12-08 오후 10 30 35" src="https://user-images.githubusercontent.com/81547954/145216698-5b93e622-142c-460c-8e80-0d101b7480b0.png">



#### 출처 : https://okanghoon.medium.com/xcode-%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8-%EA%B4%80%EB%A6%AC%EB%A5%BC-%EC%9C%84%ED%95%9C-tuist-%EC%95%8C%EC%95%84%EB%B3%B4%EA%B8%B0-6a92950780be
