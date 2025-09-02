# 启动页



## 导入

```yaml
dependencies:
  flutter_native_splash: ^2.4.6
```



## 配置

```yaml
flutter_native_splash:
  color: "#ffffff"              
  image: resource/images/common/logo.png
  android: true
  ios: true
  web: false
```



| 配置项             | 说明                                                        |
| ------------------ | ----------------------------------------------------------- |
| `color`            | 启动画面的背景颜色                                          |
| `background_image` | 设置整张背景图（通常不用，适配麻烦）                        |
| `image`            | 居中的主 Logo 图                                            |
| `branding`         | 底部的商标图                                                |
| `fullscreen`       | 是否全屏显示（true/false）                                  |
| `android`          | 是否生成 Android 配置                                       |
| `ios`              | 是否生成 iOS 配置                                           |
| `android_12`       | 针对 Android 12+ 需要单独配置（因为 Google 改了启动页样式） |

<warning>
   Android 12 的图标需要单独配置，且会被裁剪成圆形
</warning>

## 命令

- 运行

```bash
flutter pub run flutter_native_splash:create
```



- 清理

```bash
flutter pub run flutter_native_splash:remove
```

