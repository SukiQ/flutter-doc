# 脚手架

`Scaffold` 是一个用于创建应用基本结构的布局组件，它提供了一个框架，用于放置各种常见的 UI 组件

| 属性                       | 描述                                                         |
| -------------------------- | ------------------------------------------------------------ |
| `appBar`                   | 显示页面顶部的应用栏，通常是一个 `AppBar` 小部件             |
| `body`                     | 页面主体部分，用于显示主内容                                 |
| `drawer`                   | 用于显示侧边菜单。通常是一个 `Drawer` 小部件，可以通过滑动或点击按钮打开 |
| `endDrawer`                | 显示右侧的侧边菜单，通常是一个 `Drawer` 小部件               |
| `bottomNavigationBar`      | 页面底部的导航栏，通常是一个 `BottomNavigationBar` 小部件    |
| `floatingActionButton`     | 显示浮动操作按钮（FAB），通常是一个圆形按钮，放置在页面右下角 |
| `bottomSheet`              | 页面底部的抽屉式面板                                         |
| `backgroundColor`          | 设置 `Scaffold` 背景颜色。默认情况下，`Scaffold` 背景颜色为白色 |
| `resizeToAvoidBottomInset` | 控制页面是否自动调整，避免软键盘弹出时遮挡输入框。默认为 `true` |
| `extendBody`               | 是否扩展 `body` 区域，使其延伸至底部。默认为 `false`         |
| `extendBodyBehindAppBar`   | 是否让 `body` 区域的内容显示在 `AppBar` 后面。默认为 `false` |
| `persistentFooterButtons`  | 页面底部的常驻按钮列表                                       |
| `primary`                  | 如果为 `true`，`Scaffold` 会根据 `ThemeData` 的设置来显示 `AppBar`。默认值为 `true` |
| `appBarTheme`              | 用于自定义 `AppBar` 的主题样式                               |
| `drawerEdgeDragWidth`      | 控制侧边菜单可被拖动的宽度，默认为 20.0                      |
| `key`                      | 用于标识 `Scaffold` 的唯一键                                 |

- **`appBar`**

用于设置页面的顶部应用栏，例如 `AppBar`

- **`body`**

页面主体部分，用于显示主内容。可以是任何类型的 Widget，例如 `Text`、`ListView`、`Column` 等

```dart
body: Center(
  child: Text('这是主体内容'),
),
```

- **`drawer`**

用于显示侧边菜单（即抽屉菜单）。这是一个常见的导航方式，可以通过滑动或者点击按钮打开
```dart
drawer: Drawer(
  child: ListView(
    children: <Widget>[
      ListTile(title: Text('菜单项 1')),
      ListTile(title: Text('菜单项 2')),
    ],
  ),
),
```

- **`bottomNavigationBar`**

用于显示页面底部的导航栏，通常是一个 `BottomNavigationBar`。它可以包含多个按钮，帮助用户在页面之间切换

```dart
bottomNavigationBar: BottomNavigationBar(
  items: [
    BottomNavigationBarItem(icon: Icon(Icons.home), label: '首页'),
    BottomNavigationBarItem(icon: Icon(Icons.search), label: '搜索'),
  ],
),
```

- **`floatingActionButton`**

用于显示浮动的操作按钮（FAB），通常是一个圆形按钮，放置在页面右下角。可以用来执行页面的主要操作（例如添加、创建等）。

```dart
floatingActionButton: FloatingActionButton(
  onPressed: () {},
  child: Icon(Icons.add),
),
```

- **`bottomSheet`**

设置页面底部的抽屉式面板（可以滑动出现的内容）。可以是 `PersistentBottomSheet` 或 `ModalBottomSheet`

```dart
bottomSheet: Container(
  color: Colors.green,
  height: 200.0,
  child: Center(child: Text('底部面板内容')),
),
```

- **`backgroundColor`**

设置 `Scaffold` 背景颜色。默认情况下，`Scaffold` 背景颜色为白色

```dart
backgroundColor: Colors.blue[50],
```

- **`resizeToAvoidBottomInset`**

一个布尔值，用来控制是否自动调整界面，当软键盘弹出时避免遮挡输入框。默认为 `true`。

```dart
resizeToAvoidBottomInset: false,
```

- **`endDrawer`**

这是一个额外的侧边菜单，与 `drawer` 类似，但它出现在屏幕的右侧

```dart
endDrawer: Drawer(
  child: ListView(
    children: <Widget>[
      ListTile(title: Text('右侧菜单项')),
    ],
  ),
),
```



## AppBar

`AppBar` 是一个非常常用的顶部应用栏组件，通常用于展示应用的标题、图标、操作按钮等内容。它可以包含多个元素，如标题（`title`）、操作按钮（`actions`）、图标按钮（`leading`）、底部边框、背景颜色等等

```dart
AppBar(
  title: Text('My Transparent AppBar'),
  backgroundColor: Colors.transparent,
  elevation: 0
)
```

| 属性                        | 说明                                                         |
| --------------------------- | ------------------------------------------------------------ |
| `title`                     | 设置 AppBar 的标题，通常是 `Text` widget                     |
| `leading`                   | 可选，通常是一个菜单按钮或返回按钮                           |
| `actions`                   | 可选，包含多个操作按钮的列表，通常是图标按钮                 |
| `backgroundColor`           | 设置 AppBar 的背景颜色                                       |
| `elevation`                 | 设置 AppBar 的阴影高度，默认值为 4.0                         |
| `automaticallyImplyLeading` | 是否自动显示 `leading` 按钮，默认为 `true`                   |
| `centerTitle`               | 设置标题是否居中，iOS 默认为 `true`，Android 默认为 `false`  |
| `bottom`                    | 可选，设置 AppBar 的底部组件，通常用于添加 TabBar            |
| `toolbarOpacity`            | 设置工具栏的透明度，范围从 0.0（完全透明）到 1.0（完全不透明） |
| `flexibleSpace`             | 可选，允许你在 AppBar 上放置一个自定义的 widget（通常用于显示背景图像） |
| `titleSpacing`              | 设置标题左右的间距                                           |
| `primary`                   | 是否是主要的应用栏，影响返回按钮等行为。默认值为 `true`      |
| `scrolledUnder`             | 是否在滑动时让 AppBar 隐藏，默认为 `false`                   |
