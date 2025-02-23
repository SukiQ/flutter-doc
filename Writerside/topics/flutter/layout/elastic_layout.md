# 弹性布局



## Flex

`Flex` 是一个灵活的布局小部件，用于创建基于主轴和交叉轴的布局。它是 `Row` 和 `Column` 的底层实现，可以通过设置 `direction` 属性来决定子组件的排列方向（水平或垂直）。`Flex` 提供了更高级的布局控制能力，适合需要动态调整布局的场景

| 属性        | 说明                                                         |
| ----------- | ------------------------------------------------------------ |
| `direction` | 布局方向<br/>`Axis.horizontal`：水平布局，等同与`Row`<br/>`Axis.vertical`：垂直布局，等同与`Column` |

```dart
Flex(
  direction: Axis.horizontal, // 可以选择 Axis.vertical
  children: [
    Expanded(
      child: Container(
        color: Colors.red,
        height: 50,
      ),
    ),
    Expanded(
      child: Container(
        color: Colors.green,
        height: 50,
      ),
    ),
    Expanded(
      child: Container(
        color: Colors.blue,
        height: 50,
      ),
    ),
  ],
)
```



## Expanded

`Expanded` 使得它包裹的子组件在主轴方向（即 `Row` 的水平方向或 `Column` 的垂直方向）占据可用的剩余空间。简而言之，它会让子组件尽可能地扩展，以填满父布局中的可用空间

| 属性   | 说明     |
| ------ | -------- |
| `flex` | 弹性系数 |

```dart
Column(
        children: [
          Expanded(
              flex: 1,
              child: Container(
                height: 50,
                color: Colors.deepOrangeAccent,
              )),
          Expanded(
              flex: 2,
              child: Container(
                height: 50,
                color: Colors.amberAccent,
              )),
          Expanded(
              flex: 3,
              child: Container(
                height: 50,
                color: Colors.deepPurple,
              ))
        ],
      )
```



## Wrap

`Wrap`用于将子组件按行或列自动换行。它通常用于当子组件数量不固定，且子组件的尺寸可能会超出父容器的可用空间时，能够自动换行或者换列



| 属性                 | 说明                                                         |
| -------------------- | ------------------------------------------------------------ |
| `direction`          | 主轴的方向，默认水平                                         |
| `alignment`          | 主轴对齐方式                                                 |
| `spacing`            | 主轴方向上子组件之间的间距                                   |
| `runAlignment`       | 整体子组件相对于父组件的辅轴对齐方式                         |
| `runSpacing`         | 辅轴的间距                                                   |
| `crossAxisAlignment` | 辅轴对齐方式                                                 |
| `textDirection`      | 表示水平方向子组件的布局顺序(是从左往右还是从右往左) <br/>`TextDirection.rtl`：从右到左<br/>`TextDirection.ltr`：从左到右 |
| `verticalDirection`  | 垂直方向朝向                                                 |
| `clipBehavior`       | 裁剪行为：<br/>`Clip.none`：不裁剪 <br/>`Clip.hardEdge`：裁剪但是不应用抗锯齿<br/>`Clip.antiAlias`：裁剪而且抗锯齿<br/>`Clip.antiAliasWithSaveLayer`：图层抗锯齿 |

```dart
Wrap(
      spacing: 10.0,
      alignment: WrapAlignment.spaceEvenly,
      runSpacing: 10.0,
      children: <Widget>[
        Container(height: 100, width: 100, color: Colors.teal,),
        Container(height: 100, width: 100, color: Colors.redAccent,),
        Container(height: 100, width: 100, color: Colors.amberAccent,),
        Container(height: 100, width: 100, color: Colors.green,),
        Container(height: 100, width: 100, color: Colors.pink,),
        Container(height: 100, width: 100, color: Colors.orange,)

      ],
    )
```

