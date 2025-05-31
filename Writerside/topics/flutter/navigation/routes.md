# 路由



## Navigator

使用 `Navigator` 来管理应用中的页面导航

| 属性                    | 说明                   |
| :---------------------- | :--------------------- |
| push                    | 将给定的路由推入堆栈   |
| pushNamed               | 按名称推送路由         |
| pushReplacement         | 用新路由替换当前路由   |
| pushReplacementNamed    | 按名称替换当前路由     |
| pushAndRemoveUntil      | 推送新路由并删除旧路由 |
| pushNamedAndRemoveUntil | 按名称推送并删除旧路由 |
| pop                     | 从堆栈弹出当前路由     |
| popUntil                | 弹出直到满足条件       |
| canPop                  | 检查是否可以弹出       |
| maybePop                | 安全弹出方法           |
| of                      | 获取当前导航器状态     |

- 跳转

```dart
Navigator.push(
  context,
  MaterialPageRoute(builder: (context) => NewPage()),
);	
```

- 命名路由跳转

```dart
Navigator.pushNamed(context, '/newPage');
```

- 返回上一页 

```dart
Navigator.pop(context);
```

