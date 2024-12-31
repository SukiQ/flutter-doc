# 混入

`Mixin`是一种有利于代码复用，又避免了多继承的解决方案

<note>mixin并不是对子类的拓展，而是对父类的拓展</note>

|                | 继承      | 实现         | 混入   |
| -------------- | --------- | ------------ | ------ |
| 关键字         | `extends` | `implements` | `with` |
| 数量           | 1个       | 多个         | 多个   |
| 父类是否可实现 | 是        | 否           | 是     |



## 使用mixin {id="mixin_1"}

要使用混入，请使用`with`关键字，后跟一个或多个混入类名称

```dart
class Musician extends Performer with Musical {
  // ···
}

class Maestro extends Person with Musical, Aggressive, Demented {
  Maestro(String maestroName) {
    name = maestroName;
    canConduct = true;
  }
}
```



## 定义mixin {id="mixin_2"}

要定义 mixin，请使用`mixin`关键字

- mixin不能有`extends`，
- mixin不能实例化
- mixin可以定义**抽象方法**，子类必须实现
- mixin可以`implements`接口

```dart
mixin Musical {
  bool canPlayPiano = false;
  bool canCompose = false;
  bool canConduct = false;

  void entertainMe() {
     // Ignore
  }
}
```



## 定义mixin class

`mixin class`声明定义了一个类，该类既可用作常规类，又可用作 `mixin`

- mixin class不能有`extends`
- mixin class可以**实例化**，但不能有**构造函数**

```dart
mixin class Musician {
  // ...
}
```



## 限制mixin

使用`on`关键字限制混入`mixin`的类

```dart
mixin MusicalPerformer on Musician {
  performerMethod() {
    print('Performing music!');
    super.musicianMethod();
  }
}
```

