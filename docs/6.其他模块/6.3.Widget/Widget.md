# Widgets

当使用 Flutter 开发游戏时， Flutter 工具集能够构建一个很酷UI，Flame 试图扩展这一功能，引入专门为游戏而设计的部件。

在这里，您可以找到Flame提供的所有可用部件。

您还可以在此查看 [Dashbook](https://github.com/erickzanardo/dashbook) 和 [此处](https://github.com/flame-engine/flame/blob/master/doc/examples/widgets) 内展示的所有部件

## 九宫格
九宫格是使用网格精灵绘制的矩形。

网格精灵是一个3x3网格，总有9个格，分别代表4个角格，4个边格和中间格。

拐角以相同的大小绘制，侧面在侧面方向上拉伸，中间部分双向扩展。

`NineTileBox` 部件是使用该标准实现了一个容器。 此模式在游戏中由 `NineTileBoxComponent` 实现，您可以在其中使用相同的功能，可以直接在游戏 Canvas 中使用，要了解更多信息，请查看组件文档 [此处](https://github.com/flame-engine/flame/blob/master/doc/components.md#nine-tile-box-component) 。

用法示例:

```dart
import 'package:flame/widgets/nine_tile_box.dart';

NineTileBox(
    image: image, // dart:ui image 实例
    tileSize: 16, // 网格图像上图块的宽度/高度
    destTileSize: 50, // 在画布上绘制图块时要使用的尺寸
    child: SomeWidget(), // 任何Flutter部件
)
```

## SpriteButton
`SpriteButton` 是一个简单的部件，可以基于Flame精灵创建一个按钮。 尝试创建具有复古外观的按钮时，这可能非常有用。 例如，通过在绘图软件中绘制按钮而不是直接在Flutter中创建按钮，可以更轻松地创建外观。

请记住，将Sprites传递到部件时必须确保已经加载了它们。

如何使用它:
```dart
SpriteButton(
    onPressed: () {
        print('Pressed');
    },
    label: const Text('Sprite Button', style: const TextStyle(color: const Color(0xFF5D275D))),
    sprite: _spriteButton,
    pressedSprite: _pressedSpriteButton,
)
```
## SpriteWidget
`SpriteWidget` 用于在部件树中显示 [Sprites](https://github.com/flame-engine/flame/blob/master/lib/sprite.dart) 的部件。

如何使用它:
```dart
SpriteWidget(
    sprite: shieldSprite,
    center: true,
),

```
## AnimationWidget

`AnimationWidget` 用于在部件树中显示 [Animations](https://github.com/flame-engine/flame/blob/master/lib/animation.dart) 的部件。

如何使用它:
```dart
AnimationWidget(
    animation: _animation,
    playing: true,
    center: true,
),
```
