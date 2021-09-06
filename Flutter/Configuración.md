# Configuración

## Instalación
Descargar el fichero comprimido y descomprimirlo en una carpeta

```
cd ~/development
unzip ~/Downloads/

flutter_macos_1.22.6-stable.zip
```
```
 export PATH="$PATH:`pwd`/flutter/bin"
```

Actualizar la ruta en fichero
Users\Juan\.bash_profile

```
export PATH="$PATH:/Users/Juan/Development/flutter/bin"
```
## Configurar para la web
flutter config --enable-web


## Errores Configuración

### Cambio de proyecto entre Mac y Linux

Da errores

- No reconoce el import package flutter. Se ejecuta 'flutter pub get'
- No deja hacer el debug. Se ejecuta 'flutter clean'

### Versión mínima

A veces el build pide actualizar la versión mínima

You have to edit the build.gradle file. In a flutter project, it is found at the path ./android/app/build.gradle.

The parameter that needs to be changed is, of course, minSdkVersion 16, bumping it up to what you need (in this case 19).

defaultConfig {
    // TODO: Specify your own unique Application ID (https://developer.android.com/studio/build/application-id.html).
    applicationId "com.example.projectname"
    minSdkVersion 19 //*** This is the part that needs to be changed, previously was 16
    targetSdkVersion 28
    versionCode 1
    versionName "1.0"
    testInstrumentationRunner "android.support.test.runner.AndroidJUnitRunner"
}
