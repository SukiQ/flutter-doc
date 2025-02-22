# 文字



## Text

`Text` 是用来显示一段文本的最基本的组件。它能够渲染静态文本、富文本，并且支持多种样式、对齐方式、颜色等设置

| 属性名               | 描述                                              |
| :------------------- | :------------------------------------------------ |
| `data`               | 要显示的文本内容                                  |
| `style`              | 文本的样式，包括字体、颜色、大小等                |
| `textAlign`          | 文本的对齐方式，如左对齐、右对齐、居中等          |
| `textDirection`      | 文本的方向，如从左到右 (`ltr`) 或从右到左 (`rtl`) |
| `overflow`           | 文本溢出时的处理方式，如截断、省略号等            |
| `maxLines`           | 文本的最大行数                                    |
| `textScaleFactor`    | 文本的缩放比例                                    |
| `semanticsLabel`     | 用于无障碍功能的语义标签                          |
| `softWrap`           | 是否允许文本换行                                  |
| `strutStyle`         | 用于控制文本的行高和基线                          |
| `textWidthBasis`     | 控制文本宽度的计算方式                            |
| `locale`             | 用于选择特定区域设置的字体或文本格式              |
| `selectionColor`     | 文本被选中时的背景颜色                            |
| `key`                | 用于控制小部件的唯一标识符                        |
| `textHeightBehavior` | 控制文本高度的行为，如是否包含首行或尾行的间距    |

- **`style`**

用于设置文本的样式，可以包括字体大小、颜色、字体加粗等。

  ```dart
  Text(
    'Hello, Flutter!',
    style: TextStyle(
      fontSize: 20,
      color: Colors.blue,
      fontWeight: FontWeight.bold,
    ),
  )
  ```

- **`textAlign`**

设置文本的对齐方式，常用值包括 `TextAlign.left` , `TextAlign.center` , `TextAlign.right` , `TextAlign.justify`

  ```dart
  Text(
    'Hello, Flutter!',
    textAlign: TextAlign.center,
  )
  ```

- **`overflow`**

设置文本溢出时的处理方式，常用值包括 `TextOverflow.clip` , `TextOverflow.ellipsis` , `TextOverflow.fade`

  ```dart
  Text(
    'This is a long text that might overflow',
    overflow: TextOverflow.ellipsis,
  )
  ```

- **`maxLines`**
  

限制文本显示的最大行数。

  ```dart
  Text(
    'This is a long text that might overflow',
    maxLines: 2,
  )
  ```



## TextStyle

`TextStyle` 是用于定义文本样式的类，控制文本的外观

| 属性                  | 描述                                       |
| --------------------- | ------------------------------------------ |
| `backgroundColor`     | 文本背景颜色                               |
| `color`               | 文本颜色                                   |
| `fontSize`            | 字体大小                                   |
| `fontWeight`          | 字体粗细（如 `FontWeight.bold`）           |
| `fontStyle`           | 字体样式（如 `FontStyle.italic`）          |
| `letterSpacing`       | 字符间距                                   |
| `wordSpacing`         | 单词间距                                   |
| `textBaseline`        | 文本基线（如 `TextBaseline.alphabetic`）   |
| `height`              | 文本行高（与字体大小的倍数关系）           |
| `locale`              | 用于选择区域特定字形的语言环境             |
| `foreground`          | 文本前景画笔（可以用于渐变等效果）         |
| `background`          | 文本背景画笔                               |
| `shadows`             | 文本阴影列表                               |
| `fontFeatures`        | 字体特性列表（如连字、替代字形等）         |
| `decoration`          | 文本装饰（如下划线、删除线等）             |
| `decorationColor`     | 文本装饰颜色                               |
| `decorationStyle`     | 文本装饰样式（如虚线、点线等）             |
| `decorationThickness` | 文本装饰线条的粗细                         |
| `debugLabel`          | 调试标签（仅在调试模式下使用）             |
| `fontFamily`          | 字体家族名称（如 `'Roboto'`）              |
| `fontFamilyFallback`  | 字体家族回退列表（当首选字体不可用时使用） |
| `package`             | 字体资源所在的包名（用于从包中加载字体）   |

```dart
Text(
  'Hello Flutter',
  style: TextStyle(
    color: Colors.blue,
    fontSize: 24.0,
    fontWeight: FontWeight.bold,
    fontFamily: 'Roboto',
    letterSpacing: 1.5,
    decoration: TextDecoration.underline,
    decorationColor: Colors.red,
    backgroundColor: Colors.yellow.withOpacity(0.3),
  ),
),
```



## RichText

`RichText` 允许你创建具有不同样式、颜色和字体的复杂文本布局

| 属性              | 描述                                                         |
| ----------------- | ------------------------------------------------------------ |
| `text`            | 必填，定义要显示的文本及其样式                               |
| `textAlign`       | 文本对齐方式，默认为 `TextAlign.start`                       |
| `textDirection`   | 文本方向，通常需要指定为 `TextDirection.ltr` 或 `TextDirection.rtl` |
| `softWrap`        | 是否自动换行，默认为 `true`                                  |
| `overflow`        | 当文本超出容器时的处理方式，默认为 `TextOverflow.clip`       |
| `textScaleFactor` | 文本缩放因子，默认为 `1.0`                                   |

```dart
RichText(
  text: TextSpan(
    style: TextStyle(fontSize: 20, color: Colors.black),
    children: <TextSpan>[
      TextSpan(text: 'Hello ', style: TextStyle(fontWeight: FontWeight.bold)),
      TextSpan(text: 'World', style: TextStyle(color: Colors.blue)),
    ],
  ),
)

```



## TextSpan



