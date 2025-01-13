# 扩展方法

Dart提供了一个**扩展方法**（Extension methods）来扩充目标类的方法



## 使用扩展方法

```dart
extension 扩展方法类名 on 目标类 {
    //扩展方法1
    //扩展方法2
}
```

```dart
void main() {
  print('123'.parseInt());
}

extension NumberParsing on String {
  int parseInt() {
    return int.parse(this);
  }

  double parseDouble() {
    return double.parse(this);
  }
}
```

- `dynamic`动态类型禁止使用扩展方法
- `var`类型可以使用扩展方法，因为会自动推断类型



## 扩展方法冲突

1. 在引入库时，通过`show`或者`hide`关键字限制扩展方法

```dart
import 'string_apis.dart';
 
import 'string_apis_2.dart' hide NumberParsing2;
 
print('42'.parseInt());
```

2. 显示指定**扩展类型**的扩展方法：

```dart
import 'string_apis.dart';
 
import 'string_apis_2.dart';
 
print(NumberParsing('42').parseInt());
print(NumberParsing2('42').parseInt());
```

3. 假设第二种方法的**扩展类型**也一样，那么可在引入库增加前缀解决

```dart
import 'string_apis.dart';
 
import 'string_apis_3.dart' as rad;
```



## 实现扩展方法

- 命名扩展方法

```dart
extension NumberParsing on String {
  int parseInt() {
    return int.parse(this);
  }
 
  double parseDouble() {
    return double.parse(this);
  }
}
```

- 匿名扩展方法

```dart
extension on String {
  bool get isBlank => trim().isEmpty;
}
```

<note>匿名扩展方法的可见范围仅在库内容（类似于私有属性和方法）</note>



## 实现泛型扩展

扩展也运用在泛型参数

```dart
extension MyFancyList<T> on List<T> {
  int get doubleLength => length * 2;
  List<T> operator -() => reversed.toList();
  List<List<T>> split(int at) => [sublist(0, at), sublist(at)];
}
```

