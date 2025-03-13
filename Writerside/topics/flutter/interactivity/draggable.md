# 拖动



## APP内拖动


### Draggable

`Draggable` 和 `DragTarget` 用于实现拖拽功能。`Draggable` 表示可以拖拽的组件，`DragTarget` 表示可以接收拖拽目标的区域

```dart
Draggable<int>(
  data: 10,
  child: Container(
    width: 100,
    height: 100,
    color: Colors.blue,
    child: Center(child: Text('Drag Me')),
  ),
  feedback: Container(
    width: 100,
    height: 100,
    color: Colors.blue.withOpacity(0.5),
    child: Center(child: Text('Dragging')),
  ),
  childWhenDragging: Container(
    width: 100,
    height: 100,
    color: Colors.grey,
  ),
);

DragTarget<int>(
  onAccept: (data) {
    print('Accepted: $data');
  },
  builder: (context, candidateData, rejectedData) {
    return Container(
      width: 100,
      height: 100,
      color: Colors.red,
      child: Center(child: Text('Drop Here')),
    );
  },
);
```



### LongPressDraggable

`LongPressDraggable` 是一个专门用于处理长按拖拽操作的组件。它结合了长按手势（`onLongPress`）和拖拽功能（`Draggable`），允许用户在长按某个组件后开始拖拽操作

| 属性                      | 说明                                                         |
| ------------------------- | ------------------------------------------------------------ |
| `data`                    | 拖拽时传递的数据，通常会在 `DragTarget` 的 `onAccept` 中接收 |
| `feedback`                | 拖拽时显示的组件，通常是拖拽内容的半透明版本                 |
| `childWhenDragging`       | 拖拽时原位置的占位组件。如果未设置，原位置会显示为空         |
| `child`                   | 正常状态下显示的组件                                         |
| `onDragStarted`           | 拖拽开始时的回调                                             |
| `onDragEnd`               | 拖拽结束时的回调，返回 `DraggableDetails` 对象               |
| `onDraggableCanceled`     | 拖拽被取消时的回调，返回 `Velocity` 和 `Offset`              |
| `maxSimultaneousDrags`    | 同时允许的最大拖拽数量。默认值为 `1`                         |
| `axis`                    | 限制拖拽方向<br/> `Axis.horizontal`: 水平<br/> `Axis.vertical`: 垂直 |
| `feedbackOffset`          | 拖拽时 `feedback` 组件相对于指针的偏移量                     |
| `dragAnchorStrategy`      | 拖拽锚点策略，决定 `feedback` 组件如何跟随指针移动           |
| `ignoringFeedbackPointer` | 是否忽略 `feedback` 组件的指针事件。默认值为 `true`          |
| `hapticFeedbackOnStart`   | 拖拽开始时是否触发触觉反馈（如振动）                         |
| `affinity`                | 拖拽的亲和力方向，用于控制拖拽的优先级                       |
| `delay`                   | 长按触发拖拽的延迟时间。默认值为 `kLongPressTimeout`（约 500 毫秒） |



## APP间拖动 {id="app_1"}


### super_drag_and_drop

`super_drag_and_drop`提供更强大的拖放功能，尤其是在桌面平台上（如 Windows、macOS 和 Linux）。它扩展了 Flutter 内置的拖放功能，支持更复杂的场景，例如跨应用程序拖放、自定义拖放数据格式等

- 导入

```yaml
dependencies:
  super_drag_and_drop: ^0.8.24
```

