# 可滚动



## 简单滚动



### SingleChildScrollView

`SingleChildScrollView`用来包裹一个子组件，并使其支持滚动

<warning>SingleChildScrollView不支持基于 Sliver 的延迟加载模型，所以如果预计视口可能包含超出屏幕尺寸太多的内容时，那么使用SingleChildScrollView将会非常昂贵</warning>

| 属性                      | 说明                                                |
| ------------------------- | --------------------------------------------------- |
| `scrollDirection`         | 滚动方向                                            |
| `reverse`                 | 是否反转                                            |
| `padding`                 | 外边距                                              |
| `primary`                 | 是否使用 widget 树中默认的`PrimaryScrollController` |
| `physics`                 | 滚动类型                                            |
| `controller`              | 控制组件                                            |
| `dragStartBehavior`       | 确定处理拖动开始行为的方式                          |
| `clipBehavior`            | 内容将被裁剪（或不裁剪）                            |
| `restorationId`           | 保持滑动的偏移量                                    |
| `keyboardDismissBehavior` | 键盘关闭行为                                        |

```dart
SingleChildScrollView(
            scrollDirection: Axis.vertical,
            padding: EdgeInsets.all(10),
            child: Column(
            children: List.generate(50, (index) {
              return Container(
                alignment: Alignment.center,
                height: 80,
                child: Text("$index"),
                color: Colors.primaries[index % Colors.primaries.length],
              );
            }).toList(),
          ),
        )
```



## 无限滚动



### ListView

`ListView`可以用来显示大量数据，支持垂直和水平滚动。`ListView` 提供了几种构造方法来满足不同的需求

-  `ListView.builder`

当有大量数据，或者数据是动态生成时，`ListView.builder`会构建当前可见区域内的项，避免了不必要的内存消耗

```dart
ListView.builder(
  itemCount: 100, // 项目数量
  itemBuilder: (context, index) {
    return ListTile(
      title: Text('Item $index'),
    );
  },
)
```

- `ListView.separated`

使用 `ListView.separated`允许提供分隔符构建函数

```dart
ListView.separated(
  itemCount: 100,
  itemBuilder: (context, index) {
    return ListTile(
      title: Text('Item $index'),
    );
  },
  separatorBuilder: (context, index) {
    return Divider(); // 分隔符
  },
)
```

- `ListView.custom`

`ListView.custom` 提供了完全的控制权，可以定制更多的属性

```dart
ListView.custom(
  childrenDelegate: SliverChildBuilderDelegate(
    (context, index) {
      return ListTile(
        title: Text('Item $index'),
      );
    },
    childCount: 100,
  ),
)
```

- ListView.horizontal

`ListView` 默认是垂直滚动的，如果需要实现水平滚动，可以通过设置 `scrollDirection` 属性来改变方向

```dart
ListView.builder(
  scrollDirection: Axis.horizontal,
  itemCount: 10,
  itemBuilder: (context, index) {
    return Container(
      width: 100,
      color: Colors.blue,
      child: Center(child: Text('Item $index')),
    );
  },
)
```

| 属性                      | 说明                                                         |
| ------------------------- | ------------------------------------------------------------ |
| `scrollDirection`         | 滚动方向<br/>`Axis.horizontal`水平方向<br/>`Axis.vertical`垂直方向 |
| `reverse`                 | 组件反向排序                                                 |
| `controller`              | 滚动监听                                                     |
| `primary`                 | 内容不足时是否可以尝试滑动                                   |
| `physics`                 | 滑动类型                                                     |
| `shrinkWrap`              | scrollDirection中滚动视图的范围是否应由正在查看的内容确定    |
| `padding`                 | 外边距                                                       |
| `itemExtent`              | 不为空则强制子级在滚动方向上具有给定范围，指定itemExtend能优化性能 |
| `prototypeItem`           | 为所有子Widget设置一个原型，方便计算高度                     |
| `addAutomaticKeepAlives`  | 是否将每个子Widget都包装在AutomaticKeepAlive组件中           |
| `addRepaintBoundaries`    | 是否将每个子Widget都包装在RepaintBoundary组件中              |
| `addSemanticIndexes`      | 是否将每个子Widget都包装在IndexedSemantics组件中             |
| `cacheExtent`             | 用于设置不可见的缓存区域的大小，合理的设置该值可以有效优化效率 |
| `semanticChildCount`      | 为ListView中的子列表中Widget提供语义信息的数量               |
| `dragStartBehavior`       | 确定处理拖动开始行为的方式                                   |
| `keyboardDismissBehavior` | 键盘关闭行为                                                 |
| `restorationId`           | 保持滑动的偏移量                                             |
| `clipBehavior`            | 内容将被裁剪（或不裁剪）                                     |

```dart
ListView(
  // This next line does the trick.
  scrollDirection: Axis.horizontal,
  children: <Widget>[
    Container(
      width: 160,
      color: Colors.red,
    ),
    Container(
      width: 160,
      color: Colors.blue,
    ),
    Container(
      width: 160,
      color: Colors.green,
    ),
    Container(
      width: 160,
      color: Colors.yellow,
    ),
    Container(
      width: 160,
      color: Colors.orange,
    ),
  ],
),
```





### GridView

`GridView`会把子项排列成多行多列。`GridView` 在显示大量相同类型的数据时非常有用，尤其是在需要网格布局的场景（例如照片库、商品展示等）

-  `GridView.builder`

`GridView.builder`只有在需要时才会构建可视区域内的项目，从而提高性能

```dart
GridView.builder(
  gridDelegate: SliverGridDelegateWithFixedCrossAxisCount(
    crossAxisCount: 2, // 每行显示两个子项
  ),
  itemCount: 20, // 数据的数量
  itemBuilder: (context, index) {
    return Card(
      child: Center(child: Text('Item $index')),
    );
  },
)
```

- `GridView.count`

`GridView.count` 是一种快捷方式，适用于知道每行显示多少个子项的情况。效果和 `SliverGridDelegateWithFixedCrossAxisCount` 类似

```dart
GridView.count(
  crossAxisCount: 3, // 每行显示3个子项
  children: List.generate(20, (index) {
    return Card(
      child: Center(child: Text('Item $index')),
    );
  }),
)
```

- `GridView.extent`

`GridView.extent` 允许你根据每个子项的最大宽度来动态计算列数，而不是直接指定列数。适用于子项宽度不同的场景

```dart
GridView.extent(
  maxCrossAxisExtent: 150, // 每个子项的最大宽度
  children: List.generate(20, (index) {
    return Card(
      child: Center(child: Text('Item $index')),
    );
  }),
)
```

- `GridView.custom`

`GridView.custom` 提供了更多的灵活性，从而实现更高的定制性

```dart
GridView.custom(
  gridDelegate: SliverGridDelegateWithFixedCrossAxisCount(
    crossAxisCount: 3,
  ),
  childrenDelegate: SliverChildBuilderDelegate(
    (context, index) {
      return Card(
        child: Center(child: Text('Item $index')),
      );
    },
    childCount: 20, // 数据的数量
  ),
 )
```

| 属性                     | 说明                                               |
| ------------------------ | -------------------------------------------------- |
| `scrollDirection`        | 滚动方向                                           |
| `reverse`                | 组件反向排序                                       |
| `controller`             | 滚动监听                                           |
| `primary`                | 内容不足时是否可以尝试滑动                         |
| `physics`                | 滑动类型                                           |
| `crossAxisCount`         | 主轴一行的数量                                     |
| `mainAxisSpacing`        | 行间距                                             |
| `crossAxisSpacing`       | 列间距                                             |
| `childAspectRatio`       | 元素宽高比                                         |
| `addAutomaticKeepAlives` | 是否将每个子Widget都包装在AutomaticKeepAlive组件中 |
| `addRepaintBoundaries`   | 是否将每个子Widget都包装在RepaintBoundary组件中    |
| `addSemanticIndexes`     | 是否将每个子Widget都包装在IndexedSemantics组件中   |
| `cacheExtent`            | 用于设置不可见的缓存区域的大小                     |
| `semanticChildCount`     | 为GridView中的子列表中Widget提供语义信息的数量     |
| `dragStartBehavior`      | 确定处理拖动开始行为的方式                         |
| `keyboardDismissBehavior`| 键盘关闭行为                                       |
| `restorationId`          | 保持滑动的偏移量                                   |
| `clipBehavior`           | 内容将被裁剪（或不裁剪）                           |

```dart
GridView.count(
            crossAxisCount: 4,
            mainAxisSpacing: 50,
            crossAxisSpacing: 20,
            childAspectRatio: 1 / 0.5,
            children: [
              Container(color: Colors.orange,),
              Container(color: Colors.red,),
              Container(color: Colors.cyan,),
              Container(color: Colors.purple,),
              Container(color: Colors.blue,),
              Container(color: Colors.lime,)
            ],
          )
```



## 自定义滚动



### CustomScrollView

`CustomScrollView` 允许你创建一个可滚动的视图，并且能够灵活地**组合**多种类型的滚动组件，如 `Sliver` 组件它适用于那些需要更高自定义滚动行为的场景

| 属性                      | 说明                                                         |
| ------------------------- | ------------------------------------------------------------ |
| `scrollDirection`         | 滚动方向                                                     |
| `reverse`                 | 是否反转                                                     |
| `controller`              | 控制组件                                                     |
| `primary`                 | 是否使用 widget 树中默认的`PrimaryScrollController`          |
| `physics`                 | 滚动类型                                                     |
| `scrollBehavior`          | 滚动行为                                                     |
| `shrinkWrap`              | scrollDirection中滚动视图的范围是否应由正在查看的内容确定    |
| `center`                  | 计算基准，默认为第一个元素                                   |
| `anchor`                  | 排列位置的初始偏移量，0-1之间，0代表不便宜，1代表偏移一个视窗 |
| `cacheExtent`             | 用于设置不可见的缓存区域的大小，合理的设置该值可以有效优化效率 |
| `slivers`                 | 自定义Sliver                                                 |
| `semanticChildCount`      | 设置子视窗的个数                                             |
| `dragStartBehavior`       | 确定处理拖动开始行为的方式                                   |
| `keyboardDismissBehavior` | 键盘关闭行为                                                 |
| `restorationId`           | 保持滑动的偏移量                                             |
| `clipBehavior`            | 内容将被裁剪（或不裁剪）                                     |

```dart
CustomScrollView(
          slivers: [
            // 这里是一个 SliverAppBar
            SliverAppBar(
              expandedHeight: 200.0,
              floating: false,
              pinned: true,
              flexibleSpace: FlexibleSpaceBar(
                title: Text("CustomScrollView Example"),
                background: Image.network(
                  "https://example.com/image.jpg",
                  fit: BoxFit.cover,
                ),
              ),
            ),
            // 这里是一个 SliverList
            SliverList(
              delegate: SliverChildBuilderDelegate(
                (BuildContext context, int index) {
                  return ListTile(title: Text('Item $index'));
                },
                childCount: 50,
              ),
            ),
          ],
        ),
      )
```



### SliverAppBar

`SliverAppBar` 允许实现可伸缩、可固定的 AppBar。通常，`SliverAppBar` 与 `CustomScrollView` 配合使用，使得在滚动时能够产生类似伸缩折叠效果的交互体验

| 属性                        | 说明                                                         |
| --------------------------- | ------------------------------------------------------------ |
| `expandedHeight`            | 设置 `SliverAppBar` 展开时的最大高度                         |
| `floating`                  | 是否允许 `SliverAppBar` 在滚动时浮动。`true` 表示快速浮动，`false` 表示不浮动 |
| `pinned`                    | 是否将 `SliverAppBar` 固定在滚动视图的顶部。`true` 表示固定，`false` 表示不固定 |
| `snap`                      | 当 `floating` 设置为 `true` 时，决定是否启用“快速滑动到顶部”的效果 |
| `flexibleSpace`             | 一个可自定义的空间区域，通常用来展示背景图片、渐变等         |
| `backgroundColor`           | 设置 `SliverAppBar` 的背景颜色                               |
| `elevation`                 | 设置 `SliverAppBar` 的阴影高度                               |
| `shape`                     | 设置 `SliverAppBar` 的形状，通常用于圆角或其他自定义形状     |
| `automaticallyImplyLeading` | 设置 `SliverAppBar` 是否自动显示返回按钮                     |
| `forceElevated`             | 是否强制将 `SliverAppBar` 设置为具有 `elevation`，即使在滚动视图内容较多时 |

```dart
SliverAppBar(
  expandedHeight: 200.0,
  floating: false,
  pinned: true,
  flexibleSpace: FlexibleSpaceBar(
    title: Text("SliverAppBar Example"),
    background: Image.network(
      "https://example.com/your-image.jpg",
      fit: BoxFit.cover,
    ),
  ),
)
```



### SliverList \ SliverGrid

和 `ListView`\ `GridView`类似
