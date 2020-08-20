# 循环BGM
TODO

通过使用`Bgm`类，你可以管理游戏（App）的生命周期或者控制背景音乐的循环。

当App暂停、停止或者切换至后台时，`Bgm`类将会自动暂停当前播放的音乐。同样，App恢复后，`Bgm`将会同时恢复背景音乐的播放。并且支持手动暂停/恢复。

你需要通过以下代码来注册该监听器：
```dart
Flame.bgm.initialize();
```

> 注意：调用`initialize()`前，你需要确保`WidgetsBinding`实例已经存在。可以确定的是，在至少调用一次runApp后没有问题。

如果你不需要处理背景音乐，但是希望游戏（App）继续正常运行，可以通过`dispose`函数来删除监听器。
```dart
Flame.bgm.dispose();
```

输入以下代码以循环播放背景音乐：
```dart
import 'package:flame/flame.dart';

Flame.bgm.play('adventure-track.mp3');
```

或者：
```dart
import 'package:flame/bgm.dart';

Bgm audio = Bgm();
audio.play('adventure-track.mp3');
```

> 注意：`Bgm`类将始终使用`Flame.audio`中的`FlameAudio`静态变量来存储缓存的音乐文件。

你需要保证你的目录结构正确，并且将文件添加在`pubspec.yaml`中，如[音频处理文档](../4.1常见音频处理/常见音频处理.md)所述。

## 缓存音乐文件
以下函数可用于将音乐文件预加载（或取消加载）到缓存中。这些函数只是`Flame.audio`中具有相同名称的功能的别名。
```dart
Flame.audio.load('adventure-track.mp3');
Flame.audio.loadAll([
  'menu.mp3',
  'dungeon.mp3',
]);
Flame.audio.clear('adventure-track.mp3');
Flame.bgm.clearAll();
```
同样的，请查看[音频处理文档](../4.1常见音频处理/常见音频处理.md)获取更多信息。

## 可用函数
### 播放 Play
`Play`函数接收一个字符串，该字符串为你要播放的音乐文件的文件名。（确保你的目录结构符合Flame Audio规范）

你可以传入类型为double的额外参数，即`volume`音量（默认为`1.0`）.

比如：
```dart
Flame.bgm.play('bgm/boss-fight/level-382.mp3');
```
```dart
Flame.bgm.play('bgm/world-map.mp3', volume: .25);
```

### 停止 Stop
通过调用`stop`直接停止播放背景音乐。
```dart
Flame.bgm.stop();
```

### 暂停/恢复 Pause/Resume
可以使用`pause`和`resume`函数以手动 暂停/恢复 播放背景音乐。

`Flame.bgm`会自动处理暂停/恢复当前正在播放的背景音乐。手动暂停后，游戏（App）恢复后将不会自动播放。

```dart
Flame.bgm.pause();
```
```dart
Flame.bgm.resume();
```