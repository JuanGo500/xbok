# Flame

## Instalación
Specify dependency in  pubspec.yaml>dependencies:
flame: ^1.0.0

The latest version can be found on pub.dev.

## Estructura de un juego

1. Importación de librerías
```dart
import 'package:flame/components.dart';
import 'package:flame/game.dart';
import 'package:flame/input.dart';
import 'package:flutter/widgets.dart';
import 'package:flutter/material.dart';
```
2. Se crea la clase del juego que contiene
- un futuro para la carga donde se añade el componente Player
- métodos para controlar los gestos

```dart
class BasketSally extends FlameGame with TapDetector {
  late final PlayerComponent player;

  @override
  Future<void>? onLoad() async {
    await super.onLoad();

    add(player = PlayerComponent()
      ..width = 100
      ..height = 100);
  }

  @override
  void onTapDown(TapDownInfo info) {
    player.jump();
  }
}
```
3. Se crea la clase para la pantalla
```dart
class GameScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return GameWidget(game: BasketSally());
  }
}
```



class PlayerComponent extends PositionComponent {
  static Paint _paint = Paint()..color = Colors.red;
  Vector2 velocity = Vector2.zero();
  static Vector2 gravity = Vector2(0, 20);

  @override
  void render(Canvas canvas) {
    super.render(canvas);
    canvas.drawRect(size.toRect(), _paint);
  }

  @override
  void update(double dt) {
    super.update(dt);
    position += velocity * dt - gravity * dt * dt / 2;
    velocity += gravity * dt;
    
  }

  void jump() {
    velocity += Vector2(0, -50);
    
  }
}





## References
https://pub.dev/packages/flame

https://jap.alekhin.io/create-mobile-game-flutter-flame-beginner-tutorial

https://blog.geekyants.com/building-a-2d-game-in-flutter-a-comprehensive-guide-913f647846bc

Construir un juego con los creadores de Flame
https://www.youtube.com/watch?v=J3ZZyzKS-rg

Desarrollo de un juego básico con colisión (Marines)
https://www.youtube.com/watch?v=SNQVYyBLIO4

Repo con ejemplo Crates, incluye renderizado de texto
https://github.com/flame-engine/flame-crates-example/blob/master/tutorial/article.md