# HTTP



## 客户端

- 部署

```yaml
http: ^1.3.0
```

- 函数

| 函数名      | 函数描述                                               | 样例                                                         |
| ----------- | ------------------------------------------------------ | ------------------------------------------------------------ |
| get()       | 发送 GET 请求。                                        | `var response = await http.get(url);`                        |
| post()      | 发送 POST 请求。                                       | `var response = await http.post(url, headers: {...}, body: jsonEncode({...}));` |
| put()       | 发送 PUT 请求。                                        | `var response = await http.put(url, headers: {...}, body: jsonEncode({...}));` |
| delete()    | 发送 DELETE 请求。                                     | `var response = await http.delete(url);`                     |
| head()      | 发送 HEAD 请求，获取响应头信息，不包含响应体。         | `var response = await http.head(url);`                       |
| patch()     | 发送 PATCH 请求，用于部分更新资源。                    | `var response = await http.patch(url, headers: {...}, body: jsonEncode({...}));` |
| send()      | 发送自定义的 HTTP 请求（需要使用 `http.Request` 类）。 | `var request = http.Request('GET', url); var response = await request.send();` |
| read()      | 获取 URL 的响应内容并将其作为字符串返回。              | `var body = await http.read(url);`                           |
| readBytes() | 获取 URL 的响应内容并将其作为字节数组返回。            | `var bytes = await http.readBytes(url);`                     |

```dart
import 'dart:convert' as convert;

import 'package:http/http.dart' as http;

void main(List<String> arguments) async {
  var url = Uri.https('www.googleapis.com', '/books/v1/volumes', {'q': '{http}'});
  
  var response = await http.get(url);
  if (response.statusCode == 200) {
    var jsonResponse =
    convert.jsonDecode(response.body) as Map<String, dynamic>;
    var itemCount = jsonResponse['totalItems'];
    print('Number of books about http: $itemCount.');
  } else {
    print('Request failed with status: ${response.statusCode}.');
  }
}
```



## 服务端

```dart
import 'dart:io';

void main() async {
  // 设置服务器监听的地址和端口
  var address = InternetAddress.anyIPv4;
  var port = 8080;

  // 创建 HTTP 服务器
  var server = await HttpServer.bind(address, port);
  print('Server listening on http://$address:$port');

  // 监听客户端的请求
  await for (var request in server) {
    // 设置响应的内容类型
    request.response.headers.contentType = ContentType.json;

    // 处理不同的请求方法
    if (request.method == 'GET') {
      // 处理 GET 请求
      request.response.write('{"message": "Hello, Dart HTTP Server!"}');
    } else if (request.method == 'POST') {
      // 处理 POST 请求
      var content = await utf8.decoder.bind(request).join();
      request.response.write('Received POST data: $content');
    } else {
      // 其他请求方法
      request.response.statusCode = HttpStatus.methodNotAllowed;
      request.response.write('Method not allowed');
    }

    // 关闭响应
    await request.response.close();
  }
}

```

