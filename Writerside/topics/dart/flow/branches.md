# 分支



## if

```dart
if (isRaining()) {
  you.bringRainCoat();
} else if (isSnowing()) {
  you.wearJacket();
} else {
  car.putTopDown();
}
```



### if-case

<note> Dart 3.0+</note>

```dart
if (pair case [int x, int y]) {
  print('Was coordinate array $x,$y');
} else {
  throw FormatException('Invalid coordinates.');
}
```



## switch 

### switch语句

`switch`语句后面可以有多个`case`子句，每一个`case`子句都可以是一个`patterns`，当没有`case`子句匹配时，就会执行`default`子句或者`_`通配符子句

```dart
switch (command) {
  case 'OPEN':
    executeOpen();
    continue newCase; // 继续执行
 
  case 'DENIED':
  case 'CLOSED':
    executeClosed(); // `DENIED`和`CLOSED`均会执行
 
  newCase:
  case 'PENDING':
    executeNowClosed(); // `OPEN`和`PENDING`均会执行
}
```

### switch表达式

<note> Dart 3.0+</note>

- case可选项无需使用`case`开头
- case可选项的逻辑是一个**表达式**，而不是一系列的语句
- case可选项都必须有**逻辑**，空可选性不代表隐性失败
- case可选项模式，逻辑使用`=>`分割
- 多个case可选项之间，使用`,`分割
- 默认可选项，只能使用`_`

```dart
token = switch (charCode) {
  slash || star || plus || minus => operator(charCode),
  comma || semicolon => punctuation(charCode),
  >= digit0 && <= digit9 => number(),
  _ => throw FormatException('Invalid')
};
```



## case-when

计算任何一个`boolean`类型的值，值为`true`代表可以执行本case可选项逻辑，为`false`则**继续执行**下一个case可选项，并不会退出整个switch语句

```dart
switch (pair) {
  case (int a, int b) when a > b:
    print('First element greater');
  case (int a, int b):
    print('First element not greater');
}
```

