# Material组件



## MaterialApp

`MaterialApp` 用于构建遵循 Material Design 规范的应用程序界面。它是应用的根组件，通常用来包裹整个应用，并且它负责设置一些全局的属性，比如主题、路由、语言本地化等

```dart
MaterialApp(
  home: Scaffold(
    appBar: AppBar(
      title: const Text('Home'),
    ),
  ),
  debugShowCheckedModeBanner: false,
)
```

| 属性名称                        | 说明                                                   |
| ------------------------------- | ------------------------------------------------------ |
| `title`                         | 应用的标题，通常用于系统任务管理器中显示               |
| `theme`                         | 设置应用的主题，定义颜色、字体等样式                   |
| `home`                          | 应用的首页，用户打开应用时看到的第一个页面             |
| `initialRoute`                  | 默认的初始路由                                         |
| `routes`                        | 路由表，键为路由名称，值为构建页面的回调函数           |
| `onGenerateRoute`               | 自定义路由生成逻辑，提供更复杂的路由处理               |
| `onUnknownRoute`                | 当无法根据路由表找到匹配的路由时调用，用于处理未知路由 |
| `navigatorKey`                  | 控制 `Navigator` 的 `GlobalKey`，允许直接操作导航      |
| `builder`                       | 自定义应用构建方式，可以用于包装应用内容               |
| `onGenerateTitle`               | 动态生成应用标题，常用于本地化                         |
| `locale`                        | 设置应用当前语言环境                                   |
| `localizationsDelegates`        | 本地化支持，用于支持多语言                             |
| `supportedLocales`              | 应用支持的语言和地区列表                               |
| `debugShowCheckedModeBanner`    | 是否显示调试模式下的 `DEBUG` 标签                      |
| `showPerformanceOverlay`        | 是否显示 Flutter 性能检测面板                          |
| `showSemanticsDebugger`         | 是否启用语义调试器，适用于无障碍开发                   |
| `checkerboardRasterCacheImages` | 是否启用栅格缓存图像的检查板，通常用于调试             |
| `checkerboardOffscreenLayers`   | 是否启用离屏层的检查板，通常用于调试                   |
| `restorationScopeId`            | 应用恢复的 ID，支持应用状态恢复                        |
| `color`                         | 设置应用的背景颜色                                     |
| `useInheritedMediaQuery`        | 是否启用继承自 `MediaQuery` 的布局信息                 |
| `themeMode`                     | 设置应用的主题模式（暗黑模式、亮色模式、系统默认）     |
| `onGenerateAppTheme`            | 动态生成应用主题，适用于多种情境下动态变化的主题       |

- **`theme`**

用于设置应用的主题。`ThemeData` 定义了应用的颜色、字体、按钮样式等

| 属性名称                    | 说明                                                         |
| --------------------------- | ------------------------------------------------------------ |
| `primaryColor`              | 主要颜色，通常用于导航栏、按钮等主要UI元素                   |
| `primarySwatch`             | 主色调的颜色集，Flutter 自动生成不同深浅的颜色               |
| `accentColor`               | 强调颜色，用于突出显示按钮、选项等可交互元素（推荐使用 `colorScheme` 替代） |
| `backgroundColor`           | 背景颜色，通常用于 `Scaffold` 的背景                         |
| `textTheme`                 | 应用的文本样式（如标题、正文、按钮文本等）                   |
| `headline1, headline2, ...` | 定义不同级别的标题样式                                       |
| `bodyText1, bodyText2`      | 定义正文文本样式                                             |
| `buttonTheme`               | 配置按钮样式                                                 |
| `iconTheme`                 | 配置图标的样式                                               |
| `scaffoldBackgroundColor`   | `Scaffold` 背景颜色                                          |
| `cardColor`                 | 卡片的背景颜色                                               |
| `colorScheme`               | 统一管理应用的色彩主题，包括主色、次色、背景色、错误色等     |
| `buttonColor`               | 设置按钮的默认颜色（`buttonTheme` 的一部分）                 |
| `disabledColor`             | 禁用控件的颜色                                               |
| `canvasColor`               | 画布颜色，通常用于 `Drawer` 背景                             |
| `shadowColor`               | 阴影颜色                                                     |
| `dividerColor`              | 分割线颜色                                                   |
| `indicatorColor`            | 选项卡指示器颜色                                             |
| `toggleableActiveColor`     | 切换按钮激活时的颜色                                         |
| `appBarTheme`               | 配置 `AppBar` 的主题样式                                     |
| `dialogTheme`               | 配置对话框的主题样式                                         |
| `cardTheme`                 | 配置卡片的主题样式                                           |
| `chipTheme`                 | 配置 Chip 的主题样式                                         |
| `platform`                  | 设置应用的目标平台。 (`TargetPlatform`，如 `android` 或 `ios`) |
| `inputDecorationTheme`      | 配置输入框样式                                               |
| `textButtonTheme`           | 配置文本按钮的样式                                           |

```dart
theme: ThemeData(
  primarySwatch: Colors.blue,
),
```

- **`routes`**

定义应用内的所有路由映射。键是路由名称，值是构建页面的回调函数

```dart
routes: {
  '/': (context) => HomePage(),
  '/second': (context) => SecondPage(),
},
```

- **`locale`**

设置应用的当前语言环境，影响文本的显示

```dart
locale: Locale('zh', 'CN'),
```

