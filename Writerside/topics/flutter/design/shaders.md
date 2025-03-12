# 着色



## 画布

### CustomPaint

`CustomPaint`提供了一个画布（`Canvas`），允许你通过 `CustomPainter` 来实现自定义的图形绘制。`CustomPaint` 非常适合需要绘制复杂图形、图表、自定义 UI 元素等场景

```dart
CustomPaint(
  size: Size(300, 300), // 画布大小
  painter: MyPainter(), // 背景绘制
  foregroundPainter: MyForegroundPainter(), // 前景绘制
  child: Text('Hello, CustomPaint!'), // 子部件
)
```



### CustomPainter 

`CustomPainter` 是一个抽象类，你需要实现它的两个方法：

- **`paint`**: 在这里编写绘制逻辑

- **`shouldRepaint`**: 决定是否需要重新绘制。通常根据属性是否变化来决定

```dart
class MyPainter extends CustomPainter {
  @override
  void paint(Canvas canvas, Size size) {
    // 在这里编写绘制逻辑
    final paint = Paint()
      ..color = Colors.blue
      ..strokeWidth = 5
      ..style = PaintingStyle.stroke;

    // 绘制一个圆形
    canvas.drawCircle(Offset(size.width / 2, size.height / 2), 100, paint);
  }

  @override
  bool shouldRepaint(covariant CustomPainter oldDelegate) {
    return false; // 如果返回 true，则会重新绘制
  }
}
```



### Canvas

`Canvas` 是一个用于自定义绘图和图形的强大工具。它允许你直接在屏幕上创建自定义形状、路径和设计

| 属性            | 说明                                   |
| --------------- | -------------------------------------- |
| `drawLine`      | 绘制一条直线                           |
| `drawRect`      | 绘制一个矩形                           |
| `drawCircle`    | 绘制一个圆形                           |
| `drawOval`      | 绘制一个椭圆                           |
| `drawArc`       | 绘制一个弧形                           |
| `drawRRect`     | 绘制一个圆角矩形                       |
| `drawPath`      | 绘制一个自定义路径（`Path` 对象）      |
| `drawPoints`    | 绘制一系列点                           |
| `drawRawPoints` | 绘制一系列原始点（使用 `Float32List`） |
| `drawImage`     | 绘制一个图像                           |
| `drawImageRect` | 绘制图像的某一部分到指定的矩形区域     |
| `drawImageNine` | 使用九宫格缩放绘制图像                 |
| `drawAtlas`     | 绘制一个图集（多个图像组合）           |
| `drawParagraph` | 绘制一个段落（`Paragraph` 对象）       |
| `drawShadow`    | 绘制路径的阴影                         |
| `translate`     | 平移画布                               |
| `scale`         | 缩放画布                               |
| `rotate`        | 旋转画布                               |
| `skew`          | 倾斜画布                               |
| `transform`     | 应用矩阵变换                           |
| `save`          | 保存当前画布状态                       |
| `restore`       | 恢复之前保存的画布状态                 |
| `saveLayer`     | 保存当前画布状态到一个新的图层         |
| `clipPath`      | 使用路径裁剪画布                       |
| `clipRect`      | 使用矩形裁剪画布                       |
| `clipRRect`     | 使用圆角矩形裁剪画布                   |
| `getSaveCount`  | 获取当前保存状态的次数                 |
| `drawColor`     | 用颜色填充整个画布                     |
| `drawPaint`     | 用 `Paint` 对象填充整个画布            |
| `drawVertices`  | 绘制顶点（用于自定义网格绘制）         |
| `drawDRRect`    | 绘制一个双圆角矩形（内外两个圆角矩形） |

```dart
class MyPainter extends CustomPainter {
  @override
  void paint(Canvas canvas, Size size) {
    final paint = Paint()
      ..color = Colors.blue
      ..strokeWidth = 5
      ..style = PaintingStyle.stroke;

    // 绘制直线
    canvas.drawLine(Offset(0, 0), Offset(size.width, size.height), paint);

    // 绘制矩形
    final rect = Rect.fromLTWH(50, 50, 200, 100);
    canvas.drawRect(rect, paint);

    // 绘制圆形
    canvas.drawCircle(Offset(size.width / 2, size.height / 2), 50, paint);

    // 绘制路径
    final path = Path();
    path.moveTo(0, 0);
    path.lineTo(size.width, 0);
    path.lineTo(size.width / 2, size.height);
    path.close();
    canvas.drawPath(path, paint);

    // 平移画布
    canvas.translate(100, 100);
    canvas.drawRect(Rect.fromLTWH(0, 0, 50, 50), paint);
  }

  @override
  bool shouldRepaint(covariant CustomPainter oldDelegate) {
    return false;
  }
}
```

