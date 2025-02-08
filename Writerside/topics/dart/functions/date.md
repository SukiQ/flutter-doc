# 日期和时间

| **方法名**                            | **说明**                                                     | **样例代码**                                                 |
| ------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| DateTime.now()                        | 获取当前本地时间                                             | `DateTime now = DateTime.now()`                              |
| DateTime.utc()                        | 创建一个 UTC 时间的 `DateTime` 对象                          | `DateTime utcDate = DateTime.utc(2024, 10, 23, 14, 30);`     |
| DateTime()                            | 创建一个本地时间的 `DateTime` 对象                           | `DateTime specificDate = DateTime(2024, 10, 23, 14, 30)`     |
| DateTime.fromMillisecondsSinceEpoch() | 根据毫秒时间戳创建 `DateTime` 对象                           | `DateTime fromMilliseconds = DateTime.fromMillisecondsSinceEpoch(1700000000000)` |
| DateTime.fromMicrosecondsSinceEpoch() | 根据微秒时间戳创建 `DateTime` 对象                           | `DateTime fromMicroseconds = DateTime.fromMicrosecondsSinceEpoch(1700000000000000)` |
| DateTime.parse()                      | 从标准 ISO 8601 字符串创建 `DateTime` 对象                   | `DateTime parsed = DateTime.parse("2024-10-23T14:30:00")`    |
| DateTime.add()                        | 返回一个新的 `DateTime` 对象，它比当前时间晚指定的 `Duration` 时间 | `DateTime futureDate = DateTime.now().add(Duration(days: 5))` |
| DateTime.subtract()                   | 返回一个新的 `DateTime` 对象，它比当前时间早指定的 `Duration` 时间 | `DateTime pastDate = DateTime.now().subtract(Duration(days: 5))` |
| DateTime.isBefore()                   | 判断当前时间是否在指定时间之前                               | `bool isBefore = DateTime.now().isBefore(DateTime(2025, 1, 1))` |
| DateTime.isAfter()                    | 判断当前时间是否在 `other` 之后。                            | `bool isAfter = DateTime.now().isAfter(DateTime(2023, 1, 1));` |
| DateTime.isAtSameMomentAs()           | 判断当前时间是否与 `other` 相同（精确到微秒）                | `bool isSame = DateTime.now().isAtSameMomentAs(DateTime.now())` |
| DateTime.weekday                      | 获取星期几（1 = Monday, 7 = Sunday）                         | `int weekday = DateTime.now().weekday`                       |
| DateTime.year                         | 获取年份                                                     | `int year = DateTime.now().year`                             |
| DateTime.month                        | 获取月份（1-12）                                             | `int month = DateTime.now().month`                           |
| DateTime.day                          | 获取日期（1-31）                                             | `int day = DateTime.now().day`                               |
| DateTime.hour                         | 获取小时（0-23）                                             | `int hour = DateTime.now().hour`                             |
| DateTime.minute                       | 获取分钟（0-59）                                             | `int minute = DateTime.now().minute`                         |
| DateTime.secon                        | 获取秒数（0-59）                                             | `int second = DateTime.now().second`                         |
| DateTime.millisecond                  | 获取毫秒数（0-999）                                          | `int millisecond = DateTime.now().millisecond`               |
| DateTime.microsecond                  | 获取微秒数（0-999999）                                       | `int microsecond = DateTime.now().microsecond`               |
| DateTime.toUtc()                      | 将本地时间转换为 UTC 时间                                    | `DateTime utcTime = DateTime.now().toUtc()`                  |
| DateTime.toLocal()                    | 将 UTC 时间转换为本地时间                                    | `DateTime localTime = DateTime.now().toUtc().toLocal()`      |
| DateTime.toIso8601String()            | 将 `DateTime` 对象转换为 ISO 8601 格式字符串                 | `String isoString = DateTime.now().toIso8601String()`        |
| DateTime.toString()                   | 将 `DateTime` 对象转换为字符串格式（`yyyy-MM-dd HH:mm:ss.SSSSSS`） | `String str = DateTime.now().toString()`                     |
| DateTime.difference()                 | 返回当前时间与指定时间之间的 `Duration`                      | `Duration diff = DateTime.now().difference(DateTime(2025, 1, 1))` |



## 创建日期对象

- 获取当前时间

```dart
DateTime now = DateTime.now();
```

- 指定日期时间

```dart
DateTime specificDate = DateTime(2024, 10, 23, 14, 30, 0); 
```

- 从时间戳创建（Unix 时间戳）

```dart
int timestamp = 1700000000000; // 毫秒级时间戳
DateTime fromTimestamp = DateTime.fromMillisecondsSinceEpoch(timestamp);
```



## **获取时间信息**

```dart
DateTime now = DateTime.now();
print(now.year);    // 年份，例如：2025
print(now.month);   // 月份，例如：2
print(now.day);     // 日期，例如：8
print(now.hour);    // 小时
print(now.minute);  // 分钟
print(now.second);  // 秒
print(now.weekday); // 星期（1=周一，7=周日）
```



##  **时间计算**

- 加减时间

```dart
DateTime now = DateTime.now();
DateTime nextWeek = now.add(Duration(days: 7)); // 7 天后
DateTime lastMonth = now.subtract(Duration(days: 30)); // 30 天前

print(nextWeek);
print(lastMonth);
```

- 计算时间差

```dart
DateTime start = DateTime(2024, 1, 1);
DateTime end = DateTime(2024, 2, 1);

Duration difference = end.difference(start);
print(difference.inDays); // 31天
```



##  时间格式化

Dart 原生不提供格式化方法，可以使用 `intl` 库：

```yaml
dependencies:
  intl: ^0.18.0
```

```dart
import 'package:intl/intl.dart';

void main() {
  DateTime now = DateTime.now();
  String formattedDate = DateFormat('yyyy-MM-dd HH:mm:ss').format(now);
  print(formattedDate); // 2025-02-08 14:30:00
}
```



## String -> DateTime

```dart
DateTime parsedDate = DateTime.parse("2024-10-23 14:30:00");
print(parsedDate); // 2024-10-23 14:30:00.000
```

如果格式不同，可以用 `intl` 解析：

```dart
String dateString = "23/10/2024 14:30";
DateTime parsed = DateFormat("dd/MM/yyyy HH:mm").parse(dateString);
print(parsed);
```



## **时区处理**

Dart `DateTime` 默认是 **本地时间**，但可以用 `toUtc()` 和 `toLocal()` 处理时区：

```dart
DateTime now = DateTime.now();
DateTime utcTime = now.toUtc();
DateTime localTime = utcTime.toLocal();

print(utcTime);  // UTC 时间
print(localTime); // 转回本地时间
```

