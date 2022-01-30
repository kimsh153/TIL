# PinLayout

### PinLayout이란

**Auto layout 없이 Swift View layout을 구성할 수 있도록 도와주는 프레임워크(Auto layout을 사용하지 않고 수동으로 view를 layout합니다.)**

```
수동으로 layouting하므로 디바이스 회전을 포함한 컨테이너 크기의 변경을 처리하려면 
UIView.layoutSubviews() 또는 UIViewController.viewDidLayoutSubviews() 내부에서 레이아웃
을 업데이트해야합니다.
```

### PinLayout의 성능

![benchmark_comparison_all_small](https://user-images.githubusercontent.com/81547954/151690924-ce8c5205-a8cb-4292-a91f-5658d27e68d5.png)

PinLayout은 수동 레이아웃보다 빠르거나 같으며 자동 렝이아웃보다 8배에서 12배 빠릅니다.


### 참고 : https://zeddios.tistory.com/1243, https://github.com/layoutBox/PinLayout
