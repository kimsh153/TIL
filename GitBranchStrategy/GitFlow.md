# GitFlow

GitFlow는 기능이 아니라 서로간의 약속인 방법론입니다. <br>그리고 GitFlow를 생각해낸 사람도 GitFlow는 완벽한 방법론은 아니고 각자 개발 환경에 따라 수정하고 변형해서 사용하라고 말했습니다.

`GitFlow`는 협업을 하거나 프로젝트의 규모가 커지면 소스코드를 관리하기에 용이하다.

GitFlow는 5가지 브랜치를 사용하여 운영을 합니다.

* **master** : 기준이 되는 브랜치로 제품을 베포하는 브랜치 입니다.
* **develop** : 개발 브랜치로 개발자들이 이 브랜치를 기준으로 각자 작업한 기능들을 합(Merge)칩니다.
* **feature** : 단위 기능을 개발하는 브랜치로 기능 개발이 완료되면 develop 브랜치에 합칩니다.
* **release** : 배포를 위해 master 브랜치로 보내기 전에 먼저 QA(품질검사)를 하기위한 브랜치입니다.
* **hotfix** : master 브랜치로 베포를 했는데 버그가 생겼을 때 긴급 수정하는 브랜치입니다.


> master와 develop가 중요한 매인 브랜치이고 나버지는 필요에 의해서 운영하는 브랜치라고 보시면 됩니다.

![99CD994C5E69CCF223](https://user-images.githubusercontent.com/81547954/144524999-a1f4b4f4-8051-4ad2-ad5c-be099b32a8ad.png)

출처 : https://ux.stories.pe.kr/183
