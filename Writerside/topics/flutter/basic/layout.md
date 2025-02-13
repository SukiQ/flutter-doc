# 布局



## 盒子布局

### AspectRatio

尝试将子组件调整为固定宽高比

| 属性        | 解释     |
| ----------- | -------- |
| aspectRatio | 宽高比例 |

```dart
AspectRatio(
        aspectRatio: 16 / 9, // 宽高比为16:9
        child: Container(
          decoration: BoxDecoration(color: Colors.blue),
        ),
      )
```



### ConstrainedBox

用于给其子组件添加额外的尺寸约束，通过设置 `constraints` （[`BoxConstraints`](layout.md#boxconstraints)）参数，可以对子组件的最小和最大宽度、最小和最大高度进行限制

| 属性        | 解释     |
| ----------- | -------- |
| constraints | 限制参数 |

```dart
ConstrainedBox(
  constraints: const BoxConstraints.expand(),
  child: const Card(child: Text('Hello World!')),
)
```

<note>ConstrainedBox 并不会直接修改子组件的尺寸，而是通过强制子组件遵守给定的约束来调整其大小。它常用于你需要明确指定一个组件的最小和最大尺寸的场景</note>



### BoxConstraints

BoxConstraints可以通过设置`minWidth`，`maxWidth`，`minHeight`，`maxHeight`限制子组件的大小

- BoxConstraints.expand(`width?`,`height?`)

  展开约束，如果 `width`/`height` 为空则最大/最小宽高均无限大，如果不为空最大/最小宽高均为`width`/`height` 大小

- BoxConstraints.loose(`Size`)

  松约束，最小宽高为 0，最大宽高为width/height

- BoxConstraints.tight(`Size`)

  紧约束，最小最大宽高均等为width/height

- BoxConstraints.tightFor(`width?`,`height?`)

  单侧松约束，如果`width`/`height`不为空则紧约束不为空的边，为空则松约束该边

- BoxConstraints.tightForFinite(`width?`,`height?`)

  与BoxConstraints.tightFor相同，不同的是如果设置为无限大`double.infinity`，那么依然会松约束



### Container

Container是一个多功能容器组件

| 属性                 | 解释                                                                                                                             | 默认值      |
| -------------------- |--------------------------------------------------------------------------------------------------------------------------------| ----------- |
| alignment            | [`AlignmentGeometry`](layout.md#alignmentgeometry) 对齐方式                                                                                        |             |
| padding              | 内边距                                                                                                                            |             |
| color                | 颜色                                                                                                                             |             |
| decoration           | 背景样式                                                                                                                           |             |
| foregroundDecoration | 前景样式                                                                                                                           |             |
| width                | 宽度                                                                                                                             |             |
| height               | 高度                                                                                                                             |             |
| constraints          | [`BoxConstraints`](layout.md#boxconstraints)约束                                                                                 |             |
| margin               | 外边距                                                                                                                            |             |
| transform            | 变化                                                                                                                             |             |
| transformAlignment   | 变化时对齐方式                                                                                                                        |             |
| clipBehavior         | 裁剪行为： <br/>`Clip.none`：不裁剪<br/>`Clip.hardEdge`：裁剪但是不应用抗锯齿<br/>`Clip.antiAlias`：裁剪而且抗锯齿<br/>`Clip.antiAliasWithSaveLayer`：图层抗锯齿 | `Clip.none` |



### SizedBox

`Sizebox`相对于`Container`更简单，且可以使用`const`定义



## 线性布局

| 属性               | 解释                                                         | 默认值                      |
| ------------------ | ------------------------------------------------------------ | --------------------------- |
| mainAxisAlignment  | 子组件的主轴对齐方式，只有当`mainAxisSize`的值为`MainAxisSize.max`时，此属性才有意义 | `MainAxisAlignment.start`   |
| mainAxisSize       | 子组件在主轴方向占用的空间 `MainAxisSize.max`，尽可能多的占用空间，此时无论子 widgets 实际占用多少水平空间，父组件宽度始终等于主轴方向的最大宽度 `MainAxisSize.min`尽可能少的占用水平空间，当子组件没有占满剩余空间，则父组件的实际宽度等于所有子组件占用的空间 | `MainAxisSize.max`          |
| crossAxisAlignment | 表示子组件在辅轴方向的对齐方式                               | `CrossAxisAlignment.center` |
| textDirection      | 表示水平方向子组件的布局顺序(是从左往右还是从右往左) `TextDirection.rtl`：从右到左 `TextDirection.ltr`：从左到右 |                             |
| verticalDirection  | 表示垂直方向自组建的布局顺序                                 | `VerticalDirection.down`    |
| textBaseline       | 基线对齐规则 `TextBaseline.alphabetic`：字母基线 `TextBaseline.ideographic`：表意基线 |                             |

### MainAxisAlignment

![](layout-0.png)

### crossAxisAlignment

![](layout-1.png)

<warning>CrossAxisAlignment.baselin为基于基线对齐，设置该属性必须设置属性textBaseline</warning>



### Row

```dart
const Row(
                  mainAxisSize: MainAxisSize.max,
                  children: [Text('1'), Text('2'), Text('3')],
                )
```



### Column

```dart
const Column(
                  mainAxisSize: MainAxisSize.max,
                  children: [Text('1'), Text('2'), Text('3')],
                )
```



## 弹性布局



### Flex

Flex是`Row`和`Column`的父类，当然也可以直接使用Flex（在方向不确定的时候）

| 属性      | 解释                                                         |
| --------- | ------------------------------------------------------------ |
| direction | 布局方向 `Axis.horizontal`：水平布局，等同与`Row` `Axis.vertical`：垂直布局，等同与`Column` |



### Expanded

Expanded是弹性布局的一部分，它必须做为`Flex`的子组件，可以动态调整子组件的尺寸

| 属性 | 解释     |
| ---- | -------- |
| flex | 弹性系数 |

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



### Wrap

Wrap突破了单行的限制，在单行元素饱和后可以自动折行

| 属性               | 解释                                                         | 默认值                     |
| ------------------ | ------------------------------------------------------------ | -------------------------- |
| direction          | 主轴的方向，默认水平                                         | `Axis.horizontal`          |
| alignment          | 主轴对齐方式                                                 | `WrapAlignment.start`      |
| spacing            | 主轴方向上子组件之间的间距                                   | `0.0`                      |
| runAlignment       | 整体子组件相对于父组件的辅轴对齐方式                         | `WrapAlignment.start`      |
| runSpacing         | 辅轴的间距                                                   | `0.0`                      |
| crossAxisAlignment | 辅轴对齐方式                                                 | `WrapCrossAlignment.start` |
| textDirection      | 表示水平方向子组件的布局顺序(是从左往右还是从右往左) `TextDirection.rtl`：从右到左 `TextDirection.ltr`：从左到右 |                            |
| verticalDirection  | 垂直方向朝向                                                 | `VerticalDirection.down`   |
| clipBehavior       | 裁剪行为：<br/>`Clip.none`：不裁剪 <br/>`Clip.hardEdge`：裁剪但是不应用抗锯齿<br/>`Clip.antiAlias`：裁剪而且抗锯齿<br/>`Clip.antiAliasWithSaveLayer`：图层抗锯齿 | `Clip.none`                |

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



## 定位布局

### Stack

Stack允许子Widget按照代码顺序堆叠起来。并可以利用其相关属性调整其子Widget的位置

<note>可以使用 alignment 属性或 Align / Positioned 子组件来控制子组件在 Stack 内部的对齐和定位</note>

| 属性          | 解释                                                         | 默认值                          |
| ------------- | ------------------------------------------------------------ | ------------------------------- |
| alignment     | [`AlignmentGeometry`](layout.md#alignmentgeometry)对齐方式   | `AlignmentDirectional.topStar`t |
| textDirection | 表示水平方向子组件的布局顺序(是从左往右还是从右往左) `TextDirection.rtl`：从右到左 `TextDirection.ltr`：从左到右 |                                 |
| fit           | 填充方式 `StackFit.loose`：Stack 的大小将由其最大的非定位子部件（即没有包裹在 Align / Positioned 中的子部件）决定`StackFit.expand`：伸以填满 Stack 的整个区域`StackFit.passthrough`：不改变其原始尺寸 | `StackFit.loose`                |
| clipBehavior  | 裁剪行为：<br/>`Clip.none`：不裁剪<br/>`Clip.hardEdge`：裁剪但是不应用抗锯齿<br/>`Clip.antiAlias`：裁剪而且抗锯齿<br/>`Clip.antiAliasWithSaveLayer`：图层抗锯齿 | `Clip.hardEdge`                 |

### AlignmentGeometry

`AlignmentGeometry`是一个用于表示偏移位置的抽象类，它的具体实现类 `Alignment` 和 `AlignmentDirectional` 分别用于不同的场景

### Alignment

Alignment 用于表示与文本方向无关的偏移位置，表示矩形内的一个点，以矩形的中心为原点。它定义了一个坐标系，其中水平方向的范围是从 -1.0 到 1.0，垂直方向的范围也是从 -1.0 到 1.0。这个坐标系的中心点是 `Alignment(0.0, 0.0)`，表示矩形的中心

![](layout-2.png)

### FractionalOffset

FractionalOffset原点是左上角

<warning>不建议使用</warning>

##### AlignmentDirectional

AlignmentDirectional以文本方向为坐标

```dart
Stack(
    alignment: const Alignment(0.6, 0.6),
    children: [
      const CircleAvatar(
        backgroundImage: AssetImage('images/pic.jpg'),
        radius: 100,
      ),
      Container(
        decoration: const BoxDecoration(
          color: Colors.black45,
        ),
        child: const Text(
          'Mia B',
          style: TextStyle(
            fontSize: 20,
            fontWeight: FontWeight.bold,
            color: Colors.white,
          ),
        ),
      ),
    ],
  );
```



### Positioned

定位组件,`Positioned`可以指定`left`，`top`，`right`，`bottom`，`width`，`height` 以确定位置

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



### Align

对齐组件

| 属性          | 解释                                                         |
| ------------- | ------------------------------------------------------------ |
| alignment     | [`AlignmentGeometry`](layout.md#alignmentgeometry)对齐方式   |
| textDirection | 表示水平方向子组件的布局顺序(是从左往右还是从右往左)         |
| widthFactor   | Align组件宽度，默认为空，表示全占满，如果有值，组件宽度=子组件宽度 * widthFactor |
| heightFactor  | Align组件高度，默认为空，表示全占满，如果有值，组件高度=子组件高度 * heightFactor |

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



### OverflowBox

允许子组件溢出父组件

| 属性      | 解释                                                       | 默认值             |
| --------- | ---------------------------------------------------------- | ------------------ |
| alignment | [`AlignmentGeometry`](layout.md#alignmentgeometry)对齐方式 | `Alignment.center` |
| minWidth  | 最小宽度                                                   |                    |
| maxWidth  | 最大宽度                                                   |                    |
| minHeight | 最小高度                                                   |                    |
| maxHeight | 最大高度                                                   |                    |

```dart
Container(
                  width: 100,
                  height: 100,
                  color: Colors.teal,
                  child:  const OverflowBox(
                    maxWidth: 200,
                    maxHeight: 200,
                    child: FlutterLogo(size: 200),
                  ),
                )
```



## 响应式布局

### LayoutBuilder

LayoutBuilder 允许根据父组件的尺寸来动态构建界面。在构建方法中，LayoutBuilder 提供了一个[`BoxConstraints`](layout.md#boxconstraints)对象，其中有父组件的尺寸信息

```dart
LayoutBuilder(
          builder: (context, constraints) {
            if (constraints.maxWidth > 200) {
              return Container(
                  height: 100, width: 100, color: Colors.deepOrange);
            } else {
              return Container(height: 50, width: 50, color: Colors.pinkAccent);
            }
          },
        )
```