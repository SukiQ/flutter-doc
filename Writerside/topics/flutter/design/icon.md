# 图标



| 属性            | 说明                                                         |
| :-------------- | :----------------------------------------------------------- |
| `icon`          | 指定要显示的图标。可以是 `Icons` 或 `CupertinoIcons` 中的图标 |
| `size`          | 图标的大小，单位为逻辑像素                                   |
| `color`         | 图标的颜色。可以通过 `Colors` 类指定颜色，如 `Colors.red`    |
| `semanticLabel` | 为图标提供语义标签，用于辅助功能（如屏幕阅读器）             |
| `textDirection` | 图标的方向（从左到右或从右到左）。通常不需要设置             |
| `shadows`       | 为图标添加阴影效果。可以设置多个阴影                         |
| `grade`         | 图标的粗细程度（仅适用于部分图标字体）                       |
| `opticalSize`   | 图标的光学尺寸，用于调整图标的视觉比例                       |
| `fill`          | 图标的填充程度（仅适用于部分图标字体）                       |
| `weight`        | 图标的粗细（仅适用于部分图标字体）                           |

```dart
Icon(
  Icons.favorite, // 图标
  size: 50.0, // 大小
  color: Colors.red, // 颜色
  semanticLabel: 'Favorite Icon', // 语义标签
  shadows: [
    Shadow(
      color: Colors.black,
      offset: Offset(2.0, 2.0),
      blurRadius: 3.0,
    ),
  ], // 阴影效果
)
```



- 使用  **[Material Icons](https://fonts.google.com/icons)** 库（默认）

```dart
Icon(
       Icons.home,
       color: Colors.blue,
       size: 20.0,
     )
```

- 使用  **[Cupertino  Icons](https://cupertino-icons.web.app/)** 库

```dart
Icon(
       CupertinoIcons.home,
       color: Colors.blue,
       size: 20.0,
     )
```



## 自定义图标



- 在 `pubspec.yaml` 文件中声明字体文件

```yaml
flutter:
  fonts:
    - family: CustomIcons # 字体名称
      fonts:
        - asset: assets/fonts/custom_icons.ttf # 字体文件路径
```



- 定义 `IconData`

在 Dart 文件中定义自定义图标的 `IconData`。你需要知道每个图标在字体文件中的 Unicode 码点（通常可以从字体文件的文档或工具中获取）

```dart
class CustomIcons {
  // 定义图标的 Unicode 码点
  static const IconData home = IconData(0xe900, fontFamily: 'CustomIcons');
  static const IconData settings = IconData(0xe901, fontFamily: 'CustomIcons');
  static const IconData star = IconData(0xe902, fontFamily: 'CustomIcons');
}
```



- 使用自定义图标

```dart
 Icon(
                CustomIcons.settings,
                size: 50.0,
                color: Colors.grey,
              ),
```

