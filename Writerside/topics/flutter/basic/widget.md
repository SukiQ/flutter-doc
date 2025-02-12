# Widget



## Widget状态



### StatelessWidget

没有任何随时间变化的属性（例如icon或label）

```dart
class MyWidget extends StatelessWidget {
  
  @override
  Widget build(BuildContext context) {
    ...
  }
}
```



### StatefulWidget

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



## 生命周期

![](widget-0.png)



### Widget生命周期 {id="widget_1"}

- createElement: 当创建一个Widget时，框架会调用其构造函数生成一个对应的Element对象。
- build: 每当Widget的状态改变或依赖于它的任何其他状态发生改变时，都会调用build方法来重新构建UI。build方法必须是无状态的，且需要返回一个新的Widget树
- updateShouldNotify (对于StatelessWidget的shouldRebuild): 当父Widget重建并触发子Widget重建时，这个方法会被调用来决定当前Widget是否需要进行实际的重建
- dispose: 对于实现了DisposableWidget接口的Widget，在它们从树中移除时，会调用dispose方法以释放资源

### State生命周期

- createState: 创建StatefulWidget时，会调用此方法创建关联的State对象
- initState: 在State对象被创建后立即调用，用于初始化工作，通常在这里设置监听器或其他一次性设置操作
- didChangeDependencies: 在依赖项更改后但在build之前调用。例如，如果State对象依赖InheritedWidget，则在此处获取最新的依赖值
- build: 同Widget的build，每当State对象的状态发生变化时，都会调用该方法来更新界面
- setState: 由开发人员主动调用，用于通知框架State已更改，并触发build过程。
- didUpdateWidget: 在StatefulWidget的配置参数更改时调用，允许State处理新的Widget配置。
- deactivate: 当State对象离开活跃树（但可能尚未销毁）时调用，可以用于清理不需要但不涉及资源释放的操作
- dispose: 当State对象将永久从树中删除时调用，这是释放所有资源的地方，如关闭打开的流、取消计时器等



## 渲染

![](widget-1.png)