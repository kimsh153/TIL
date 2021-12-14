# GithubFlow

`GithubFlow`는 `GitFlow`랑 다르게 `Github`에서 사용하기 용이하게 만들어진 방법입니다. 그리고 **자동화의 개념**이 들어가 있습니다.

GithubFlow는 흐름이 단순합니다. 그리고 그 만큼 룰도 단순합니다.

![20151104223339](https://user-images.githubusercontent.com/81547954/145706812-e3b083ee-e0e9-45ff-a47a-bd8b5f628e92.png)

`master`브랜치에 어떻게 올릴지 `role`을 정확히 정확하다면 나머지 브랜치들에는 관여를 하지 않습니다. 그리고 Pull request 기능을 사용하도록 권장합니다.

## 사용 방법
### 1.`master`브랜치는 어떤 때든 배포가 가능하다.
`master`브랜치는 항상 최신의 상태이며, stable(안정적인) 상태로 Product(제품)에 배포되는 브랜치입니다. 그리고 이 브랜치는 엄격한 role를 주고 사용해야 합니다.
### 2. 새로운 일을 시작하기 위해 브랜치를 `master`에서 딴다면 이름은 어떤일을 하는지 명확하게 작성한다.
`github flow`는 `feature`와`develop`과 같은 브랜치가 존재하지 않습니다. 그렇기에 **자세하게 어떤 일을 하고 있는지에 대해서 작성** 해줘야합니다. 그래야 Github 페이지에서 어떤 일들이 진행되고 있는지 확인할 수 있기 때문입니다.

### 3. 원격지(remote) 브랜치로 수시로 push를 한다.

#### 참고 : https://ujuc.github.io/2015/12/16/git-flow-github-flow-gitlab-flow/
