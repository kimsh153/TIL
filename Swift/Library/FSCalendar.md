# FSCalendar

### FSCalendar?
iOS에서 달력을 쉽게 사용할 수 있는 라이브러리입니다

![4fabae40-69f2-11e5-97ab-afbacd0a3da2](https://user-images.githubusercontent.com/81547954/177998136-3971b4a4-efec-4ccc-801d-80ad5503c2b2.jpg)

사용하는 방법

```swift
let calendar = FSCalendar(frame: CGRect(x: 0, y: 0, width: 320, height: 300))
calendar.dataSource = self
calendar.delegate = self
view.addSubview(calendar)
self.calendar = calendar
```

### 설치법

**CocoaPods**
```swift
pod 'FSCalendar'
```

**SPM**
```
.package(url: "https://github.com/WenchaoD/FSCalendar.git", from: "2.8.3")
```

### 참고: https://github.com/WenchaoD/FSCalendar
