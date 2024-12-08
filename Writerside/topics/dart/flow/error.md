# 异常

和Java不同的是，Dart中的异常全部都是**未检测异常**。如果一个方法没有申明任何类型的异常，那么我们就**无需捕获**该方法的异常，Dart提供了`Exception`和`Error`两种异常的基础类型，同时内置了其他一些它们的子类。我们也可以定义我们自己的异常类型，Dart可以把**任何非空的对象**当作异常抛出，且这些对象类型不一定是`Exception`或`Error`类型的子类



## throw

<warning>不建议抛出对象</warning>

```dart
throw FormatException('Expected at least 1 section');
 
throw 'Out of llamas!';
 
void distanceTo(Point other) => throw UnimplementedError();
```



## catch

捕获异常的语法有：

- `on 异常类型 catch(异常对象)`

```dart
try {
    bussinse();
  } on  OutOfMemoryError catch(error){
    print('out of Memory $error');
}
```

- `catch(异常对象）`

```dart
try {
    bussinse();
  } catch(error){
    print('error: $error');
}
```

- `catch(异常对象, 异常堆栈)`

```dart
try {
   bussinse();
}catch (e, s) {
  print('Exception details:\n $e');
  print('Stack trace:\n $s');
}
```



## rethrow

当捕获到异常之后，可以通过`rethrow`重新抛出异常

```dart
void misbehave() {
  try {
    dynamic foo = true;
    print(foo++); 
  } catch (e) {
    print('misbehave() partially handled ${e.runtimeType}.');
    rethrow; 
  }
}
```



## finally

```dart
try {
  breedMoreLlamas();
} finally {
  cleanLlamaStalls();
}
```



## assert

<warning>在生产阶段，`assert`相关代码被忽略，因此断言会失效</warning>

`assert(<condition>, <optionalMessage>);`

断言失败时，抛出`AssertionError`类型的异常

```dart
assert(text != null);
 
assert(urlString.startsWith('https'), 'URL ($urlString) should start with "https".');
```

