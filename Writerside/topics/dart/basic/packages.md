# 包



## 导入包

- 在 `pubspec.yaml` 文件中增加包

```yaml
name: my_app

dependencies:
  intl: ^0.20.0
  path: ^1.9.1
```

- 使用 `dart pub get` 命令获取包



## 升级包

- 使用 `dart pub upgrade` 尝试升级`pubspec.yaml` 文件中所有的依赖
- 使用 `dart pub upgrade $package` 升级指定依赖



## 创建包

<img src="package-0.png" alt="image.png" width="550" />

- 使用 `dart create -t package $package` 命令创建包工程

- 在 `pubspec.yaml` 文件中定义依赖



## 发布包

- 使用 `dart pub publish` 发布包