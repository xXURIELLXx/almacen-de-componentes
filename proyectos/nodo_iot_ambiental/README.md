# Proyecto: nodo IoT ambiental

## Objetivo

Construir una ruta de pruebas para un nodo ambiental con ESP32, sensores de temperatura/humedad, PIR y pantalla TFT, manteniendo niveles logicos seguros.

## Componentes relacionados

| ID | Componente | Uso |
|---|---|---|
| `MCU-002` | ESP32 Super Mini | controlador IoT compacto |
| `MCU-003` | Live mini kit ESP32 | controlador IoT alternativo |
| `SEN-001` | DHT11/DHT22 | temperatura y humedad |
| `SEN-003` | PIR HC-SR501 | presencia/movimiento |
| `SEN-004` | AHT10 | temperatura y humedad por I2C |
| `DISP-001` | TFT SPI 1.8 128x160 | interfaz local |
| `PWR-002` | TP4056 | energia LiPo 1S futura, solo con validacion |

## Reglas de seguridad

- Tratar GPIO ESP32 como 3.3 V.
- No conectar senales de 5 V directo a GPIO ESP32.
- Validar si cada modulo acepta 3.3 V o requiere adaptacion.
- No usar TP4056 con bateria 12 V.
- Medir 3.3 V y 5 V antes de conectar perifericos.

## Flujo inicial

1. Identificar la placa ESP32 real y su pinout.
2. Cargar Blink o prueba USB sin sensores.
3. Probar I2C con AHT10 si esta disponible.
4. Probar DHT por separado.
5. Probar PIR por separado y confirmar nivel de salida.
6. Probar TFT SPI despues de validar jumper/logica.
7. Integrar sensores uno por uno.

## Entregables pendientes

- Pinout elegido para la placa ESP32 real.
- Sketch de lectura AHT10/DHT.
- Prueba de PIR con registro serial.
- Prueba de TFT con texto basico.
- Diagrama de alimentacion.
