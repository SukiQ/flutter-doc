# 盒子布局



## AspectRatio

`AspectRatio` 用来根据给定的宽高比来调整子组件的大小,它确保子组件在不同屏幕尺寸下保持特定的**宽高比**

| 属性        | 说明     |
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



## ConstrainedBox

用于给其子组件添加额外的尺寸**约束**，通过设置 `constraints` 参数，可以对子组件的最小和最大宽度、最小和最大高度进行限制

| 属性        | 说明     |
| ----------- | -------- |
| constraints | 限制参数 |

```dart
ConstrainedBox(
  constraints: const BoxConstraints.expand(),
  child: const Card(child: Text('Hello World!')),
)
```



## BoxConstraints

`BoxConstraints`可以通过设置`minWidth`， `maxWidth`， `minHeight`， `maxHeight`限制子组件的大小

- BoxConstraints.expand(`width?`, `height?`)

  展开约束，如果 `width`/`height` 为空则最大/最小宽高均无限大，如果不为空最大/最小宽高均为`width`/`height` 大小

- BoxConstraints.loose(`Size`)

  松约束，最小宽高为 0，最大宽高为width/height

- BoxConstraints.tight(`Size`)

  紧约束，最小最大宽高均等为width/height

- BoxConstraints.tightFor(`width?`, `height?`)

  单侧松约束，如果`width`/`height`不为空则紧约束不为空的边，为空则松约束该边

- BoxConstraints.tightForFinite(`width?`, `height?`)

  与BoxConstraints.tightFor相同，不同的是如果设置为无限大`double.infinity` ，那么依然会松约束



## Container

`Container` 是一个非常常用的布局`Widget`，它本质上是一个盒子，允许你控制子组件的尺寸、装饰、边距、填充、对齐等属性。可以看作是一个多功能的容器，它能够将其他 Widget 包裹起来并提供额外的样式和布局控制

| 属性                 | 说明                                                         |
| -------------------- | ------------------------------------------------------------ |
| alignment            | AlignmentGeometry对齐方式                                    |
| padding              | 内边距                                                       |
| color                | 颜色                                                         |
| decoration           | 背景样式                                                     |
| foregroundDecoration | 前景样式                                                     |
| width                | 宽度                                                         |
| height               | 高度                                                         |
| constraints          | BoxConstraints约束                                           |
| margin               | 外边距                                                       |
| transform            | 变化                                                         |
| transformAlignment   | 变化时对齐方式                                               |
| clipBehavior         | 裁剪行为： <br/>`Clip.none`：不裁剪<br/>`Clip.hardEdge`：裁剪但是不应用抗锯齿<br/>`Clip.antiAlias`：裁剪而且抗锯齿<br/>`Clip.antiAliasWithSaveLayer`：图层抗锯齿 |



## SizedBox

`SizedBox`作用是创建一个具有固定尺寸的盒子，可以用来在布局中占据固定的空间。`SizedBox` 既可以作为占位符，也可以用来设置组件的固定宽度或高度

```dart
SizedBox(
  width: 100,  // 设置宽度为100
  child: Container(color: Colors.blue),
)
```



## UnconstrainedBox

`UnconstrainedBox` 用于移除父组件的约束条件，允许子组件按照自己的尺寸进行布局

```dart
 Container(
            color: Colors.blue,
            width: 300,
            height: 300,
            child: UnconstrainedBox(
              child: Container(
                width: 100,
                height: 100,
                color: Colors.red,
              ),
            ),
          )
```



## FractionallySizedBox

`FractionallySizedBox` 用于按父容器的比例来调整子组件尺寸的小部件

```dart
FractionallySizedBox(
  widthFactor: 0.5,    // 宽度占父容器的 50%
  heightFactor: 0.5,   // 高度占父容器的 50%
  child: Container(
    color: Colors.blue,
  ),
)
```



## LimitedBox

`LimitedBox`用于限制子组件的最大尺寸

```dart
LimitedBox(
  maxWidth: 200,   // 最大宽度 200
  maxHeight: 100,  // 最大高度 100
  child: Container(
    color: Colors.blue,
    width: 300,   // 宽度超出最大限制，子组件会被限制为 200
    height: 150,  // 高度超出最大限制，子组件会被限制为 100
  ),
)
```



## FittedBox

用于根据其父组件的约束条件，自动缩放和调整子组件的大小，以确保子组件适应父组件的边界

<note>FittedBox 通常用于处理文本、图片等内容的自适应缩放</note>

| 属性           | 说明                                                         |
| :------------- | :----------------------------------------------------------- |
| `fit`          | 控制子组件的缩放方式，例如保持宽高比、填充父组件等<br/>`BoxFit.contain`: 保持宽高比，确保子组件完全显示在父组件内<br/>`BoxFit.cover`: 保持宽高比，确保子组件覆盖父组件，可能会裁剪内容<br/>`BoxFit.fill`: 拉伸子组件以填充父组件，不保持宽高比<br>`BoxFit.fitWidth`: 保持宽高比，确保宽度匹配父组件<br>`BoxFit.fitHeight`: 保持宽高比，确保高度匹配父组件<br>`BoxFit.scaleDown`: 如果子组件比父组件大，则缩小子组件；否则保持原尺寸<br>`BoxFit.none`: 不进行任何缩放，子组件按原始尺寸显示 |
| `alignment`    | 控制子组件在父组件中的对齐方式                               |
| `clipBehavior` | 控制子组件超出父组件边界时的裁剪行为 <br/>`Clip.none`：不裁剪<br/>`Clip.hardEdge`：裁剪但是不应用抗锯齿<br/>`Clip.antiAlias`：裁剪而且抗锯齿<br/>`Clip.antiAliasWithSaveLayer`：图层抗锯齿 |
| `child`        | 需要缩放和调整的子组件                                       |

```dart
FittedBox(
  fit: BoxFit.contain,
  alignment: Alignment.topLeft,
  clipBehavior: Clip.antiAlias,
  child: Image.network('https://example.com/image.png'),
);
```

