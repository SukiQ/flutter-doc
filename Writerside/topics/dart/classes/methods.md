# 方法



## 定义运算符

Dart 允许使用以下名称定义运算符

- `<`
- `>`
- `<=`
- `>=`
- `==`
- `~`
- `-`
- `+`
- `/`
- `~/`
- `*`
- `%`
- `|`
- `ˆ`
- `&`
- `<<`
- `>>>`
- `>>`
- `[]=`
- `[]`

```dart
class Vector {
  final int x, y;

  Vector(this.x, this.y);

  Vector operator +(Vector v) => Vector(x + v.x, y + v.y);
  Vector operator -(Vector v) => Vector(x - v.x, y - v.y);

  @override
  bool operator ==(Object other) =>
      other is Vector && x == other.x && y == other.y;

  @override
  int get hashCode => Object.hash(x, y);
}
```



## Getter/Setter

`Getters`和`Setters`是读写对象属性的特殊方法，每一个实例变量都隐含有一个`Getter`方法（如：object.x）和一个`Setter`方法（如：object.x = 'xxx'）

```dart
class Rectangle {
  double left, top, width, height;
 
  Rectangle(this.left, this.top, this.width, this.height);
 
  double get right => left + width;
  set right(double value) => left = value - width;
 
  double get bottom => top + height;
  set bottom(double value) => top = value - height;
}
```

