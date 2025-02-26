# 可滚动



## 简单滚动



### SingleChildScrollView

`SingleChildScrollView`用来包裹一个子组件，并使其支持滚动

<warning>SingleChildScrollView不支持基于 Sliver 的延迟加载模型，所以如果预计视口可能包含超出屏幕尺寸太多的内容时，那么使用SingleChildScrollView将会非常昂贵</warning>



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

