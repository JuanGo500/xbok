# Redes

## Sistema de capas

Modelo OSI (Open Interconnection Layer) 7 capas

Modelo simplificado (5 capas)
La comunicación entre redes se estructura en capas

- Física: señales eléctricas y cableado
- Enlace de datos: tarjetas de red, dirección MAC (todas tarjetas de red tienen una) 
- Red: ips, máscaras, router, LAN 
    - IP privada, pública
    - DNS traducción de URLs a IPs
- Transporte
- Aplicación


Túnel: comunicación de una red privada con una red privada a través de una red pública 
IP: número de 32 bits dividido en 4 bloques
Mascara: 32 bits con 1 a la izquierda y 0 a la derecha. El número de la máscara son los unos a la izquierda.
Por ejemplo: 1111111111110000 es una máscara 24
Si se hace una operación AND lógica con la IP del dispositivo obtenemos la IP de la red
NAT asocia IPs públicas con IPs privadas
