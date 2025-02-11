# 数学函数

## 三角函数

| 函数名  | 函数描述                 | 样例          |
| ------- | ------------------------ | ------------- |
| sin()   | 计算正弦值               | `sin(pi/4)`   |
| cos()   | 计算余弦值               | `cos(pi/4)`   |
| tan()   | 计算正切值               | `tan(pi/4)`   |
| asi()   | 计算反正弦值             | `asin(1)`     |
| acos()  | 计算反余弦值             | `acos(0)`     |
| atan()  | 计算反正切值             | `atan(1)`     |
| atan2() | 计算反正切值 (x, y 坐标) | `atan2(1, 1)` |

```dart
// 正弦
print('sin($angle) = ${sin(angle)}');
  
// 余弦
print('cos($angle) = ${cos(angle)}');
  
// 正切
print('tan($angle) = ${tan(angle)}');
  
// 反正弦
print('asin(1) = ${asin(1)}');
  
// 反余弦
print('acos(0) = ${acos(0)}');
  
// 反正切
print('atan(1) = ${atan(1)}');
  
// 反正切，传入 x 和 y
print('atan2(1, 1) = ${atan2(1, 1)}');
```



## 最大值/最小值

| 函数名 | 描述       | 样例            |
| ------ | ---------- | --------------- |
| max()  | 计算最大值 | `max(1, 1000)`  |
| min()  | 计算最小值 | `min(1, -1000)` |



## 数学常量

| 函数名  | 描述           | 样例                     |
| ------- | -------------- | ------------------------ |
| pi      | 圆周率         | `sin(pi / 2)` // 1.0     |
| e       | 自然对数的底数 | `log(e)` // 1.0          |
| LN2     | 2 的自然对数   | `log(2)` // LN2          |
| LN10    | 10 的自然对数  | `log(10)` // LN10        |
| LOG2E   | log₂(e)        | `log(e) / LOG2E` // 1.0  |
| LOG10E  | log₁₀(e)       | `log(e) / LOG10E` // 1.0 |
| SQRT2   | 2 的平方根     | `sqrt(2)` // SQRT2       |
| SQRT1_2 | 1/2 的平方根   | `sqrt(1 / 2)` // SQRT1_2 |



## 随机数

可以使用`Random`类生成随机数

| 函数名       | 描述                                       | 样例                  |
| ------------ | ------------------------------------------ | --------------------- |
| nextInt()    | 生成一个大于等于 0 且小于 `max` 的随机整数 | `random.nextInt(100)` |
| nextDouble() | 生成一个在 [0.0, 1.0) 范围内的随机浮点数   | `random.nextDouble()` |
| nextBool()   | 生成一个随机布尔值，`true` 或 `false`      | `random.nextBool()`   |

```dart
// 创建一个随机数生成器
var random = Random();
// 生成一个随机整数 (0 到 99)
int randomInt = random.nextInt(100);
// 生成一个随机浮点数 (0.0 到 1.0)
double randomDouble = random.nextDouble();
// 生成一个随机布尔值
bool randomBool = random.nextBool();
```

