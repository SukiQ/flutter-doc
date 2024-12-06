# 模式匹配

<note> Dart 3.0+</note>

## Record

- 非命名 Record 的类型

```dart
var ( 变量1 , 变量2 , ... )  = Record 对象
```


```dart
var user = ('toly',29);
var (name, age) = user;
print('======$name====${age}===');
```

- 命名 Record 类型

```dart
var ( k1: 变量1, k2: 变量2 , ... ) = Record 对象
```

```dart
var position = (x:1,y:3,'p0');
var (x:a, y:b ,c) = position;
print('====$a====$b====$c====');
```



## 集合

- List

```bash
var [ 变量1, 变量2, ... ] = List 对象
```

```dart
List<int> numList = [1, 2, 3];
var [a, b, c] = numList;
print('====$a====$b====$c=');
```

- Map

```bash
var { key : 变量1, key: 变量2, ...} = Map 对象
```

```dart
Map<String,dynamic> data = {
   'name': 'toly',
   'age': 29,
};
var {'name': name,'age': age}= data;
print('======$name====${age}===');
```
