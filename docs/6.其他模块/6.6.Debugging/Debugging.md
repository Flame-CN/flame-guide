# Debug 功能

## FPS计数器
Flame 提供了一个混合 `FPSCounter` 用于记录fps, 可应用于 `Game` 的扩展类中。
使用时我们要实现 `recordFps` 方法,如果我们要访问当前fps,此方法需要返回 `true`。 

```dart
class MyGame extends Game with FPS {
  @override
  bool recordFps() => true;
}
```

## BaseGame 功能

Flame为调试提供了一些功能，这些功能都是通过重写BaseGame类的方法并返回 `true` 来启用调试模式。当启用时，它的所有 `PositionComponent` 将包装到一个矩形，并将其位置呈现在屏幕上，这样可以直观地验证组件边界和位置。

这里有一些BaseGame调试功能的例子[点击示例](https://github.com/flame-engine/flame/tree/master/doc/examples/debug)
