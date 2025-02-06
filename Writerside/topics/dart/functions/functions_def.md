# 函数定义

## 箭头函数

- 声明


```dart
bool isNoble(int atomicNumber) {
  return _nobleGases[atomicNumber] != null;
}
```

- 箭头函数

```dart
bool isNoble(int atomicNumber) => _nobleGases[atomicNumber] != null;
```

<note>在dart中箭头函数只是普通函数的一种简写形式</note>



## 函数参数

- 必填参数

```dart
String userInfo(String username,int age){
    return 'use: $username age: $age';
  }
```

- 可选参数

```dart
String userInfo(String username,[int? age]){
    return 'use: $username age: $age';
  }
```

<warning>可选参数必须在必填函数后面</warning>

- 命名参数

```dart
//命名参数
String userInfo(String username,{required int age}){
    return 'use: $username age: $age';
  }
print(userInfo('hxq',age: 18));
```

<note>命名参数也是可选的，除非它们被明确标记为 `required`</note>



## main() 函数

- 无参

```dart
void main() {
  print('Hello, World!');
}
```

- 有参

```dart
void main(List<String> arguments) {
  print(arguments);
}
```



## 匿名函数

```dart
var uppercaseList = list.map((item) {
  return item.toUpperCase();
}).toList();
```



## Tear-offs

可以在使用 `lambda` 函数时，如果函数体中仅有一个函数调用，可以省略函数的入参

```dart
var charCodes = [68, 97, 114, 116];
//lambda
charCodes.forEach((code) {
  print(code);
});
//tear-offs
charCodes.forEach(print);
```



## 返回值

所有函数都会返回一个值。如果没有指定返回值，则语句`return null;`会隐式附加到函数主体中

```dart
foo() {}
assert(foo() == null);
```



## 外部函数

外部函数是函数体与其声明分开实现的函数。使用`external`关键字在函数声明前添加

```dart
external void someFunc(int i);
```

