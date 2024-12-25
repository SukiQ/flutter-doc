# 继承



dart通过`extends`关键字创建子类，通过`super`关键字引用父类

```dart
class Television {
  void turnOn() {
    _illuminateDisplay();
    _activateIrSensor();
  }
}
 
class SmartTelevision extends Television {
  void turnOn() {
    super.turnOn();
    _bootNetworkInterface();
    _initializeMemory();
    _upgradeApps();
  }
}
```



## 重写

通过`@override`注解表明重写父类的成员方法

```dart
class Television {
  // ···
  set contrast(int value) {...}
}
 
class SmartTelevision extends Television {
  @override
  set contrast(num value) {...}
  // ···
}
```



<note>当我们重写了相等`==`操作符，则必须重写`hashCode`的`getter`方法</note>

```dart
class Person {
  final String firstName, lastName;
 
  Person(this.firstName, this.lastName);

  @override
  int get hashCode => Object.hash(firstName, lastName);
 
  @override
  bool operator ==(Object other) {
    return other is Person &&
        other.firstName == firstName &&
        other.lastName == lastName;
  }
}
```



## noSuchMethod

若需要在访问不存在的方法或实例变量时，我们代码能做出响应（而不是抛出`NoSuchMethodError`错误），则我们可以重写`noSuchMethod()`方法

```dart
class A {
 
  @override
  void noSuchMethod(Invocation invocation) {
    print('You tried to use a non-existent member: '
        '${invocation.memberName}');
  }
}
```

在Dart语言中，除了以下几种情况外，我们不可能调用一个不存在的方法（编译就出错）：

- 对象是`dynamic`动态类型，运行时才能确定具体类型
- 对象是静态类型，存在未实现的方法，且它实现了`noSuchMethod()`方法（即它不是继承`Object`类型的`noSuchMethod()`方法）