# Tiled

[Tiled](https://www.mapeditor.org/) 是一个用于设计平铺地图很棒的工具。

Flame 提供了一个给予 [dart package](https://pub.dev/packages/tiled) 的包 [flame_tiled](https://github.com/flame-engine/flame_tiled) , 允许您访问并解析 tmx (xml) 文件中的所有内容。

Flame 还为地图渲染提供了一个简单的 `Tiled` 类及其组件包 `TiledComponent`，用于在屏幕上进行地图渲染，平铺，旋转，翻转。

其他高级功能尚未支持，但您可以轻松地阅读tmx的对象和其他功能，并添加自定义行为(例如触发区域或行走地区，可自定义动画对象)。

这里有个例子，你可以点击查看[示例](https://github.com/flame-engine/flame_tiled/tree/master/example)