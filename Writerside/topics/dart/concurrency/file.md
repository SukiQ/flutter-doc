# 文件



## File

- 定义

```dart
 var config = File('config.txt');
// 读取文件
var stringContents = await config.readAsString();
```

- 函数

| 函数名          | 函数描述                                   | 样例                                                 |
| --------------- | ------------------------------------------ | ---------------------------------------------------- |
| readAsStrin()   | 读取文件内容作为字符串                     | `String contents = await file.readAsString();`       |
| writeAsString() | 将字符串写入文件                           | `await file.writeAsString('Hello, Dart!');`          |
| readAsBytes()   | 读取文件内容作为字节数组                   | `List<int> bytes = await file.readAsBytes();`        |
| writeAsBytes()  | 将字节数组写入文件                         | `await file.writeAsBytes([72, 101, 108, 108, 111]);` |
| exists()        | 检查文件是否存在                           | `bool exists = await file.exists();`                 |
| delete()        | 删除文件                                   | `await file.delete();`                               |
| length()        | 获取文件的字节长度                         | `int length = await file.length();`                  |
| open()          | 打开文件进行读写                           | `RandomAccessFile raf = await file.open();`          |
| stat()          | 获取文件的状态信息（如大小、修改时间）     | `FileStat stat = await file.stat();`                 |
| create()        | 创建一个文件，如果文件已存在则不做任何操作 | `await file.create();`                               |
| copy()          | 复制文件到指定路径                         | `File newFile = await file.copy('new_path.txt');`    |
| rename()        | 重命名文件                                 | `await file.rename('new_name.txt');`                 |
| parent()        | 获取文件的父目录                           | `Directory parentDir = file.parent;`                 |



### 流式读取文件

```dart
Stream<List<int>> stream = File("example.txt").openRead();
 
stream.listen((List<int> event) {
// 处理文件内容
   print(event);
}
```



### 随机读取文件

```dart
RandomAccessFile raf = await file.open();
List<int> bytes = await raf.read(100); // 读取前 100 字节
print(String.fromCharCodes(bytes));  
```



### 写入文件

```dart
var logFile = File('log.txt');
var sink = logFile.openWrite();
sink.write('FILE ACCESSED ${DateTime.now()}\n');
await sink.flush();
await sink.close();
```



## Directory

- 定义

```dart
var dir = Directory('tmp');
```

- 函数

| 函数名       | 函数描述                                         | 样例                                            |
| ------------ | ------------------------------------------------ | ----------------------------------------------- |
| create()     | 创建目录，如果目录已存在，则不做任何操作         | `await directory.create();`                     |
| delete()     | 删除目录及其内容                                 | `await directory.delete();`                     |
| exists()     | 检查目录是否存在                                 | `bool exists = await directory.exists();`       |
| list()       | 列出目录中的文件和子目录（异步）                 | `await directory.list();`                       |
| rename()     | 重命名目录                                       | `await directory.rename('new_directory_name');` |
| stat()       | 获取目录的状态信息（如修改时间、文件类型等）     | `DirectoryStat stat = await directory.stat();`  |
| path()       | 获取目录的路径                                   | `String path = directory.path;`                 |
| parent()     | 获取目录的父目录                                 | `Directory parentDir = directory.parent;`       |
| createSync() | 同步创建目录。如果目录已存在，则不做任何操作     | `directory.createSync();`                       |
| deleteSync() | 同步删除目录及其内容                             | `directory.deleteSync();`                       |
| existsSync() | 同步检查目录是否存在                             | `bool exists = directory.existsSync();`         |
| listSync()   | 同步列出目录中的文件和子目录                     | `directory.listSync();`                         |
| renameSync() | 同步重命名目录                                   | `directory.renameSync('new_directory_name');`   |
| statSync()   | 同步获取目录的状态信息（如修改时间、文件类型等） | `DirectoryStat stat = directory.statSync();`    |