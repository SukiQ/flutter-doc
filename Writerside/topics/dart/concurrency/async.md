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

<warning>考虑改用await替换Future API，使用await比使用 Future API 的代码更容易理解</warning>

| 函数名                | 描述                                                         | 样例                                                         |
| ------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| Future()           | 创建一个 `Future` 对象，通常用于自定义异步操作               | `Future(() => 'Custom Future')`                              |
| Future.value()     | 创建一个立即完成的 `Future`，并返回给定的值                  | `Future.value(42)`                                           |
| Future.error(error) | 创建一个立即完成的 `Future`，并返回一个错误                  | `Future.error(Exception('Error'))`                           |
| Future.delayed()   | 创建一个在指定延迟后执行的 `Future`                          | `Future.delayed(Duration(seconds: 2), () => 'Delayed result')` |
| Future.microtask() | 创建一个在微任务队列中执行的 `Future`                        | `Future.microtask(() => 'Microtask result')`                 |
| Future.sync()      | 创建一个同步执行的 `Future`                                  | `Future.sync(() => 'Sync result')`                           |
| Future.wait()      | 等待多个 `Future` 完成，返回一个包含所有结果的列表           | `Future.wait([Future.value(1), Future.value(2)])`            |
| Future.any()       | 返回第一个完成的 `Future` 的结果，忽略其他 `Future`          | `Future.any([Future.delayed(Duration(seconds: 2), () => 'First'), Future.delayed(Duration(seconds: 1), () => 'Second')])` |
| Future.forEach()   | 对可迭代对象中的每个元素执行异步操作，返回一个 `Future` 列表 | `Future.forEach([1, 2, 3], (int element) async => print(element))` |
| Future.doWhile(fn) | 重复执行异步操作，直到条件不满足为止                         | `Future.doWhile(() => Future.delayed(Duration(seconds: 1), () => false))` |
| then(onValue)      | 注册一个回调，当 `Future` 完成时调用，并返回一个新的 `Future` | `Future.value(42).then((value) => print(value))`             |
| catchError(onError) | 注册一个回调，当 `Future` 失败时调用，并返回一个新的 `Future` | `Future.error(Exception('Error')).catchError((error) => print(error))` |
| whenComplete(action) | 注册一个回调，无论 `Future` 成功或失败都会调用               | `Future.value(42).whenComplete(() => print('Complete'))`     |
| timeout(duration) | 为 `Future` 设置超时时间，超时后返回一个错误                 | `Future.delayed(Duration(seconds: 2)).timeout(Duration(seconds: 1))` |
| asStream()   | 将 `Future` 转换为一个 `Stream`，该 `Stream` 会发出一个事件后关闭 | `Future.value('Stream result').asStream().listen(print)`     |

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

<warning>

- 要定义异步函数，请在函数体前添加 async
- await 关键字仅在 async 函数中起作用

</warning>

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

