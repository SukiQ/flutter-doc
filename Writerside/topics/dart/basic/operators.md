# 操作符



## as

类型转换操作符

```dart
(employee as Person).firstName = 'Bob';
```



## is

判断类型操作符

```dart
if (employee is Person) {
  employee.firstName = 'Bob';
}
```



## is!

反判断类型操作符

```dart
if(employee is! Person) {
  ...
}
```



## ??=

判空赋值运算符，如果对象为空，则赋值，不为空则保持不变

```dart
b ??= value;
```



## ?. 

条件成员访问符，如果对象为null，返回null，否则访问成员属性或方法

```dart
print(name?.length);
```



## ?[]

条件下标访问符，如果对象为null，返回null，否则通过下标访问变量

```dart
print(fooList?[1].hashCode)
```



## `*expr1* ?? *expr2*`

如果 `expr1` 为非 null，则返回其值; 否则，计算并返回 `expr2` 的值

```dart
String playerName(String? name) => name ?? 'Guest';
```



## 级联表达式

允许你在同一个对象上连续使用操作符，除了方法调用之外，你还可以获取同一个对象上的成员变量。这样做通常省去了创建临时变量的步骤，同时允许你写出更流畅的代码

```dart
var paint = Paint()
  ..color = Colors.black
  ..strokeCap = StrokeCap.round
  ..strokeWidth = 5.0;
//等效于
var paint = Paint();
paint.color = Colors.black;
paint.strokeCap = StrokeCap.round;
paint.strokeWidth = 5.0;
```



## 空短路级联

```dart
querySelector('#confirm') // Get an object.
  ?..text = 'Confirm' // Use its members.
  ..classes.add('important')
  ..onClick.listen((e) => window.alert('Confirmed!'))
  ..scrollIntoView();
//等效于
var button = querySelector('#confirm');
button?.text = 'Confirm';
button?.classes.add('important');
button?.onClick.listen((e) => window.alert('Confirmed!'));
button?.scrollIntoView();
```

