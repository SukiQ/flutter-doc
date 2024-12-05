# 集合



## List

- 创建（字面量）

```dart
var list = [1,2,3]
```

<note>dart会根据list字面量的数据进行类型推断，如果后续插入了不同类型的数据则会引发错误</note>

- 创建（带泛型）

```dart
var list = <String>[];
//or
List<String> list = [];
```

- 函数创建

```sql
List<int> list = List.empty(growable: true);
```

- 函数

| 函数名           | 函数描述                                 | 样例                                                                                                           |
| ---------------- | ---------------------------------------- |--------------------------------------------------------------------------------------------------------------|
| add()            | 添加元素                                 | `numbers.add(4)`                                                                                             |
| addAll()         | 添加多个元素                             | `numbers.addAll([4, 5, 6])`                                                                                  |
| sort()           | 元素排序                                 | `numbers.sort()` <br/>`numbers.sort((a,b)=> a.hashCode - b.hashCode)`                                        |
| shuffle()        | 随机洗牌元素                             | `numbers.shuffle()`                                                                                          |
| indexOf(）       | 元素的位置                               | `notes.indexOf('fa')`                                                                                        |
| indexWhere()     | 数组中第一个满足条件元素的位置           | `notes.indexWhere((note) => note.startsWith('r'))`<br/>`notes.indexWhere((note) => note.startsWith('r'), 2)` |
| lastIndexWhere() | 数组中第一个满足条件元素的位置（倒叙）   | `notes.lastIndexWhere((note) => note.startsWith('k'))`                                                       |
| lastIndexOf()    | 元素的位置（倒叙）                       | `notes.lastIndexOf('fa')`                                                                                    |
| clear()          | 清空数组                                 | `numbers.clear()`                                                                                            |
| insert()         | 在指定位置插入元素                       | `numbers.insert(index, 10)`                                                                                  |
| insertAll()      | 在指定位置插入多个元素                   | `numbers.insertAll(2, [10, 11])`                                                                             |
| setAll()         | 在指定位置覆盖多个元素                   | `list.setAll(1, ['bee', 'sea'])`                                                                             |
| remove()         | 移除列表中第一个出现的元素               | `parts.remove('head')`                                                                                       |
| removeAt()       | 移除并返回列表中指定位置的元素           | `parts.removeAt(2)`                                                                                          |
| removeLast()     | 移除并返回列表中最后一个元素             | `parts.removeLast()`                                                                                         |
| removeWhere()    | 移除所有满足条件的元素                   | `numbers.removeWhere((item) => item.length == 3)`                                                            |
| retainWhere()    | 移除所有不满足条件的元素                 | `numbers.retainWhere((item) => item.length == 3)`                                                            |
| +                | 将列表元素拼接                           | `list+["bee","sea"]`                                                                                         |
| sublist()        | 截取指定位置的元素并返回为新的列表       | `colors.sublist(1, 3)`                                                                                       |
| getRange()       | 截取指定位置的元素并返回为新的集合       | `colors.getRange(0, 3)`                                                                                      |
| setRange()       | 截取指定位置的元素并用传入的列表元素替换 | `list1.setRange(1, 3, list2)`                                                                                |
| removeRange()    | 从列表中移除指定位置的元素               | `numbers.removeRange(1, 4)`                                                                                  |
| fillRange()      | 使用指定元素替换掉列表中的一段位置       | `words.fillRange(1, 3, 'new')`                                                                               |
| replaceRange()   | 用某一数组替换指定索引范围内的所有元素   | `numbers.replaceRange(1, 4, [6, 7])`                                                                         |
| asMap()          | 将列表转为不可变的Map                    | `words.asMap()`                                                                                              |
| =                | 与列表进行比较                           | `list1==list2`                                                                                               |



## Map

- 创建（字面量）

```dart
var map = {
  'first': 'partridge',
  'second': 'turtledoves',
  'fifth': 'golden rings'
}
```

- 创建（带泛型）

```dart
var map = Map<String, String>()
//or
Map<String, String> map = []
```

- 函数

| 函数名          | 函数描述                                                 | 样例                                                |
| --------------- | -------------------------------------------------------- | --------------------------------------------------- |
| cast()          | 泛型提升为其父祖类                                       | `mapWithStringKeys.cast<Object,Object>()`           |
| containsValue() | 是否包含某个value                                        | `moonCount.containsValue(3)`                        |
| containsKey()   | 是否包含某个key                                          | `moonCount.containsKey('Uranus')`                   |
| []              | 返回给定key的值，如果key不在Map中，则为null              | `map['sec']`                                        |
| []=             | 将key与给定的value关联，如果已存在，则更新               | `map['sec']=2`                                      |
| map()           | 将Map转换成其他泛型的Map                                 | `map.map((key, value) => MapEntry(value, key))`     |
| addEntries()    | 两个Map合并，类型需要一致 ，且如果key相同，则会覆盖value | `map20.addEntries(map21.entries)`                   |
| update()        | 根据指定的Key对应的value做出修改                         | `map10.update('b10', (value) => value * 2)`         |
| updateAll()     | 对所有的Key对应的value做出修改                           | `map.updateAll((key, value) => value * 2)`          |
| removeWhere()   | 移除所有满足条件的元素                                   | `map13.removeWhere((key, value) => value > 3)`      |
| putIfAbsent()   | 存在key则返回value，查不到则返回值，不修改Map            | `map22.putIfAbsent('a22', () => 2)`                 |
| addAll()        | 将指定Map合并到当前Map                                   | `map18.addAll({'a18':1,'b18':7,'a19':2})`           |
| remove()        | 移除列指定元素                                           | `map.remove(2)`                                     |
| clear()         | 清空Map                                                  | `map.clear()`                                       |
| forEach()       | 遍历Map                                                  | `map.forEach((key, value) => print("$key $value"))` |



## Set

- 创建（字面量）

```dart
var set = {'fluorine', 'chlorine', 'bromine', 'iodine', 'astatine'}
```

- 创建（带泛型）

```dart
var set = Set<String>()
//or
Set<> set = {}
```

- 函数

| 函数名         | 函数描述                                                     | 样例                                                         |
| -------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| cast()         | 转换为对应的类型                                             | `setOfStrings.cast<int>()`                                   |
| contains()     | 是否包含某个元素                                             | `characters.contains('B')`                                   |
| add()          | 添加元素                                                     | `dateTimes.add(time1)`                                       |
| addAll()       | 添加元素集合                                                 | `characters.addAll({'A', 'B', 'C'})`                         |
| remove()       | 移除列指定元素                                               | `characters.remove('B')`                                     |
| lookup()       | 从Set中查找元素，有则返回，无则返回null                      | `colorsA.lookup('red')`                                      |
| removeAll()    | 移除多个元素                                                 | `colors.removeAll(['cyan', 'purple'])`                       |
| retainAll()    | 在Set中保留集合中的所有元素，不包含在集合中的元素将从Set中移除 | `colorsA.retainAll(['red', 'blue'])`                         |
| removeWhere()  | 移除所有满足条件的元素                                       | `characters.removeWhere((element) => element.startsWith('B'))` |
| retainWhere()  | 移除所有不满足条件的元素                                     | `characters.retainWhere((element) => element.startsWith('B')` |
| containsAll()  | 判断是否包含所有指定的元素                                   | `characters.containsAll({'A', 'D'})`                         |
| intersection() | 提取两个Set交集元素创建新的Set                               | `characters1.intersection(characters2)`                      |
| union()        | 提取两个Set并集元素创建新的Set                               | `colorsA.union(colorsB)`                                     |
| difference()   | 提取Set与指定Set的差集元素创建新的Set                        | `characters1.difference(characters2)`                        |
| clear()        | 清空Set                                                      | `characters.clear()`                                         |
| toSet()        | 以Set为模板创建新的Set                                       | `characters.toSet()`                                         |

