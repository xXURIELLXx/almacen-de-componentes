# Proyecto: nodo IoT ambiental

## Objetivo

Crear un nodo de medicion ambiental con ESP32 para aprender sensores, pantalla, eventos y comunicacion.

## Componentes sugeridos

- ESP32 ESP-WROOM-32 o ESP32-C3.
- AHT10.
- DHT11 o DHT22 como comparativo.
- HC-SR501 para presencia.
- TFT SPI 1.8 para lectura local.
- Modulo touch como entrada simple.

## Fases

1. Leer temperatura y humedad por I2C.
2. Mostrar datos por monitor serial.
3. Mostrar datos en TFT.
4. Agregar deteccion de movimiento.
5. Enviar datos por WiFi.
6. Registrar eventos para analisis posterior.

## Aplicaciones

- Terrario automatizado.
- Cuarto seco de filamento.
- Monitor ambiental de habitacion.
- Base para agente fisico IoT.
