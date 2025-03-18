# 表单验证



## 通过Form中的GlobalKey验证

```dart
class MyCustomFormState extends State<MyCustomForm> {
 
  final _formKey = GlobalKey<FormState>();

  @override
  Widget build(BuildContext context) {
   
    return Form(
      key: _formKey,
      child: const Column(
        children: <Widget>[
        ],
      ),
    );
  }
}
```

- `_formKey.currentState!.validate()` 会调用每个 `TextFormField` 的 `validator` 函数进行验证

- 如果所有字段都通过验证，`_formKey.currentState!.save()` 会调用每个 `TextFormField` 的 `onSaved` 函数保存数据

```dart
 ElevatedButton(
                onPressed: () {
                  if (_formKey.currentState!.validate()) {
                    _formKey.currentState!.save();
                    // 表单验证通过，处理表单数据
                    print('Email: $_email');
                    print('Password: $_password');
                  }
                },
                child: Text('提交'),
              )
```

