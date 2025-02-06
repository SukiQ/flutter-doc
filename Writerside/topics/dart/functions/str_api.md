# 字符函数

| 函数名        | 函数描述                           | 样例                                          |
| ------------- | ---------------------------------- | --------------------------------------------- |
| contains()    | **正则**或字符是否存在             | `'Never odd or even'.contains('odd')`         |
| startsWith()  | 是否以指定字符开头                 | `'Never odd or even'.startsWith('Never')`     |
| endsWith()    | 是否以指定字符结尾                 | `123.456.toStringAsPrecision(2)`              |
| indexOf()     | 返回指定字符的位置                 | `'Never odd or even'.indexOf('odd')`          |
| substring()   | 截取指定字符                       | `'Never odd or even'.substring(6, 9)`         |
| split()       | 使用指定字符分割                   | `'progressive web apps'.split(' ')`           |
| toUpperCase() | 字符转大写                         | `'web apps'.toUpperCase()`                    |
| toLowerCase() | 字符转小写                         | `'WEB APPS'.toLowerCase()`                    |
| trim()        | 删除前后空格                       | `'  hello  '.trim()`                          |
| isEmpty()     | 检查字符串是否为空                 | `''.isEmpty`                                  |
| isNotEmpty()  | 检查字符串是否不为空               | `'  '.isNotEmpty`                             |
| replaceAll()  | 根据**正则**或字符替换字符串的内容 | `'123 say'.replaceAll(RegExp('\\d+'), 'Bob')` |



## 拼接字符串

- **定义**

```dart
var sb = StringBuffer();
sb
  ..write('Use a StringBuffer for ')
  ..writeAll(['efficient', 'string', 'creation'], ' ')
  ..write('.');

var fullString = sb.toString();
```

- **函数**

| 函数名     | 函数描述                       | 样例                                                    |
| ---------- | ------------------------------ | ------------------------------------------------------- |
| write()    | 在尾部拼接个字符               | `sb.write('Use a StringBuffer for ')`                   |
| writeAll() | 在尾部拼接多个字符并指定分隔符 | `sb.writeAll(['efficient', 'string', 'creation'], ' ')` |
| clear()    | 清除字符队列                   | `sb.clear()`                                            |



## 正则表达式

- **定义**

```dart
RegExp regex = RegExp(r'\d+');
```

<note>可以在正则前加入前缀r，标识使用原始字符串，使用原始字符串可将字符串中的每个字符（包括\和$）视为字面量，如字符RegExp(r'\w')等同于RegExp('\\w')</note>

- **函数**

| 函数名       | 函数描述                     | 样例                                                      |
| ------------ | ---------------------------- | --------------------------------------------------------- |
| hasMatch()   | 判断正则是否匹配字符串       | `RegExp(r'\d+').hasMatch('llamas live 15 to 20 years')`   |
| firstMatch() | 查找正则匹配到的第一个匹配项 | `RegExp(r'\d+').firstMatch('llamas live 15 to 20 years')` |
| allMatches() | 查找正则匹配到的所有匹配项   | `RegExp(r'\d+').allMatches('llamas live 15 to 20 years')` |

```dart
RegExp regex = RegExp(r'\s+(\d+)');
String text = 'Hello 123 World 456';
print(regex.firstMatch('Hello 123 World 456')!.group(0)); //  123
print(regex.firstMatch('Hello 123 World 456')!.group(1)); // 123
```

