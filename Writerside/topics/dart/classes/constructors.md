# 构造函数



## 生成构造函数

```dart
class Point {
  double x, y = 0;

  Point(this.x, this.y);
}
```



## 默认构造函数

如果没有声明构造函数，Dart 将使用默认构造函数。默认构造函数是一个没有参数或名称的生成构造函数



## 命名构造函数

使用`类名称.构造函数名`定义

<note>在类中使用命名构造函数实现多个构造器，可以提高代码的清晰度</note>

```dart
class Point {
  final double x, y;

  //命名构造函数1
  Point.origin()
      : x = 0,
        y = 0;

  //命名构造函数2
  Point.fromJson({required this.x, required this.y});
}
```



## 常量构造函数

如果类生成的对象不会改变，则可以通过常量构造函数创建，常量类中的属性需要用`final`修饰，构造需要用`const`修饰

```dart
class ImmutablePoint {
  
  final double x, y;

  const ImmutablePoint(this.x, this.y);
}
```

在实例化常量类时，不能用`new`，而需要用`const`

```dart
void main() {
  var point  = const ImmutablePoint(1, 2);
  var point2 = const ImmutablePoint(1, 2);
  //true
  print(point == point2);
}
```

<note>使用常量构造函数可以优化效率</note>



## 工厂构造函数

使用场景：

- 避免创建过多的重复实例

```dart
class Logger {
  final String name;
  bool mute = false;

 
  static final Map<String, Logger> _cache =
      <String, Logger>{};

  factory Logger(String name) {
    return _cache.putIfAbsent(
        name, () => Logger._internal(name));
  }

  factory Logger.fromJson(Map<String, Object> json) {
    return Logger(json['name'].toString());
  }

  Logger._internal(this.name);
}
```

- 调用子类的构造函数

```dart
abstract class Animal {
  String? name;
  void getNoise();
  factory Animal(String type, String name) {
    switch (type) {
      case "cat":
        return new Cat(name);
      case "dog":
        return new Dog(name);
      default:
        throw "The '$type' is not an animal";
    }
  }
}

class Cat implements Animal {
  String? name;
  Cat(this.name);

  @override
  void getNoise() {
    print("${this.name}: 喵~");
  }
}

class Dog implements Animal {
  String? name;
  Dog(this.name);

  @override
  void getNoise() {
    print("${this.name}: 旺~");
  }
}
void main() {
  var cat = new Animal("cat", "花花");
  var dog = new Animal("dog", "小黑");
  cat.getNoise(); // 花花:  喵~
  dog.getNoise(); // 小黑: 旺~
}
```

- 单例模式

```dart
class Singleton {
  static final Singleton _singleton = Singleton._internal();

  factory Singleton() {
    return _singleton;
  }

  Singleton._internal();
}
void main() {
  var s1 = Singleton();
  var s2 = Singleton();
  print(identical(s1, s2)); // true
}
```





## 重定向构造函数

构造函数可能会重定向到同一个类中的另一个构造函数。重定向构造函数有一个空体。构造函数`this`在冒号 (:) 后使用类名代替

```dart
class Point {
  double x, y;

  // The main constructor for this class.
  Point(this.x, this.y);

  // Delegates to the main constructor.
  Point.alongXAxis(double x) : this(x, 0);
}
```

