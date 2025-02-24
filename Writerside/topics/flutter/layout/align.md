# 对齐方式



## AlignmentGeometry

`AlignmentGeometry`是一个用于表示偏移位置的抽象类，它的具体实现类 `Alignment` 和 `AlignmentDirectional` 分别用于不同的场景



## Alignment

`Alignment` 用于表示与文本方向无关的偏移位置，表示矩形内的一个点，以矩形的中心为原点。它定义了一个坐标系，其中水平方向的范围是从 -1.0 到 1.0，垂直方向的范围也是从 -1.0 到 1.0。这个坐标系的中心点是 `Alignment(0.0, 0.0)`，表示矩形的中心



![](layout-2.png)



## FractionalOffset

`FractionalOffset`用来表示一个相对位置的类，它通过一个 **浮动比例** 来表示在一个矩形区域内的对齐位置

<warning>不建议使用</warning>



## AlignmentDirectional

`AlignmentDirectional` 用于处理 **从右向左（RTL）** 语言支持的布局。在支持 RTL 的环境中（如阿拉伯语或希伯来语等语言），文本和布局的方向会发生变化，`AlignmentDirectional` 通过自动调整子部件的位置来处理这一需求