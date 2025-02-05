# 隔离

`Dart`是单线程语言，因此`Dart`程序没有主线程和子线程之分，在`Dart`中线程并不是指`Thread` ，而是指`Isolate` 。因为`Dart`没有线程的概念，只有`Isolate` ，每个`Isolate`都是隔离的，并不会共享内存。所有的`Dart`代码都是在`Isolate`中运行，它就像机器上的一个小空间，具有自己的私有内存块和一个运行着事件循环模型的单线程。也就是说，一旦某个`Dart`函数开始执行，它将执行到这个函数的结束而不被其他`Dart`代码打断，这就是单线程的特性

<note>可以使用Flutter的compute函数代替Isolate.run()</note>



## 创建Isolate {id="isolate_1"}

```dart
const String filename = 'with_keys.json';

void main() async {
  // Read some data.
  final jsonData = await Isolate.run(_readAndParseJson);

  // Use that data.
  print('Number of JSON keys: ${jsonData.length}');
}

Future<Map<String, dynamic>> _readAndParseJson() async {
  final fileData = await File(filename).readAsString();
  final jsonData = jsonDecode(fileData) as Map<String, dynamic>;
  return jsonData;
}
```



## Isolate通信

`Isolate`之间的消息传递是通过 `SendPort` 和 `ReceivePort` 来实现的

- **ReceivePort**: 定义一个接收端口，可以接收来自其他 `isolates` 发送的消息
- **SendPort**: 通过 `ReceivePort.sendPort` 可以获取对应的 `SendPort`，并将其传递给其他 `isolates` 以便它们可以发送消息到这个 `ReceivePort`

```dart
import 'dart:async';
import 'dart:isolate';

//使用Completer来确保打印
Completer<void> _isolateReady = Completer.sync();

void workerIsolate(SendPort sendPort) {
  ReceivePort receivePort = ReceivePort();
  sendPort.send(receivePort.sendPort);
  receivePort.listen((message) {
    print("sub receive: $message");
    sendPort.send("sub 2 main");
  });
}

void main() async {
  ReceivePort receivePort = ReceivePort();
  Isolate isolate = await Isolate.spawn(workerIsolate, receivePort.sendPort);

  SendPort? isolateSendPort;
  receivePort.listen((message) {
    if (message is SendPort) {
      isolateSendPort = message;
      isolateSendPort?.send("main 2 sub");
    } else {
      print("main receive: $message");
      isolate.kill();
      receivePort.close();
      _isolateReady.complete();
    }
  });
  await _isolateReady.future;
}

```

