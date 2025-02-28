# 大屏幕适配

在 Flutter 中，适配 [大屏设备](https://m3.material.io/foundations/layout/applying-layout/window-size-classes)（如平板、折叠屏、桌面应用等）需要特别注意布局的响应式设计和屏幕空间的合理利用

- 使用 GridView 代理ListView

```dart
import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  var _list = [     Image.asset("resource/p2.png",height: 100,fit: BoxFit.contain,),
    Image.asset("resource/p3.png",height: 100,fit: BoxFit.contain),
    Image.asset("resource/p4.png",height: 100,fit: BoxFit.contain)];


  int _getCount(BuildContext context) {
    if(MediaQuery.sizeOf(context).width < 600){
      return 1;
    }
    return 2;
  }


  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(
          title: Text('Catalog'),
          actions: [
            IconButton(
              icon: Icon(Icons.cabin),
              onPressed: () {},
            ),
            IconButton(
              icon: Icon(Icons.edit),
              onPressed: () {},
            )
          ],
          toolbarHeight: 80,
        ),
        body: SafeArea(
          child: GridView.builder(
              padding: EdgeInsets.all(0),
              addRepaintBoundaries: false,
              gridDelegate: SliverGridDelegateWithFixedCrossAxisCount(
                crossAxisSpacing: 0, // 水平间距
                mainAxisSpacing: 0, // 垂直间距
                crossAxisCount: _getCount(context), // 每行显示两个子项
              ),
              itemCount: 3, // 数据的数量
              itemBuilder: (context, index) {
                return FittedBox(fit: BoxFit.contain,
                  alignment: Alignment.topLeft,
                  clipBehavior: Clip.antiAlias,
                 child: _list[index],
                );

              },

          )
        ),
        bottomNavigationBar: BottomNavigationBar(
          items: [
            BottomNavigationBarItem(icon: Icon(Icons.home), label: '首页'),
            BottomNavigationBarItem(icon: Icon(Icons.search), label: '搜索'),
          ],
        ),
      ),

    );


  }
}

```



## 视觉密度

`VisualDensity` 允许调整组件的大小、间距和触摸目标，以适应不同的设计需求或用户偏好。`VisualDensity` 通常用于 Material 组件（如按钮、输入框等），以提供更紧凑或更宽松的布局

| 属性         | 说明                                                   |
| :----------- | :----------------------------------------------------- |
| `horizontal` | 控制水平方向上的密度（负值表示更紧凑，正值表示更宽松） |
| `vertical`   | 控制垂直方向上的密度（负值表示更紧凑，正值表示更宽松） |

- **`VisualDensity.standard`**

默认密度（水平和垂直均为 0）

- **`VisualDensity.compact`**

紧凑密度（水平和垂直均为 -4.0）

- **`VisualDensity.comfortable`**

宽松密度（水平和垂直均为 4.0）

- **`VisualDability.adaptivePlatformDensity`**

根据平台自动调整密度（例如，Android 更紧凑，iOS 更宽松）

- 全局设置

```dart
MaterialApp(
  theme: ThemeData(
    visualDensity: VisualDensity.adaptivePlatformDensity, // 根据平台自动调整
  ),
  home: MyHomePage(),
);
```

- 局部设置

```dart
class MyHomePage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('VisualDensity 示例'),
      ),
      body: Center(
        child: ElevatedButton(
          style: ElevatedButton.styleFrom(
            visualDensity: VisualDensity.compact, // 紧凑布局
          ),
          onPressed: () {},
          child: Text('紧凑按钮'),
        ),
      ),
    );
  }
}
```

