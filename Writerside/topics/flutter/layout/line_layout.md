# 线性布局



## Row

`Row` 是一个用于水平排列子元素的布局小部件。它按顺序将其子组件沿水平方向排列。你可以控制它们在主轴（水平方向）和交叉轴（垂直方向）上的对齐方式

```dart
Row(
  mainAxisAlignment: MainAxisAlignment.center, // 水平方向居中
  crossAxisAlignment: CrossAxisAlignment.start, // 垂直方向顶部对齐
  children: <Widget>[
    Icon(Icons.star),
    Text('Hello, Flutter!'),
    Icon(Icons.star),
  ],
)

```

| 属性                 | 说明                                            |
| -------------------- | ----------------------------------------------- |
| `mainAxisAlignment`  | 控制子元素在主轴（水平方向）上的对齐方式        |
| `crossAxisAlignment` | 控制子元素在交叉轴（垂直方向）上的对齐方式      |
| `textDirection`      | 控制文本的排列方向（从左到右或从右到左）        |
| `mainAxisSize`       | 控制 `Row` 小部件的大小如何与其子元素的尺寸适配 |
| `verticalDirection`  | 控制 `Row` 小部件中文本排列的垂直方向           |
| `textBaseline`       | 控制基准线对齐，通常在文本和图标混排时使用      |

### 





## Column

`Column` 是一个用于垂直排列子元素的布局小部件。它按顺序将其子组件沿垂直方向排列

```dart
Column(
             children: <Widget>[
              Container(
                color: Colors.red,
                width: 100,
                height: 100,
              ),
              Container(
                color: Colors.green,
                width: 100,
                height: 100,
              ),
              Container(
                color: Colors.blue,
                width: 100,
                height: 100,
              ),
            ],
          )
```

| 属性                 | 说明                                               |
| -------------------- | -------------------------------------------------- |
| `mainAxisAlignment`  | 控制子元素在主轴（垂直方向）上的对齐方式           |
| `crossAxisAlignment` | 控制子元素在交叉轴（水平方向）上的对齐方式         |
| `textDirection`      | 控制文本的排列方向（从左到右或从右到左）           |
| `mainAxisSize`       | 控制 `Column` 小部件的大小如何与其子元素的尺寸适配 |
| `verticalDirection`  | 控制 `Column` 小部件中文本排列的垂直方向           |
| `textBaseline`       | 控制基准线对齐，通常在文本和图标混排时使用         |

### 

## MainAxisAlignment

![](layout-0.png)



## crossAxisAlignment

![](layout-1.png)

<warning>CrossAxisAlignment.baselin为基于基线对齐，设置该属性必须设置属性textBaseline</warning>