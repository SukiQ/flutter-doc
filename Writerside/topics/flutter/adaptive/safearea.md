# 安全区域

**安全区域（Safe Area）** 是指屏幕上那些不会被系统 UI 元素（如状态栏、导航栏、刘海屏、圆角等）遮挡的区域。安全区域确保你的 UI 元素不会被这些系统 UI 元素覆盖或遮挡



## SafeArea

`SafeArea`会自动根据设备的屏幕边缘、刘海、圆角等内容调整子元素的布局，确保子元素不会被遮挡

| 属性      | 说明                                                  |
| --------- | ----------------------------------------------------- |
| `child`   | 要放入安全区域的子组件                                |
| `top`     | 是否考虑屏幕顶部的安全区域（如状态栏）                |
| `bottom`  | 是否考虑屏幕底部的安全区域（如导航栏、HomeIndicator） |
| `left`    | 是否考虑屏幕左侧的安全区域                            |
| `right`   | 是否考虑屏幕右侧的安全区域                            |
| `minimum` | 用来设置安全区域的最小边距                            |

```dart
 SafeArea(
          child: Column(
            mainAxisAlignment: MainAxisAlignment.center,
            children: <Widget>[
              Text('This text is in a safe area!'),
              Icon(Icons.star, size: 50),
            ],
          )
```

