# Troubleshooting

## No se puede instalar la aplicación de prueba
No se puede instalar aplicación de prueba desde Google Play después de haber desinstalado del teléfono la aplicación de prueba anterior.
El error es: "No se puede instalar esta aplicación porque otro usuario ya ha instalado una versión no compatible con este dispositivo".

Teléfono: Redmi 8
Versión Android: 10 QKQ1.191014.001

Posible solución: con el teléfono conectado
``` adb shell pm uninstall com.packagename```

