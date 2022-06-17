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

#### ● obsoleted는 선언이 폐기된 지정된 플랫폼 또는 언어의 첫번째 버전을 나타냅니다

선언이 obsoledted로 지정되면, **지정된 플랫폼 또는 언어에서 제거되고, 더 이상 사용할 수 없습니다**

**obsoleted: `version number`**

버전번호는 1~3개의 양의 정수로 구성되며, 마침표로 구분됩니다

#### ● message는 사용되지 않거나 더 이상 사용되지 않는 사용하는 것에 대한 경고 또는 오류를 표시 할 때, 컴파일러가 표시하는 텍스트 메세지를 제공하는데 사용됩니다

**message: `message`**

메세지는 문자열 리터럴로 구성됩니다

#### ● renamed는 이름이 바뀐 선언의 새 이름을 나타내는 텍스트 메세지를 제공하는데 사용됩니다 

새로운 이름은, 이름이 바뀐 선언의 사용에 관헤 오류를 낼 때 컴파일러에 의해 표시됩니다

**renamed: `new name`**

새 이름은 문자열 리터럴로 구성됩니다

여기까지가 애플 공식 문서에 정리된 내용입니다

available은 사용할때 #available과 @available이 있습니다

### \#available

\#available은 많이 보셨을겁니다

```swift
if #available(iOS 11.0, *) {
      // do something
} else {
      // do something
}
```
이런식으로 써져있는거 보셨을 겁니다

**\#available은 여러 플랫폼에서 서로 다른 논리 처리를 결정하기 위해서 if 또는 guard문과 같이 사용됩니다**

**즉, Bool을 반환하는 런타임 검사입니다**

\*은 필수입니다

주의할 점은, 해당 버전을 포함하여 "**그 이상의 버전**"인지를 확인하는거입니다 그러니까

```swift
if #availabel(iOS 11.0, *) {
            // iOS 11..15
} else {
            // iOS 11..15가 아닌 다른 버전들
}
```
가 되는 것 입니다

### 참고: https://zeddios.tistory.com/647
