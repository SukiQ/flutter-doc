# JSON

## JSON转换器 {id="json_1"}

- `dart`对象转`JSON`字符串

```dart
var user = {
    'name': 'John',
    'age': 30,
    'isStudent': false,
  };

  // 将 Map 对象编码为 JSON 字符串
  String jsonString = jsonEncode(user);
```

如果需要支持自定义类转换为`JSON`字符串，那么需要添加`toJson()`方法

```dart
class Person {
  String name;
  int age;
  String city;

  Person(this.name, this.age, this.city);

  Map<String, dynamic> toJson() => {
        'name': name,
        'age': age,
        'city': city,
      };
}

void main() {
  var person = Person('John Doe', 30, 'New York');
  var json = jsonEncode(person);
  print(json);  // 输出：{"name":"John Doe","age":30,"city":"New York"}
}
```



- `JSON`字符串转换为`dart`对象

```dart
// 一个 JSON 字符串
String jsonString = '{"name": "John", "age": 30, "isStudent": false}';
// 将 JSON 字符串解码为 Map 对象
var user = jsonDecode(jsonString);
```



## JSON序列化器

处理复杂的JSON数据时，可以使用`json_serializable`库

- 导入

```yaml
dependencies:
  json_annotation: ^4.9.0
dev_dependencies:
  build_runner: ^2.3.3
  json_serializable: ^6.8.0
```

- 编写模板

```dart
import 'package:json_annotation/json_annotation.dart';

part 'test_json.g.dart';

@JsonSerializable()
class Person {
  String name;
  int age;
  String city;

  Person(this.name, this.age, this.city);

  factory Person.fromJson(Map<String, dynamic> json) => _$PersonFromJson(json);

  Map<String, dynamic> toJson() => _$PersonToJson(this);
}

```

 **@JsonSerializable()**

| 参数名            | 描述                                                         |
| ----------------- | ------------------------------------------------------------ |
| createFactory     | 是否为类生成 `fromJson()` 工厂方法，默认值为 `true`          |
| createToJson      | 是否为类生成 `toJson()` 方法，默认值为 `true`                |
| explicitToJson    | 是否强制嵌套对象也调用其 `toJson()` 方法进行序列化，默认为 `false` |
| anyMap            | 是否允许使用动态的 Map 类型，默认为 `false`                  |
| fieldRename       | 定义字段的命名规则，控制 Dart 字段和 JSON 字段的匹配方式     |
| ignoreUnannotate  | 是否忽略没有被 `@JsonKey()` 注解的字段，默认为 `false`       |
| nullable          | 是否允许字段为 `null`，默认为 `false`                        |
| disallowNullValue | 禁止字段值为 `null`，如果该字段为 `null`，则抛出异常         |
| unknownEnumValue  | 设置当枚举值无法匹配时的默认值                               |

用于标记一个类需要支持 JSON 序列化，通常在类上使用，并且要配合 `build_runner` 生成代码。

```dart
@JsonSerializable()
class User {
  final String name;
  final int age;

  User({required this.name, required this.age});

  // 从 JSON 创建对象
  factory User.fromJson(Map<String, dynamic> json) => _$UserFromJson(json);

  // 转换对象为 JSON
  Map<String, dynamic> toJson() => _$UserToJson(this);
}
```

 **@JsonKey()**

用于控制单个字段的序列化行为

| 参数名            | 描述                                                         |
| ----------------- | ------------------------------------------------------------ |
| name              | 定义 JSON 中字段的名称，可以与 Dart 类中的属性名称不同       |
| ignore            | 是否忽略该字段，默认 `false`，设置为 `true` 时，字段不会参与 JSON 序列化和反序列化 |
| defaultValue      | 设置该字段的默认值，当 JSON 中没有该字段时，使用此默认值     |
| fromJson          | 自定义反序列化逻辑，指定如何从 JSON 转换该字段的值           |
| toJson            | 自定义序列化逻辑，指定如何将字段值转换为 JSON                |
| required          | 如果字段在 JSON 中缺失，则抛出异常                           |
| disallowNullValue | 如果字段的值为 `null`，则抛出异常，默认值为 `false`          |
| explicitToJson    | 是否强制嵌套对象也使用 `toJson()`，默认为 `false`            |
| unknownEnumValue  | 指定当枚举值不在预期的范围内时，应该使用的默认值             |

```dart
@JsonSerializable()
class User {
  @JsonKey(name: 'full_name') 
  final String name;

  final int age;

  User({required this.name, required this.age});

  factory User.fromJson(Map<String, dynamic> json) => _$UserFromJson(json);

  Map<String, dynamic> toJson() => _$UserToJson(this);
}
```

- 生成源文件

```bash
dart run build_runner build
```

