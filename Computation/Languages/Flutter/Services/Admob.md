# Admob

## Instalación

### 1. Añadir dependencia

```
dependencies:
  google_mobile_ads: ^0.11.0+3
  provider: ^5.0.0


```

### 2. Añadir app id
android/app/src/main/AndroidManifest.xml

```
<manifest>
    <application>
        <!-- Sample AdMob app ID: ca-app-pub-3940256099942544~3347511713 -->
        <meta-data
            android:name="com.google.android.gms.ads.APPLICATION_ID"
            android:value="ca-app-pub-xxxxxxxxxxxxxxxx~yyyyyyyyyy"/>
    <application>
<manifest>
```

## Inicialización

> import 'package:google_mobile_ads/google_mobile_ads.dart';

void main() async {
  WidgetsFlutterBinding.ensureInitialized();
  final initFuture = MobileAds.instance.initialize();
  final adState = AdState(initFuture);
  runApp(
    Provider.value(
      value: adState,
      builder: (context, child) => MyApp(),
    ),
  );
}



Antes de cargar anuncios, haz que tu aplicación inicialice el SDK de anuncios para móviles mediante una llamada a MobileAds.instance.initialize(). Esta acción inicializa el SDK y devuelve un Future que finaliza cuando se completa la inicialización (o tras un tiempo de espera de 30 segundos). Solo es necesario hacerlo una vez, preferiblemente antes de ejecutar la aplicación.

```
void main() {
  WidgetsFlutterBinding.ensureInitialized();
  final initFuture=MobileAds.instance.initialize();

  runApp(MyApp());
}
``` 
## Anuncio en cada página

### Crear una variable en el estado

```
BannerAd banner;

void didChangeDependencies() {
    super.didChangeDependencies();
    final adState = Provider.of<AdState>(context);

    adState.initialization.then(
      (status) {
        setState(
          () {
            banner = BannerAd(
              adUnitId: adState.bannerAdUnitId,
              size: AdSize.banner,
              request: AdRequest(),
              listener: adState.adListener,
            )..load();
          },
        );
      },
    );
  }
//mostrar el anuncio
  if (banner == null)
      //       SizedBox(height: 50)
      //     else
      //       Container(height: 50, child: AdWidget(ad: banner)),
  ```

## Problemas
Según la versión de google_mobile_ads, pueden surgir problemas con Gradle.

Si hay que actualizar la versión de Gradle 
android/gradle/wrapper/gradle-wrapper.properties

en la línea
distributionUrl=https\://services.gradle.org/distributions/gradle-6.5-all.zip

Si se copia el fichero directamente de otro proyecto, puede haber problemas de dependencias

Bloques de anuncios de prueba Android
https://developers.google.com/admob/android/test-ads#sample_ad_units

Bloques de anuncios de prueba IOS
https://developers.google.com/admob/ios/test-ads


https://developers.google.com/admob/flutter/quick-start

https://pub.dev/packages/google_mobile_ads

Vídeo
https://flutter.dev/ads