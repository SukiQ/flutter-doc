# 元组

<note> Dart 3.0+</note>

records一种匿名、固定大小的、不可变的聚合类型，定义时可以**直接当放入对象**，也可以进行**命名传入**

```dart
var record = ('first', a: 2, b: true, 'last');
```

其中非命令对象通过 `.$index` 访问，命名对象通过 `.name` 访问

```dart
print(record.$1);
print(record.a);
```
