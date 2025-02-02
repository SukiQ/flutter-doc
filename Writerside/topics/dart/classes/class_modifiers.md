# 类修饰符

- `abstract`

- `base`
- `final`
- `interface`
- `sealed`

- `mixin`



## 无修饰符

当我们定义类或者`Mixin`时，不希望对构造函数或者子类进行限制时，我们可以不使用修饰符，**flutter的类既可以被继承（继承所有方法），又可以被实现（重写所有方法）**

支持以下操作：

- 通过构造函数创建类实例
- 通过继承类来创建子类
- 实现类或者`Mixin`的接口
- 混入`Mixin`或者`Mixin`类



## abstract class 抽象类

当我们定义了一个类，但又没有完整地实现了它所有的接口时使用，请使用`abstract`修饰符，抽象类不能被实例化，一般情况，抽象类都包含抽象方法

```dart
// 抽象类
abstract class Vehicle {
  void moveForward(int meters);
}
 
// 实现类
class MockVehicle implements Vehicle {
  @override
  void moveForward(int meters) {
    // ...
  }
}
```



## base class 基类

当我们用`base`修饰符定义了一个类或者`Mixin`时，那么这个基类的实现只能是基类所在库内

<warning>为了保证基类不会被破坏，子类必须使用base，final或者sealed修饰符</warning>

**a.dart**

```dart
base class Vehicle {
  void moveForward(int meters) {
    // ...
  }
}
```

**b.dart**

```dart
import 'a.dart';

// 可以使用构造函数
Vehicle myVehicle = Vehicle();

// 可以被继承
base class Car extends Vehicle {
  int passengers = 4;
  // ...
}

// ERROR: 不能跨库实现
base class MockVehicle implements Vehicle {
  @override
  void moveForward() {
    // ...
  }
}
```



## interface class 接口类

使用`interface`修饰符定义一个接口。接口可以被外部库实现，但是不能被继承

**a.dart**

```dart
interface class Vehicle {
  void moveForward(int meters) {
    // ...
  }
}

// 可以在本库内继承
interface class Vehicle2 extends Vehicle{
  
}
```

**b.dart**

```dart
import 'a.dart';

// 可以使用构造函数
Vehicle myVehicle = Vehicle();

// ERROR: 不能跨库继承
class Car extends Vehicle {
  int passengers = 4;
  // ...
}

// 可以被实现
class MockVehicle implements Vehicle {
  @override
  void moveForward(int meters) {
    // ...
  }
}
```



## abstrace interface class 抽象接口类

当我们使用`abstract interface class`组合修饰符时，可以定义一个抽象接口类：它即有接口类的功能（可被实现，但不能被继承），也有抽象类的功能（有抽象成员）

```dart
abstract interface class Vehicle {
  void moveForward(int meters);
}
```



## final class 不可变类

当使用`final`修饰符时，表示该类不能被其他库继承和**实现**

<warning>final不可变类可以在本库中被继承和实现，子类必须使用base，final或者sealed修饰符</warning>

**a.dart**

```dart
final class Vehicle {
  void moveForward(int meters) {
    // ...
  }
}

// 可以在本库内继承
base class Vehicle2 extends Vehicle{
  
  void moveForward(int meters) {
    // ...
  }
}
```

**b.dart**

```dart
import 'a.dart';

// 可以使用构造函数
Vehicle myVehicle = Vehicle();

// ERROR: 不可以被继承
class Car extends Vehicle {
  int passengers = 4;
  // ...
}

class MockVehicle implements Vehicle {
  // ERROR: 不可以被实现
  @override
  void moveForward(int meters) {
    // ...
  }
}
```



## sealed class 密封类

当我们定义了一个类，且明确该类的所有子类集合时，请使用`sealed`修饰符。这允许我们通过`switch`穷举所有的子类型

`sealed`修饰的类，禁止被其他库继承或者实现，它隐含`abstract`修饰符：

- 不能被实例化
- 可以有工厂构造函数
- 可以定义构造函数，子类可直接使用
- 子类并不是`abstract`抽象类

```dart
// 密封类
sealed class Vehicle {}
 
class Car extends Vehicle {}
 
class Truck implements Vehicle {}
 
class Bicycle extends Vehicle {}
 
// 1. ERROR: 不能被实例化
Vehicle myVehicle = Vehicle();
 
// 2. 子类可以被实例化
Vehicle myCar = Car();
 
String getVehicleSound(Vehicle vehicle) {
  // 3. ERROR: switch中子类未穷举（还有Bicycle子类）
  return switch (vehicle) {
    Car() => 'vroom',
    Truck() => 'VROOOOMM',
  };
}
```



## 有效组合

| 修饰符                      | 构造函数 | 继承   | 实现   | 混入   | 枚举   |
| --------------------------- | -------- | ------ | ------ | ------ | ------ |
| `class`                     | **是**   | **是** | **是** | 否     | 否     |
| `base class`                | **是**   | **是** | 否     | 否     | 否     |
| `interface class`           | **是**   | 否     | **是** | 否     | 否     |
| `final class`               | **是**   | 否     | 否     | 否     | 否     |
| `sealed class`              | 否       | 否     | 否     | 否     | **是** |
| `abstract class`            | 否       | **是** | **是** | 否     | 否     |
| `abstract base class`       | 否       | **是** | 否     | 否     | 否     |
| `abstract interface class`  | 否       | 否     | **是** | 否     | 否     |
| `abstract final class`      | 否       | 否     | 否     | 否     | 否     |
| `mixin class`               | **是**   | **是** | **是** | **是** | 否     |
| `base mixin class`          | **是**   | **是** | 否     | **是** | 否     |
| `abstract mixin class`      | 否       | **是** | **是** | **是** | 否     |
| `abstract base mixin class` | 否       | **是** | 否     | **是** | 否     |
| `mixin`                     | 否       | 否     | **是** | **是** | 否     |
| `base mixin`                | 否       | 否     | 否     | **是** | 否     |