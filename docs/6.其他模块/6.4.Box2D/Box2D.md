# Box2D
尽管Flame本身并未实现Box2d，但它将Java Box2d的分支移植捆绑到了Google的Dart中。

可以在 [此处](https://github.com/flame-engine/box2d.dart) 找到Flame上捆绑的Box2D的来源。

有一个简单的示例游戏 [此处](https://github.com/feroult/haunt) ，可作为如何在Flame上使用Box2D的参考，尽管它有些过时并且不使用 `Box2DGame`。

这里有一些更新的使用方法示例 [此处](https://github.com/flame-engine/flame/blob/master/doc/examples/box2d) ，但它们并不是完整的游戏实现。

## BaseGame扩展
如果您要在项目中使用Box2D，则最好使用基于 `BaseGame` 扩展的Box2D类。

它被称为 `Box2DGame` ，它将在组件根目录 `Box2DComponent` 中控制添加与删除 Box2D 组件

一个简单的 `Box2DGame` 实现示例 [此处](https://github.com/flame-engine/flame/tree/master/doc/examples/box2d/simple)

## 通信回调
如果您使用的是 `Box2DGame` ，则可以利用其处理两个 `BodyComponent` 之间的通信。

当您为 `BodyComponent` 创建主体定义时，请确保将userdata设置为当前对象，否则将无法检测到碰撞。
像这样:
```dart
final bodyDef = BodyDef()
  // To be able to determine object in collision
  ..setUserData(this);
```
现在你需要设置这两种类型，当他们接触  `ContactCallback`  时的实现。

如果您有两个名为Ball和Wall的 `BodyComponent` ，并且想在他们通信时采取某些措施，您会这样做：

```dart
class BallWallCallback implements ContactCallback<Ball, Wall> {
  BallWallCallback();

  @override
  void begin(Ball ball, Wall wall, Contact contact) {
    wall.remove();
  }

  @override
  void end(Ball ball, Wall wall, Contact contact) {}
}
```
然后只需将 `BallWallCallback` 添加到 `Box2DGame` 中：

```dart
class MyGame extends Box2DGame {
  MyGame(Box2DComponent box) : super(box) {
    addContactCallback(BallWallCallback());
  }
}
```
每当 `Ball` 和 `Wall` 接触时，`begin` 都会被调用，一旦对象停止接触，`end` 将被调用。

如果您希望对象与所有其他物体进行交互，则将 `BodyComponent` 作为 `ContactCallback` 的参数，如下所示：

`class BallAnythingCallback implements ContactCallback<Ball, BodyComponent> ...`

这里有一个实现示例 [此处](https://github.com/flame-engine/flame/blob/master/doc/examples/box2d/contact_callbacks)
