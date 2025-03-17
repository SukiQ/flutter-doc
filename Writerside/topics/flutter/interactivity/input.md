# 表单输入



## TextField

`TextField` 允许用户输入单行或多行文本。它非常灵活，支持多种自定义选项，如输入验证、样式设置、键盘类型、占位符等

| 属性                         | 说明                                                 |
| :--------------------------- | :--------------------------------------------------- |
| `controller`                 | 用于控制文本输入的内容和监听输入变化                 |
| `decoration`                 | 设置输入框的装饰，如标签、提示文本、边框、图标等     |
| `onChanged`                  | 当输入内容发生变化时触发的回调函数                   |
| `onSubmitted`                | 当用户提交输入（如按下键盘的确认键）时触发的回调函数 |
| `onEditingComplete`          | 当用户完成编辑时触发的回调函数                       |
| `onTap`                      | 当用户点击输入框时触发的回调函数                     |
| `keyboardType`               | 设置键盘类型，如文本、数字、邮箱、电话等             |
| `textInputAction`            | 设置键盘上的操作按钮，如“完成”、“下一步”等           |
| `textCapitalization`         | 控制文本的大小写，如单词首字母大写、句子首字母大写等 |
| `style`                      | 设置输入文本的样式，如字体、颜色、大小等             |
| `textAlign`                  | 设置文本的对齐方式，如左对齐、居中对齐、右对齐等     |
| `maxLines`                   | 设置输入框的最大行数，默认为 `1`（单行输入）         |
| `minLines`                   | 设置输入框的最小行数                                 |
| `maxLength`                  | 设置输入文本的最大长度                               |
| `maxLengthEnforcement`       | 控制超出最大长度时的行为，如截断或禁止输入           |
| `obscureText`                | 是否隐藏输入内容（用于密码输入）                     |
| `obscuringCharacter`         | 设置隐藏文本时显示的字符，默认为 `•`                 |
| `enabled`                    | 是否启用输入框。如果为 `false`，输入框将不可用       |
| `readOnly`                   | 是否只读。如果为 `true`，用户无法编辑内容            |
| `cursorColor`                | 设置光标的颜色                                       |
| `cursorWidth`                | 设置光标的宽度                                       |
| `cursorHeight`               | 设置光标的高度                                       |
| `cursorRadius`               | 设置光标的圆角半径                                   |
| `autofocus`                  | 是否自动获取焦点                                     |
| `autocorrect`                | 是否启用自动更正                                     |
| `enableSuggestions`          | 是否启用输入建议                                     |
| `inputFormatters`            | 设置输入格式，如限制输入为数字、字母等               |
| `focusNode`                  | 用于控制输入框的焦点                                 |
| `buildCounter`               | 自定义字符计数器的显示方式                           |
| `scrollPadding`              | 设置输入框滚动时的内边距                             |
| `scrollPhysics`              | 设置输入框滚动的物理效果                             |
| `keyboardAppearance`         | 设置键盘的外观，如亮色或暗色                         |
| `enableInteractiveSelection` | 是否启用交互式文本选择（如长按选择文本）             |
| `mouseCursor`                | 设置鼠标悬停时的光标样式                             |
| `expands`                    | 是否允许输入框扩展到最大可用空间                     |
| `strutStyle`                 | 设置文本的基线对齐方式                               |
| `selectionControls`          | 自定义文本选择的控制按钮（如复制、粘贴）             |
| `smartDashesType`            | 控制智能破折号的显示方式                             |
| `smartQuotesType`            | 控制智能引号的显示方式                               |
| `toolbarOptions`             | 设置工具栏选项，如复制、粘贴、剪切等                 |

```dart
TextField(
              decoration: InputDecoration(
                hintText: "请输入内容",
                prefixIcon: Icon(Icons.search),
                suffixIcon: Icon(Icons.close),
                border: OutlineInputBorder(
                  borderRadius: BorderRadius.circular(10),
                  borderSide: BorderSide(
                    color: Colors.blue,
                    width: 2,
                  ),
                ),
              ),
              onChanged: (value){
                print(value);
              },
            )
```

- **`onChanged`**

每次文本改变时触发（比如构建一个具有自动完成功能的搜索框）

```dart
TextField(
  onChanged: (text) {
    print('First text field: $text (${text.characters.length})');
  },
),
```



## TextFormField

`TextFormField` 是 `TextField` 的扩展，通常与 `Form` 组件一起使用，支持表单验证

**特殊属性：**

- `validator`:  用于验证输入内容的函数，返回错误信息或 `null`
- `autovalidateMode`: 控制何时自动验证输入内容（如 `AutovalidateMode.onUserInteraction`）



## TextEditingController

`TextEditingController` 用于控制 `TextField` 或 `TextFormField` 内容的类。它允许你读取、修改和监听文本输入的变化

| 属性           | 说明                                                         |
| -------------- | ------------------------------------------------------------ |
| `text`         | 获取或设置 `TextField` 或 `TextFormField` 中的文本内容       |
| `selection`    | 获取或设置文本的选择范围（光标位置和选中范围）               |
| `value`        | 获取或设置 `TextField` 的当前值，包括文本、选择范围和组合文本状态 |
| `hasListeners` | 检查是否有监听器附加到 `TextEditingController`               |
| `isDisposed`   | 检查 `TextEditingController` 是否已被释放（调用 `dispose` 方法后） |

```dart
class MyWidget extends StatefulWidget {
  @override
  _MyWidgetState createState() => _MyWidgetState();
}

class _MyWidgetState extends State<MyWidget> {
  final TextEditingController _controller = TextEditingController();

  @override
  void dispose() {
    _controller.dispose(); // 释放资源
    super.dispose();
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('TextEditingController Example'),
      ),
      body: Padding(
        padding: const EdgeInsets.all(16.0),
        child: TextField(
          controller: _controller,
          decoration: InputDecoration(
            labelText: 'Enter your text',
          ),
        ),
      ),
    );
  }
}
```

<warning>TextEditingController 需要关闭</warning>

- **`addListener`**

添加一个监控器，每次文本改变时触发

```dart
 final myController = TextEditingController();

  @override
  void initState() {
    super.initState();

    // Start listening to changes.
    myController.addListener(_printLatestValue);
  }

  @override
  void dispose() {
    // Clean up the controller when the widget is removed from the widget tree.
    // This also removes the _printLatestValue listener.
    myController.dispose();
    super.dispose();
  }

  void _printLatestValue() {
    final text = myController.text;
    print('Second text field: $text (${text.characters.length})');
  }
```

