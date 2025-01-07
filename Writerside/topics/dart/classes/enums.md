# 枚举



## 简单枚举

```dart
enum Color { red, green, blue }
```



## 增强枚举

- 实例变量必须是`final`
- 所有生成构造函数都必须是常量
- 工厂构造函数只能返回固定的枚举实例之一
- 枚举不能继承
- 枚举不能覆盖`index`，`hashCode`，`==`
- 不能声明名为`values`的成员

```dart
enum Vehicle implements Comparable<Vehicle> {
  car(tires: 4, passengers: 5, carbonPerKilometer: 400),
  bus(tires: 6, passengers: 50, carbonPerKilometer: 800),
  bicycle(tires: 2, passengers: 1, carbonPerKilometer: 0);

  const Vehicle({
    required this.tires,
    required this.passengers,
    required this.carbonPerKilometer,
  });

  final int tires;
  final int passengers;
  final int carbonPerKilometer;

  int get carbonFootprint => (carbonPerKilometer / passengers).round();

  bool get isTwoWheeled => this == Vehicle.bicycle;

  @override
  int compareTo(Vehicle other) => carbonFootprint - other.carbonFootprint;
}
```

<note>增强枚举中的实例方法可使用`this`用于引用当前枚举值</note>



## 使用枚举

枚举中的每个值都有一个`index`getter，它返回枚举声明中该值从零开始的位置。例如，第一个值的索引为 0，第二个值的索引为 1。

```dart
assert(Color.red.index == 0);
assert(Color.green.index == 1);
assert(Color.blue.index == 2);
```

要获取所有枚举值的列表，请使用枚举`values`常量。

```dart
List<Color> colors = Color.values;
assert(colors[2] == Color.blue);
```

如果需要访问枚举值的名称，请使用以下`.name`属性：

```dart
print(Color.blue.name); // 'blue'
```