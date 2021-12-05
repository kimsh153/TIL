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
프로젝트를 생성을 하시면 프로젝트 파일, 소스 파일들이 추가된 것을 확인할 수 있습니다.

프로젝트 관련 소스인 Project.swift만을 관리하고 수정하는 명령어인 ``tuist edit``를 실행합니다.
```
$ tuist edit
```
