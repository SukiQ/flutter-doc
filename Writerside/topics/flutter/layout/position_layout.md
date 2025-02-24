# 定位布局



## Stack

`Stack` 允许将多个子部件堆叠在一起，子部件按顺序叠加在屏幕上，后添加的子部件会覆盖前面的子部件。`Stack` 经常用于实现重叠的 UI 元素，如浮动按钮、气泡提示等

| 属性            | 说明                                                         |
| --------------- | ------------------------------------------------------------ |
| `alignment`     | [`AlignmentGeometry`](align.md#alignmentgeometry)对齐方式            |
| `textDirection` | 表示水平方向子组件的布局顺序(是从左往右还是从右往左)<br/>`TextDirection.rtl`：从右到左 <br/>`TextDirection.ltr`：从左到右 |
| `fit`           | 填充方式：<br/>`StackFit.loose`：Stack 的大小将由其最大的非定位子部件（即没有包裹在 Align / Positioned 中的子部件）决定<br/>`StackFit.expand`：伸以填满 Stack 的整个区域<br/>`StackFit.passthrough`：不改变其原始尺寸 |
| `clipBehavior`  | 裁剪行为：<br/>`Clip.none`：不裁剪<br/>`Clip.hardEdge`：裁剪但是不应用抗锯齿<br/>`Clip.antiAlias`：裁剪而且抗锯齿<br/>`Clip.antiAliasWithSaveLayer`：图层抗锯齿 |

```dart
Stack(
  children: <Widget>[
    Container(
      width: 200,
      height: 200,
      color: Colors.blue,
    ),
    Positioned(
      top: 30,
      left: 30,
      child: Container(
        width: 100,
        height: 100,
        color: Colors.red,
      ),
    ),
    Positioned(
      bottom: 10,
      right: 10,
      child: Icon(Icons.star, size: 50, color: Colors.yellow),
    ),
  ],
)
```



## Positioned

`Positioned`用于在 `Stack` 布局中定位子部件。它允许你通过设置子部件的相对位置（通过 `top`, `bottom`, `left`, `right` 等属性）精确控制子部件在 `Stack` 中的位置。`Positioned` 是一个包装类，它让你可以在 `Stack` 内自由地对元素进行定位，而不需要依赖默认的对齐方式

```dart
Stack(
                  children: [
                    Positioned(
                        top: 100,
                        left: 200,
                        child: Container(
                          width: 300,
                          height: 300,
                          color: Colors.indigo,
                        )),
                    Positioned(
                        top: 300,
                        right: 40,
                        child: Container(
                          width: 250,
                          height: 250,
                          color: Colors.teal,
                        ))
                  ],
                )
```



## Align

`Align` 用于在父容器内对齐其子部件。它通过 `alignment` 属性来控制子部件在父容器内的对齐方式。这个对齐方式可以是固定的，也可以根据容器的尺寸进行动态调整

| 属性            | 说明                                                    |
| -------------- |-------------------------------------------------------|
| `alignment`    | [`AlignmentGeometry`](align.md#alignmentgeometry)对齐方式 |
| `textDirection` | 表示水平方向子组件的布局顺序(是从左往右还是从右往左)                           |
| `widthFactor`  | Align组件宽度，默认为空，表示全占满，如果有值，组件宽度=子组件宽度 * widthFactor    |
| `heightFactor` | Align组件高度，默认为空，表示全占满，如果有值，组件高度=子组件高度 * heightFactor   |

```dart
Stack(
        children: [
          Align(
            alignment: Alignment.center,
            child: Container(child: Text('center'),),
          ),
          Align(
            alignment: Alignment.topLeft,
            child: Container(child: Text('topLeft'),),
          ),
          Align(
            alignment: Alignment.topRight,
            child: Container(child: Text('topRight'),),
          )
        ],
      )
```

<note>如果child小于父组件，一般使用 Align 包裹。如果child可以大于父组件，请考虑将其包裹在 SingleChildScrollView 或 OverflowBox 中</note>
