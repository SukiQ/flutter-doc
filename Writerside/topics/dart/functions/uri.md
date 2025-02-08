# URI

- 定义

```dart
var httpsUri = Uri(
    scheme: 'https',
    host: 'dart.dev',
    path: '/guides/libraries/library-tour',
    fragment: 'numbers');
var uri = Uri.parse('https://example.org:8080/foo/bar#frag');
```

- 函数

| 函数名      | 函数描述              | 样例                                                     |
| ----------- | --------------------- | -------------------------------------------------------- |
| Uri.parse() | 将给定字符转为URI对象 | `Uri.parse('https://example.org:8080/foo/bar#frag')`     |
| Uri.http()  | 生成http的URI对象     | `Uri.http('example.org', '/foo/bar', {'lang': 'dart'})`  |
| Uri.https() | 生成https的URI对象    | `Uri.https('example.org', '/foo/bar', {'lang': 'dart'})` |
