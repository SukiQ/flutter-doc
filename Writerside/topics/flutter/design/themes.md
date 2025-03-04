# 主题



## ThemeData

`ThemeData` 是用于定义应用程序的主题（如颜色、字体、形状等）的配置类。`ThemeData` 主要用于 `MaterialApp` 或 `Theme` 小部件，以统一管理应用的 UI 风格

| 属性                         | 说明                                                         |
| :--------------------------- | :----------------------------------------------------------- |
| `primaryColor`               | 应用程序的主色调                                             |
| `colorScheme`                | 定义一组颜色（如 primary、secondary、background 等）         |
| `accentColor`                | 次要颜色（已弃用，推荐使用 `colorScheme.secondary`）         |
| `scaffoldBackgroundColor`    | 页面背景颜色                                                 |
| `cardColor`                  | 卡片组件的背景颜色                                           |
| `textTheme`                  | 定义应用程序中所有文本的样式                                 |
| `fontFamily`                 | 设置全局字体                                                 |
| `buttonTheme`                | 按钮的样式（已弃用，推荐使用 `TextButtonTheme` 等）          |
| `appBarTheme`                | AppBar 的样式                                                |
| `inputDecorationTheme`       | 输入框的样式                                                 |
| `floatingActionButtonTheme`  | FloatingActionButton 的样式                                  |
| `brightness`                 | 应用程序的整体亮度（`Brightness.light` 或 `Brightness.dark`） |
| `useMaterial3`               | 是否启用 Material 3 设计风格（默认为 `false`）               |
| `iconTheme`                  | 图标的样式                                                   |
| `primaryTextTheme`           | 主色调文本的样式                                             |
| `accentTextTheme`            | 次要颜色文本的样式（已弃用，推荐使用 `colorScheme`）         |
| `primaryIconTheme`           | 主色调图标的样式                                             |
| `accentIconTheme`            | 次要颜色图标的样式（已弃用，推荐使用 `colorScheme`）         |
| `toggleableActiveColor`      | 可切换组件（如 Switch、Checkbox）激活时的颜色                |
| `dividerColor`               | 分割线的颜色                                                 |
| `errorColor`                 | 错误提示的颜色                                               |
| `backgroundColor`            | 背景颜色（已弃用，推荐使用 `colorScheme.background`）        |
| `dialogBackgroundColor`      | 对话框的背景颜色                                             |
| `indicatorColor`             | Tab 指示器的颜色                                             |
| `hintColor`                  | 输入框提示文字的颜色                                         |
| `highlightColor`             | 高亮颜色（如点击效果）                                       |
| `splashColor`                | 水波纹颜色                                                   |
| `selectedRowColor`           | 选中行的颜色                                                 |
| `unselectedWidgetColor`      | 未选中组件的颜色（如 Checkbox、Radio）                       |
| `disabledColor`              | 禁用状态的颜色                                               |
| `buttonColor`                | 按钮的颜色（已弃用，推荐使用 `TextButtonTheme` 等）          |
| `secondaryHeaderColor`       | 次要标题的颜色                                               |
| `textSelectionColor`         | 文本选中时的颜色                                             |
| `cursorColor`                | 输入框光标的颜色                                             |
| `textSelectionHandleColor`   | 文本选择手柄的颜色                                           |
| `canvasColor`                | 画布颜色（如 Material 组件的背景颜色）                       |
| `shadowColor`                | 阴影颜色                                                     |
| `bottomAppBarColor`          | BottomAppBar 的背景颜色                                      |
| `chipTheme`                  | Chip 组件的样式                                              |
| `platform`                   | 目标平台（如 Android、iOS）                                  |
| `materialTapTargetSize`      | Material 组件点击目标的大小                                  |
| `visualDensity`              | 组件的视觉密度（如紧凑或宽松）                               |
| `applyElevationOverlayColor` | 是否应用高度叠加颜色（用于暗色主题）                         |
| `snackBarTheme`              | SnackBar 的样式                                              |
| `dialogTheme`                | 对话框的样式                                                 |
| `typography`                 | 排版样式                                                     |
| `cupertinoOverrideTheme`     | 覆盖 Cupertino 主题的样式                                    |
| `popupMenuTheme`             | PopupMenu 的样式                                             |
| `bannerTheme`                | MaterialBanner 的样式                                        |
| `bottomSheetTheme`           | BottomSheet 的样式                                           |
| `tooltipTheme`               | Tooltip 的样式                                               |
| `timePickerTheme`            | 时间选择器的样式                                             |
| `textButtonTheme`            | TextButton 的样式                                            |
| `elevatedButtonTheme`        | ElevatedButton 的样式                                        |
| `outlinedButtonTheme`        | OutlinedButton 的样式                                        |
| `toggleButtonsTheme`         | ToggleButtons 的样式                                         |
| `progressIndicatorTheme`     | 进度指示器的样式（如 CircularProgressIndicator、LinearProgressIndicator） |
| `navigationRailTheme`        | NavigationRail 的样式                                        |
| `tabBarTheme`                | TabBar 的样式                                                |
| `dataTableTheme`             | DataTable 的样式                                             |
| `checkboxTheme`              | Checkbox 的样式                                              |
| `radioTheme`                 | Radio 的样式                                                 |
| `switchTheme`                | Switch 的样式                                                |
| `sliderTheme`                | Slider 的样式                                                |
| `drawerTheme`                | Drawer 的样式                                                |
| `listTileTheme`              | ListTile 的样式                                              |
| `expansionTileTheme`         | ExpansionTile 的样式                                         |
| `dividerTheme`               | Divider 的样式                                               |
| `cardTheme`                  | Card 的样式                                                  |
| `pageTransitionsTheme`       | 页面切换动画的样式                                           |



- **全局设置**

```dart
class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: '全局主题示例',
      theme: ThemeData(
        // 主色调
        primaryColor: Colors.blue,
        // 启用 Material 3
        useMaterial3: true,
        // 文本样式
        textTheme: TextTheme(
          headline1: TextStyle(fontSize: 32, fontWeight: FontWeight.bold),
          bodyText1: TextStyle(fontSize: 16, color: Colors.black87),
        ),
        // 按钮样式
        elevatedButtonTheme: ElevatedButtonThemeData(
          style: ElevatedButton.styleFrom(
            primary: Colors.blue,
            onPrimary: Colors.white,
            padding: EdgeInsets.symmetric(horizontal: 20, vertical: 10),
          ),
        ),
      ),
      home: MyHomePage(),
    );
  }
}
```



- **局部主题设置**

通过 `Theme` 组件为某个部分设置局部主题，它会覆盖全局主题

```dart
class MyHomePage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('局部主题示例'),
      ),
      body: Center(
        child: Theme(
          data: Theme.of(
            context
          ).copyWith(colorScheme: ColorScheme.fromSeed(seedColor: Colors.deepPurple)),
          child: const FloatingActionButton(onPressed: null, child: Icon(Icons.add)),
        ),
      ),
    );
  }
}
```

`Theme.of(context)`：获取当前主题

`copyWith()`：基于现有主题创建新主题