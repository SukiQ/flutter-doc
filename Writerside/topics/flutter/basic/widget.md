# Widget

Widget 是 Flutter 应用用户界面的构建块



## StatelessWidget

没有任何随时间变化的属性（例如icon或label）

```dart
class MyWidget extends StatelessWidget {
  
  @override
  Widget build(BuildContext context) {
    ...
  }
}
```



## StatefulWidget

需要根据用户交互或其他因素进行更改，用户界面是通过`State`对象构建的，每当改变`State`对象时，需要调用 `setState()`方法来通知框架更新用户界面`State`

```dart
class MyWidget extends StatefulWidget {

  @override
  State<StatefulWidget> createState() {
    return _MyWidgetState();
  }
}
class _MyWidgetState extends State<MyWidget> {
  
  @override
  Widget build(BuildContext context) {
    ...
  }
}
```