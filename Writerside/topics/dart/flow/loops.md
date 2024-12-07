# 循环



## for

```dart
var message = StringBuffer('Dart is fun');
for (var i = 0; i < 5; i++) {
  message.write('!');
}
```



## for-in

```dart
for (final Candidate(:name, :yearsExperience) in candidates) {
  print('$name has $yearsExperience of experience.');
}
```



## while

```dart
while (!isDone()) {
  doSomething();
}
```



## do-while

```dart
do {
  printLine();
} while (!atEndOfPage());
```

