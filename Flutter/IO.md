# IO 

## Orientación

Para restringir la orientación:
- importar servicios
import 'package:flutter/services.dart';

- restringir en main()
ystemChrome.setPreferredOrientations(
      [DeviceOrientation.portraitUp, DeviceOrientation.portraitDown]);
 