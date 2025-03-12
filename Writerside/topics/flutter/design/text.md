# 文本



## Text

`Text` 是一个用于显示简单样式文本的小部件

| 属性                 | 说明                                                         |
| :------------------- | :----------------------------------------------------------- |
| `data`               | 要显示的文本内容（必需）                                     |
| `style`              | 用于设置文本的样式（如字体大小、颜色、字重等）               |
| `textAlign`          | 文本的对齐方式（如 `TextAlign.left`, `TextAlign.center` 等） |
| `textDirection`      | 文本的方向（如 `TextDirection.ltr`, `TextDirection.rtl`）    |
| `locale`             | 用于选择字体的区域设置（如 `Locale('en', 'US')`）            |
| `softWrap`           | 是否允许文本换行（默认为 `true`）                            |
| `overflow`           | 文本溢出时的处理方式（如 `TextOverflow.ellipsis`, `TextOverflow.clip`） |
| `textScaleFactor`    | 文本的缩放比例（默认为 `1.0`）                               |
| `maxLines`           | 文本的最大行数。                                             |
| `semanticsLabel`     | 用于无障碍功能的语义标签                                     |
| `textWidthBasis`     | 文本宽度的计算方式（如 `TextWidthBasis.parent`, `TextWidthBasis.longestLine`） |
| `textHeightBehavior` | 控制文本高度的行为（如是否包含首行和末行的间距）             |
| `selectionColor`     | 文本被选中时的背景颜色                                       |
| `strutStyle`         | 用于设置文本的基线对齐方式                                   |
| `key`                | 用于控制小部件的唯一标识符                                   |

```dart
Text(
  'Hello, Flutter!', // data
  style: TextStyle(
    fontSize: 24.0,
    fontWeight: FontWeight.bold,
    color: Colors.blue,
  ), // style
  textAlign: TextAlign.center, // textAlign
  textDirection: TextDirection.ltr, // textDirection
  locale: Locale('en', 'US'), // locale
  softWrap: true, // softWrap
  overflow: TextOverflow.ellipsis, // overflow
  textScaleFactor: 1.2, // textScaleFactor
  maxLines: 2, // maxLines
  semanticsLabel: 'Greeting text', // semanticsLabel
  textWidthBasis: TextWidthBasis.longestLine, // textWidthBasis
  textHeightBehavior: TextHeightBehavior(
    applyHeightToFirstAscent: true,
    applyHeightToLastDescent: true,
  ), // textHeightBehavior
  selectionColor: Colors.yellow, // selectionColor
  strutStyle: StrutStyle(
    fontSize: 24.0,
    height: 1.5,
  ), // strutStyle
);
```



## TextTheme

`TextTheme`用于定义应用程序中文本样式的类，它包含了一系列预定义的文本样式，如标题、正文、按钮文本等，可以帮助你快速统一应用程序中的文本风格

`TextTheme`的字体类别：

- Display
- Headline
- Title
- Label
- Body

每种都有三种尺寸可供选择：

- Small
- Medium
- Large

| 属性             | 说明                                                       |
| :--------------- | :--------------------------------------------------------- |
| `displayLarge`   | 用于最大尺寸的显示文本，通常用于非常醒目的标题或大屏幕显示 |
| `displayMedium`  | 用于中等尺寸的显示文本，适用于次级的醒目标题               |
| `displaySmall`   | 用于较小尺寸的显示文本，适用于较小的醒目标题               |
| `headlineLarge`  | 用于大尺寸的标题文本，通常用于页面或部分的标题             |
| `headlineMedium` | 用于中等尺寸的标题文本，适用于次级标题                     |
| `headlineSmall`  | 用于较小尺寸的标题文本，适用于较小的标题                   |
| `titleLarge`     | 用于大尺寸的标题文本，通常用于卡片或对话框的标题           |
| `titleMedium`    | 用于中等尺寸的标题文本，适用于次级标题                     |
| `titleSmall`     | 用于较小尺寸的标题文本，适用于较小的标题                   |
| `bodyLarge`      | 用于大尺寸的正文文本，通常用于段落或主要内容               |
| `bodyMedium`     | 用于中等尺寸的正文文本，适用于普通正文内容                 |
| `bodySmall`      | 用于较小尺寸的正文文本，适用于辅助文本或注释               |
| `labelLarge`     | 用于大尺寸的标签文本，通常用于按钮或标签                   |
| `labelMedium`    | 用于中等尺寸的标签文本，适用于较小的按钮或标签             |
| `labelSmall`     | 用于较小尺寸的标签文本，适用于最小的按钮或标签             |

```dart
MaterialApp(
      theme: ThemeData(
        textTheme: TextTheme(
          displayLarge: TextStyle(fontSize: 72.0, fontWeight: FontWeight.bold),
          titleLarge: TextStyle(fontSize: 36.0, fontStyle: FontStyle.italic),
          bodyMedium: TextStyle(fontSize: 14.0, fontFamily: 'Hind'),
        ),
      )
    );
```



## GoogleFonts

`google_fonts`允许使用 Google Fonts 提供的字体

```yaml
dependencies:
  google_fonts: ^5.1.0 
```

