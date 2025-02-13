# 风格



## 命名

- **UpperCamelCase**：类、枚举、typedef 
- **lowercase_with_underscores**：包、源文件
- **lowerCamelCase**：对象，变量，参数，**常量**，**枚举值**



## 未使用的回调参数

使用额外的下划线以避免名称冲突：`__`、`___`

```dart
futureOfVoid.then((_) {
  print('Operation complete.');
});
```

