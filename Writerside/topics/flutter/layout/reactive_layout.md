# 响应式布局



## MediaQuery

`MediaQuery`用于获取关于设备屏幕、布局、文字大小等信息。它为我们提供了动态访问设备的屏幕尺寸、像素密度、设备方向、系统字体大小等信息，使得我们能够根据这些信息进行响应式布局和适配，如：

1. 获取屏幕尺寸
2. 获取设备的像素密度
3. 获取屏幕方向
4. 获取系统字体大小
5. 获取屏幕的安全区域
6. 获取设备的文字缩放因素

| 属性                    | 说明                                                     |
| ----------------------- | -------------------------------------------------------- |
| `size`                  | 获取设备的屏幕尺寸，包括宽度和高度                       |
| `width`                 | 获取屏幕的宽度                                           |
| `height`                | 获取屏幕的高度                                           |
| `devicePixelRatio`      | 获取设备的像素密度，表示每个物理像素对应多少逻辑像素     |
| `orientation`           | 获取设备的屏幕方向（竖屏或横屏）                         |
| `textScaleFactor`       | 获取当前系统的文本缩放因子，表示系统中设置的字体大小比例 |
| `padding`               | 获取设备的安全区域（如状态栏、底部导航栏等）大小         |
| `viewInsets`            | 获取键盘区域的尺寸，通常用于处理键盘弹出时的布局变化     |
| `alwaysUse24HourFormat` | 判断设备是否始终使用 24 小时制                           |
| `accessibleNavigation`  | 判断设备是否启用了可访问性（辅助功能）                   |
| `invertColors`          | 判断设备是否启用了反转颜色                               |
| `platformBrightness`    | 获取当前平台的亮度模式（浅色或深色模式）                 |

```dart
Widget build(BuildContext context) {
  Orientation orientation = MediaQuery.of(context).orientation;

  return Scaffold(
    appBar: AppBar(title: Text("Orientation Example")),
    body: orientation == Orientation.portrait
        ? Column(
            children: <Widget>[
              Container(color: Colors.blue, height: 200),
              Container(color: Colors.green, height: 200),
            ],
          )
        : Row(
            children: <Widget>[
              Expanded(child: Container(color: Colors.blue)),
              Expanded(child: Container(color: Colors.green)),
            ],
          ),
  );
}
```



## LayoutBuilder

`LayoutBuilder` 允许你根据父容器的尺寸来动态构建子部件。`LayoutBuilder` 会根据父容器的实际大小重新构建其子部件，而不是依赖于外部的固定尺寸或约束。因此，它特别适用于响应式布局，在不同屏幕尺寸和分辨率下调整界面元素

`LayoutBuilder` 提供了一个 `builder` 函数，这个函数会根据父容器的约束（  [`BoxConstraints `](box_layout.md#boxconstraints)）来构建子部件。在构建子部件时，你可以使用这些约束来决定如何布局子部件

```dart
LayoutBuilder(
  builder: (BuildContext context, BoxConstraints constraints) {
    // 在这里根据约束（constraints）来决定布局
    return SomeWidget();
  },
)
```

```dart
Widget build(BuildContext context) {
  return LayoutBuilder(
    builder: (context, constraints) {
      if (constraints.maxWidth > 600) {
        // 屏幕宽度大于 600，使用横向布局
        return Row(
          children: <Widget>[
            Expanded(child: Container(color: Colors.blue)),
            Expanded(child: Container(color: Colors.green)),
          ],
        );
      } else {
        // 屏幕宽度小于 600，使用纵向布局
        return Column(
          children: <Widget>[
            Container(color: Colors.blue, height: 200),
            Container(color: Colors.green, height: 200),
          ],
        );
      }
    },
  );
}

```

