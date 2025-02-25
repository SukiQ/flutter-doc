# 图像



## Image

`Image`用来显示各种类型的图片

- `Image.asset` 加载本地资源图片

```yaml
flutter:
  assets:
    - assets/images/my_image.png
```

```dart
Image.asset('assets/images/my_image.png')
```



- `Image.network` 加载网络图片

```dart
Image.network('https://example.com/my_image.jpg')
```



- `Image.file` 加载本地文件图片

```dart
Image.file(File('path/to/your/image.png'))
```



- `Image.memory` 加载内存中的图片

如果你有一个 `Uint8List`（通常是通过网络请求下载的图片数据），可以通过 `Image.memory` 来加载图片

```dart
Image.memory(Uint8List data)
```

### 

| 属性              | 说明                                                         |
| ----------------- | ------------------------------------------------------------ |
| `width`           | 设置图片的宽度                                               |
| `height`          | 设置图片的高度                                               |
| `fit`             | 图片适应容器的方式<br/>`BoxFit.contain`: 保持宽高比，确保子组件完全显示在父组件内<br/>`BoxFit.cover`: 保持宽高比，确保子组件覆盖父组件，可能会裁剪内容<br/>`BoxFit.fill`: 拉伸子组件以填充父组件，不保持宽高比<br/>`BoxFit.fitWidth`: 保持宽高比，确保宽度匹配父组件<br/>`BoxFit.fitHeight`: 保持宽高比，确保高度匹配父组件<br/>`BoxFit.scaleDown`: 如果子组件比父组件大，则缩小子组件；否则保持原尺寸<br/>`BoxFit.none`: 不进行任何缩放，子组件按原始尺寸显示 |
| `alignment`       | 设置图片在容器中的对齐方式                                   |
| `color`           | 给图片添加颜色滤镜                                           |
| `colorBlendMode`  | 设置颜色滤镜的混合模式                                       |
| `repeat`          | 图片重复方式<br/>`ImageRepeat.noRepeat`: 图片不重复，只显示一次<br/>`ImageRepeat.repeat`: 图片水平和垂直方向都重复<br/>`ImageRepeat.repeatX`: 图片只在水平方向上重复<br/>`ImageRepeat.repeatY`: 图片只在垂直方向上重复 |
| `semanticLabel`   | 为屏幕阅读器提供的语义标签，帮助辅助功能                     |
| `isAntiAlias`     | 是否启用抗锯齿效果                                           |
| `filterQuality`   | 控制图片的质量<br/>`FilterQuality.low`: 低质量<br/>`FilterQuality.medium`: 中等质量<br/>`FilterQuality.high`: 高质量 |
| `frameBuilder`    | 自定义构建图像帧的方法，通常用于控制图片的显示效果           |
| `loadingBuilder`  | 自定义图片加载过程中的构建方法                               |
| `gaplessPlayback` | 是否支持无间隙播放图像，适用于动画图像                       |
| `cacheWidth`      | 设置图片缓存的宽度，通常用于优化性能                         |
| `cacheHeight`     | 设置图片缓存的高度                                           |