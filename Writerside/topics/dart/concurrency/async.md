# 异步



`Dart` 的运行时模型基于事件循环。事件循环负责执行程序代码、收集和处理事件等
<img src="async-0.png" alt="image.png" width="550" />


## Futures

`Future` 表示异步操作的结果，该操作最终将以 `return` 或 `error` 完成

```dart
Future<String> fetchData() {
  return Future.delayed(Duration(seconds: 2), () => "Data fetched");
}
```



## async/await

- `async`：标记函数为异步，返回一个 `Future`。
- `await`：暂停异步函数的执行，直到 `Future` 完成。

```dart
Future<String> _readFileAsync() async {
  final file = File(filename);
  final contents = await file.readAsString();
  return contents.trim();
}
```



## Stream

Dart 还支持以流形式定义异步代码，`Stream`会在未来一段时间内重复提供值

```dart
Stream<int> stream = Stream.periodic(const Duration(seconds: 1), (i) => i * i);
```



## await-for/yield

await-for 是一种 for 循环，当提供新值时，它才会执行循环的每次后续迭代，使用`yield`使用关键字而不是`return`返回值流的函数

```dart
Stream<int> sumStream(Stream<int> stream) async* {
  var sum = 0;
  await for (final value in stream) {
    yield sum += value;
  }
}
```

