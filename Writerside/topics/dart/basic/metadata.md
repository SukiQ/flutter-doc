# 注解



## @Deprecated 

过时注解

```dart
@Deprecated("""
[oldFunction] is being deprecated in favor of [newFunction] (with slightly
different parameters; see [newFunction] for more information). [oldFunction]
will be removed on or after the 4.0.0 release.
""")
void oldFunction(arg1, arg2) {}
```



## @override 

覆盖注解

```dart
  @override
  Widget build(BuildContext context) {
    // TODO: implement build
    throw UnimplementedError();
  }
```
