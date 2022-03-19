# Publicar Google Play

## Pasos publicación

### 1.Crear una Keystore

```
keytool -genkey -v -keystore ~/key.jks -keyalg RSA -keysize 2048 -validity 10000 -alias key
```

Contraseña key: xandair
Contraseña keystore: xandair

¿Es correcto CN=Juan Serantes, OU=Ventas, O=IntelligentConta, L=Barcelona, ST=Barcelona, C=ES?

> Recuperar el contenido
> keytool -v -list -keystore key.jks

### 2.Crear key.properties
Para cada aplicación se debe crear un archivo llamado key.properties donde se guardan las claves para firmar la aplicación.

Se crea en <app dir>/android/key.properties
Se pondrá junto a las key.properties

```
storePassword=password
keyPassword=password
keyAlias=key
storeFile=location of the key store file, such as Users/<user name>/key.jks
```

- se pone sin comillas
- en Mac funciona con / inicial p.ej. Users/Juan/key.jks

Por ejemplo, para el keystore actual en Mac será:

storePassword=xandair
keyPassword=xandair
keyAlias=key
storeFile=/Users/Juan/key.jks


### 3.Actualizar build.gradle

<app dir>/android/app/build.gradle

- Añadir antes de el bloque android

  ```
   def keystoreProperties = new Properties()
   def keystorePropertiesFile = rootProject.file('key.properties')
   if (keystorePropertiesFile.exists()) {
       keystoreProperties.load(new FileInputStream(keystorePropertiesFile))
   }

   android {
         ...
   }
```

Añadir antes de buildTypes. No hay que cambiar los valores.
 ```  
   signingConfigs {
       release {
           keyAlias keystoreProperties['keyAlias']
           keyPassword keystoreProperties['keyPassword']
           storeFile keystoreProperties['storeFile'] ? file(keystoreProperties['storeFile']) : null
           storePassword keystoreProperties['storePassword']
       }
   }
``` 

### 4.Sustituir el ID de applicación en todos los ficheros de la aplicación.
Se busca com.example.nombreAplicación y se sustituye example por intelligentconta

### 5.Hacer build
Se modifica el fichero build.gradle en 
> app>build.gradle

- Si se ejecuta en modo debug
> flutter run

```
buildTypes {
       release {
           signingConfig signingConfigs.debug
       }
   }
```

- Si se ejecuta en modo release 
> flutter build appbundle


```
buildTypes {
       release {
           signingConfig signingConfigs.release
       }
   }
```

## Launcher icon
Actualizar dependencias en pubspec.yaml
```
dev_dependencies:
  flutter_test:
    sdk: flutter
  flutter_launcher_icons: ^0.9.0
```
Con indentación igual, a continuación de dev dependencies

```
flutter_icons:
  android: "launcher_icon"
  ios: true
  image_path: "assets/icon.png"

```

En la lista de assets se pone el activo
```
assets:
  - icon.png
```

finalmente se genera el icono ejecutando
flutter pub run flutter_launcher_icons:main

## Sentencias

- Limpiar el caché
`flutter clean`

- Detectar API deprecadas
`dart fix --dry-run`


## Referencias

### Google Developers Console
https://developer.android.com/distribute/console

ID Desarrollador
4633874983350611531

### Build and release an Android App
https://flutter.dev/docs/deployment/android#adding-a-launcher-icon

### Generación de clave
https://developer.android.com/studio/publish/app-signing#generate-key


### Cuenta de google de desarrollador

https://play.google.com/console/u/0/signup