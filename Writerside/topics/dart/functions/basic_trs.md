# 基本类型转换



## int/double -> String

| 函数名                | 函数描述                     | 样例                             |
| --------------------- | ---------------------------- | -------------------------------- |
| toString()            | 转字符                       | `42.toString()`                  |
| toStringAsFixed()     | 转字符并指定小数点右侧的位数 | `123.456.toStringAsFixed(2)`     |
| toStringAsPrecision() | 转字符并指定精度             | `123.456.toStringAsPrecision(2)` |



## String -> int/double 

| 函数名                       | 函数描述                       | 样例                                         |
| ---------------------------- | ------------------------------ | -------------------------------------------- |
| int.parse() / double.parse() | 转字符转为数字类               | `int.parse('42')`<br/>`double.parse('0.50')` |
| num.parse()                  | 转字符转为数字类，倾向转为整型 | `num.parse('0x42')`                          |