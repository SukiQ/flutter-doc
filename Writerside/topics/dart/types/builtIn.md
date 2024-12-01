# 基本类型



## int

整型且值不大于 64 位，具体取决于平台。 在本机平台上，值可以来自   -2^63^ 到 2^63^-1



## double

64 位（双精度）浮点数

<note> 两者都是num的子类型，您还可以将变量声明为 num。如果这样做，变量可以同时具有整数和双精度值 </note>

```dart
num x = 1; // x can have both int and double values
x += 2.5;
```



## string

可以使用单引号或双引号来创建字符串

```dart
var s1 = 'Single quotes work well for string literals.';
var s2 = "Double quotes work just as well.";
```



## bool

Dart有一个名为 `bool` 的类型，只有两个对象具有 bool 类型：`true`和`false`，它们都是编译时常量

```dart
bool boolean = true;
```
