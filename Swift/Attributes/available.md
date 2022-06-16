# available

### available?

available은 선언속성중 하나로 특정 Swift언어 버전 또는 특정 플랫폼 및 OS버전과 관련된 선언의 수명주기(lifecycle)를 나타냅니다

사용가능한 속성(attribute)은 항상 두개이상의 쉼표로 구분된 attribute argument목록과 함께 나타납니다

이러한 argument는 다음 플랫폼 또는 언어 이름 중 하나로 시작합니다

* iOS
* iOSApplicationExtension
* macOS
* macOSApplicationExtension
* watchOS
* watchOSApplicationExtension
* tvOS
* tvOSApplicationExtension
* swift

\*(별표)를 사용하여 위에 나열 된 모든 플랫폼 이름에 대한 선언의 가용성(availability)을 나타낼 수도 있습니다

Swift버전 가용성을 지정하는 사용가능한 attribute는 \*를 사용할 수 없습니다

나머지 argument는 순서에 관계없이 나타낼 수 있으며, 중요한 milestones를 포함하여, 선언의 수명주기에 대한 추가 정보를 지정 할 수 있습니다

#### ● unavailable는 지정된 플랫폼에서 선언을 사용할 수 없음을 나타냅니다. 이 argument는 Swift버전 가용성을 지정할 때 사용 할 수 없습니다

#### ● introduced는 선언이 도입 된 지정된 플랫폼 또는 언어의 첫번째 버전을 나타냅니다

**introduced: `version number`**

버전번호는 1~3개의 양의 정수로 구성되며, 마침표로 구분됩니다

#### ● deprecated는 선언이 사용되지 않는 지정된 플랫폼 또는 언어의 첫번째 버전을 나타냅니다

**deprecated: `version number`**

optional 버전번호는 1~3개의 양의 정수로 구성되며, 마침표로 구분됩니다

버전 번호를 생략하면, 해당 선언이 더이상 사용되지 않으므로 정보는 제공되지 않습니다

버전번호를 생략하면, :(콜론)도 생략하세요

### 참고: https://zeddios.tistory.com/647
