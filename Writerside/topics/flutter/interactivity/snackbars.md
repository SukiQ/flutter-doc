# 弹出



## 消息条

`SnackBar` 通常用于向用户提供操作反馈或提示信息。`SnackBar` 通常出现在屏幕底部，并在一段时间后自动消失，或者用户可以通过滑动将其关闭

| 属性              | 说明                                                         |
| :---------------- | :----------------------------------------------------------- |
| `content`         | **必需属性**，设置 SnackBar 的内容，通常是一个 `Text` 组件   |
| `duration`        | 设置 SnackBar 显示的时长，默认是 4 秒                        |
| `action`          | 可选属性，用于添加一个操作按钮（如“关闭”或“撤销”）           |
| `backgroundColor` | 设置 SnackBar 的背景颜色                                     |
| `behavior`        | 控制 SnackBar 的显示行为，可选值：`fixed`（默认）或 `floating` |
| `shape`           | 设置 SnackBar 的形状，例如圆角矩形                           |
| `elevation`       | 设置 SnackBar 的阴影高度                                     |
| `width`           | 设置 SnackBar 的宽度（仅在 `behavior: SnackBarBehavior.floating` 时有效） |
| `padding`         | 设置 SnackBar 内容的内边距                                   |
| `margin`          | 设置 SnackBar 的外边距（仅在 `behavior: SnackBarBehavior.floating` 时有效） |
| `animation`       | 设置 SnackBar 的显示和隐藏动画                               |
| `onVisible`       | 当 SnackBar 完全显示时触发的回调函数                         |

```dart
  onPressed: () {
          final snackBar = SnackBar(
            content: const Text('Yay! A SnackBar!'),
            action: SnackBarAction(
              label: 'Undo',
              onPressed: () {
                // Some code to undo the change.
              },
            ),
          );

          // Find the ScaffoldMessenger in the widget tree
          // and use it to show a SnackBar.
          ScaffoldMessenger.of(context).showSnackBar(snackBar);
        },
```



## 弹出框

`AlertDialog` 是一个常用的弹出框，通常用于显示提示信息或确认操作

| 属性                       | 说明                                                         |
| :------------------------- | :----------------------------------------------------------- |
| `title`                    | 设置对话框的标题，通常是一个 `Text` 组件                     |
| `titlePadding`             | 设置标题的内边距                                             |
| `titleTextStyle`           | 设置标题的文本样式                                           |
| `content`                  | 设置对话框的内容，可以是文本、输入框或其他组件               |
| `contentPadding`           | 设置内容的内边距                                             |
| `contentTextStyle`         | 设置内容的文本样式                                           |
| `actions`                  | 设置对话框的操作按钮，通常是 `TextButton` 或 `ElevatedButton` |
| `actionsAlignment`         | 设置操作按钮的对齐方式，默认是 `MainAxisAlignment.end`（右对齐） |
| `actionsOverflowAlignment` | 当操作按钮超出空间时的对齐方式                               |
| `actionsPadding`           | 设置操作按钮的内边距                                         |
| `backgroundColor`          | 设置对话框的背景颜色                                         |
| `elevation`                | 设置对话框的阴影高度                                         |
| `semanticLabel`            | 设置对话框的语义标签（用于无障碍功能）                       |
| `shape`                    | 设置对话框的形状，例如圆角矩形                               |
| `clipBehavior`             | 设置内容的裁剪行为，例如 `Clip.antiAlias`                    |
| `scrollable`               | 设置内容是否可滚动，默认是 `false`                           |
| `icon`                     | 设置对话框的图标，通常是一个 `Icon` 组件                     |
| `iconPadding`              | 设置图标的内边距                                             |
| `iconColor`                | 设置图标的颜色                                               |

```dart
AlertDialog(
                    title: Text('提示'),
                    content: Text('这是一个简单的 AlertDialog'),
                    actions: <Widget>[
                      TextButton(
                        child: Text('关闭'),
                        onPressed: () {
                          Navigator.of(context).pop();
                        },
                      ),
                    ],
                  )
```

<warning>弹出框需要设置Localizations</warning>

```dart
class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      localizationsDelegates: [
        GlobalMaterialLocalizations.delegate, // 提供 Material 组件的本地化支持
        GlobalWidgetsLocalizations.delegate,  // 提供默认的文本方向支持
        GlobalCupertinoLocalizations.delegate, // 提供 Cupertino 组件的本地化支持
      ],
      supportedLocales: [
        const Locale('en', 'US'), // 支持的语言环境
        const Locale('zh', 'CN'),
      ],
      home: MyHomePage(),
    );
  }
}
```

