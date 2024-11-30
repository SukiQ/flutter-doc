# 变量


## var
`var`可以自行推断出类型，类似于 JavaScript 中的`var`，它可以接收任何类型的变量，但最大的不同是 Dart 中 `var` 变量一旦赋值，**类型便会确定**，则不能再改变其类型
```dart
var t = "hi world";
```




## Object
`Object` 是 Dart 所有对象的根基类，也就是说在 Dart 中所有类型都是`Object`的子类(包括Function和Null)，所以任何类型的数据都可以赋值给`Object`声明的对象
```dart
Object x;
x = "2"
```




## dynamic
`dynamic`与`Object`声明的变量都可以赋值任意对象，且后期可以改变赋值的类型，`dynamic`与`Object`不同的是`dynamic`声明的对象编译器会提供所有可能的组合，而`Object`声明的对象只能使用 `Object` 的属性与方法, 否则编译器会报错
```dart
dynamic a;
a = "";
print(a.length);
```




## final / const

如果您从未打算更改一个变量，那么使用 `final` 或 `const`，不是`var`，也不是一个类型。 一个 `final` 变量只能被设置一次，两者区别在于：`const` 变量是一个编译时常量（编译时直接替换为常量值），`final`变量在第一次使用时被初始化。被`final`或者`const`修饰的变量，变量类型可以省略

```dart
final str = "hi world";
const str1 = "hi world";
```


## 空安全

- 不可空（默认）


```dart
int i = 8;
```

- 可空类型

```dart
int? j;
```

- 预期不为空

```dart
late int k;
k=9;
```



