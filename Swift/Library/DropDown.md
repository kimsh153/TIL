# DropDown

### DropDown

Swift로 작성된 iOS용 Material Design 드롭다운입니다

<img width="127" alt="스크린샷 2022-03-03 오전 9 33 56" src="https://user-images.githubusercontent.com/81547954/156473311-4e667063-267f-4a2e-8748-9dfb7cad8f04.png">


### 설치법

**Cocoapod**

```
pod 'DropDown'
```

### 사용법

1.import

라이브러리를 사용하기 위해 import 해줍니다

```swift
import DropDown
```

2.객체 생성

DropDown객체를 만들어줍니다

```swift
let dropDown = DropDown()
```

3.데이터 넣기 

만든 dropDown객체에 데이터를 넣어줍니다

```swift
dropDown.dataSource = ["하나", "둘", "셋", "넷"]
```

4.드롭다운 보이기

드롭다운을 보여줍니다

```swift
dropDown.show()
```

### 참고 : https://github.com/AssistoLab/DropDown , https://gonslab.tistory.com/9
