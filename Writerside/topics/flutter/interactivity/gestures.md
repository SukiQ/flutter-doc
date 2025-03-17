# 手势




## GestureDetector

`GestureDetector` 是一个通用的手势检测组件，可以监听多种手势事件。它可以包裹任何 widget，使其能够响应用户的交互

| 属性                     | 说明                               |
| :----------------------- | :--------------------------------- |
| `onTap`                  | 点击事件（轻触屏幕）               |
| `onDoubleTap`            | 双击事件                           |
| `onLongPress`            | 长按事件                           |
| `onPanUpdate`            | 拖动事件（手指在屏幕上移动时触发） |
| `onScaleUpdate`          | 缩放事件（双指缩放时触发）         |
| `onVerticalDragUpdate`   | 垂直拖动事件                       |
| `onHorizontalDragUpdate` | 水平拖动事件                       |
| `onTapDown`              | 手指按下时触发                     |
| `onTapUp`                | 手指抬起时触发                     |
| `onTapCancel`            | 点击取消时触发                     |
| `behavior`               | 手势检测的行为模式（如是否穿透）   |

```dart
GestureDetector(
  onTap: () {
    print('Tapped!');
  },
  onDoubleTap: () {
    print('Double Tapped!');
  },
  onLongPress: () {
    print('Long Pressed!');
  },
  onPanUpdate: (details) {
    print('Dragging: ${details.delta}');
  },
  child: Container(
    width: 200,
    height: 100,
    color: Colors.blue,
    alignment: Alignment.center,
    child: Text('GestureDetector', style: TextStyle(color: Colors.white)),
  ),
);
```



## Dismissible