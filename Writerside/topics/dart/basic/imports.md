# 导入



## 内置库

```dart
// Importing core libraries
import 'dart:math';
```



## 其他库

```dart
// Importing libraries from external packages
import 'package:test/test.dart';
```



## 文件

```dart
// Importing files
import 'path/to/my_other_file.dart';
```



## 库

- 使用 `library` 关键字定义库名

```dart
library my_library;
```

- 使用 `part` 关键字引入模块

```dart
part 'helper.dart';
```

- 使用 `part of` 关键字标识主模块

```dart
part of my_library;
```

<warning>不推荐使用 part</warning>
