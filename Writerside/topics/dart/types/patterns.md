# 模式

<note> Dart 3.0+</note>

## Record

- 匿名 Record 的类型

```dart
var ( 变量1 , 变量2 , ... )  = Record 对象
```


```dart
var user = ('toly',29);
var (name, age) = user;
print('$name ， $age');
```

- 命名 Record 类型

```dart
var ( k1: 变量1, k2: 变量2 , ... ) = Record 对象
```

```dart
var position = (x:1,y:3,'p0');
var (x:a, y:b ,c) = position;
print('$a , $b , $c');
```



## 集合

- List

```bash
var [ 变量1, 变量2, ... ] = List 对象
```

```dart
List<int> numList = [1, 2, 3];
var [a, b, c] = numList;
print('$a , $b , $c');
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
print('$name , $age');
```



## 对象

- 命名对象类型

```bash
var 类名( 命名字段1 : 变量1 , 命名字段2 : 变量2, ...) = 对象
```

```dart
Person person = Person(name: 'toly', age: 29); 
var Person(name : a, age: b) = person;
print('$a , $b');
```

- 匿名对象类型

```dart
Person person = Person(name: 'toly', age: 29);
var Person(:name, :age) = person;
print('$name , $age');
```



## 基本类型对象

```bash
var ( 变量1 , 变量2 , ...) = ( 属性1 , 属性2 , ... )
```

```dart
var (a, b) = (1, 2);
```



## 通配符

`_` 是一个通配符，它不绑定或分配给任何变量，它可用作占位符

```dart
var list = [1, 2, 3];
var [_, two, _] = list;
```

