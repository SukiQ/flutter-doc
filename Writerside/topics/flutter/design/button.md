# 按钮



| 属性               | 说明                                                        |
| :----------------- | :---------------------------------------------------------- |
| `onPressed`        | 按钮点击时触发的回调函数。如果为 `null`，按钮将处于禁用状态 |
| `onLongPress`      | 长按按钮时触发的回调函数                                    |
| `style`            | 自定义按钮的外观，包括背景颜色、文字颜色、边框、内边距等    |
| `focusNode`        | 用于控制按钮的焦点                                          |
| `autofocus`        | 是否自动获取焦点，默认为 `false`                            |
| `clipBehavior`     | 定义如何裁剪按钮的内容，默认为 `Clip.none`                  |
| `statesController` | 用于控制按钮的状态（如按下、禁用等）                        |



## ButtonStyle

| 属性                | 说明                                                |
| :------------------ | :-------------------------------------------------- |
| `textStyle`         | 按钮文字的样式（如字体大小、粗细等）                |
| `backgroundColor`   | 按钮的背景颜色                                      |
| `foregroundColor`   | 按钮的前景颜色（通常是文字或图标的颜色）            |
| `overlayColor`      | 按钮按下或悬停时的覆盖颜色                          |
| `shadowColor`       | 按钮的阴影颜色                                      |
| `elevation`         | 按钮的阴影高度                                      |
| `padding`           | 按钮的内边距                                        |
| `minimumSize`       | 按钮的最小尺寸                                      |
| `fixedSize`         | 按钮的固定尺寸                                      |
| `maximumSize`       | 按钮的最大尺寸                                      |
| `side`              | 按钮的边框样式                                      |
| `shape`             | 按钮的形状（如圆角矩形、圆形等）                    |
| `mouseCursor`       | 鼠标悬停时的光标样式                                |
| `visualDensity`     | 按钮的视觉密度（影响按钮的大小和间距）              |
| `tapTargetSize`     | 按钮的可点击区域大小                                |
| `animationDuration` | 按钮状态变化时的动画持续时间                        |
| `enableFeedback`    | 是否启用点击反馈（如点击声音或震动），默认为 `true` |
| `alignment`         | 按钮内容的对齐方式                                  |
| `splashFactory`     | 按钮点击时的水波纹效果工厂类                        |



## ElevatedButton

用于主要操作，具有阴影效果。

```dart
ElevatedButton(
  onPressed: () {
    print('ElevatedButton pressed');
  },
  child: Text('Elevated Button'),
);
```



## TextButton

用于次要操作，没有阴影和背景色

```dart
TextButton(
  onPressed: () {
    print('TextButton pressed');
  },
  child: Text('Text Button'),
);
```



## OutlinedButton

用于中等重要的操作，带有边框。

```
OutlinedButton(
  onPressed: () {
    print('OutlinedButton pressed');
  },
  child: Text('Outlined Button'),
);
```



## IconButton

用于工具栏、对话框等场景，仅显示图标。

```dart
IconButton(
  onPressed: () {
    print('IconButton pressed');
  },
  icon: Icon(Icons.favorite),
);
```



## FloatingActionButton

用于主要的突出操作，通常悬浮在界面之上。

```dart
FloatingActionButton(
  onPressed: () {
    print('FloatingActionButton pressed');
  },
  child: Icon(Icons.add),
);
```



