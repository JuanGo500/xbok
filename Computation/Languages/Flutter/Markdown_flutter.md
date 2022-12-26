# Uso de markdown en Flutter

## 1. Añadir la dependencia

Buscar la dependencia
https://pub.dev/packages/flutter_markdown

Añadirla
```
dependencies:
  flutter:
    sdk: flutter
    
  webview_flutter: ^1.0.7
  cupertino_icons: ^1.0.0
  flutter_markdown: ^0.5.1
  ```

## Cargar el markdown en un widget

- Importarla en el fichero

```
 'package:flutter_markdown/flutter_markdown.dart';
```

- Crear una función asíncrona
 
 ```dart
 @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Simple Markdown Demo'),
      ),
      body: FutureBuilder(
          future: rootBundle.loadString("assets/prueba.md"),
          builder: (BuildContext context, AsyncSnapshot<String> snapshot) {
            if (snapshot.hasData) {
              return Markdown(data: snapshot.data);
            }

            return Center(
              child: CircularProgressIndicator(),
            );
          }),
    );
  }
}
```

## Referencias

Paso a paso

https://developer.school/how-to-display-markdown-in-flutter/