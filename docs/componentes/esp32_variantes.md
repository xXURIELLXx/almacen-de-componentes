# ESP32-S2 Mini / ESP8266 D1 Mini / D1 Mini ESP32

## Identificacion

- Componentes relacionados: placas ESP32-S2 Mini, ESP8266 D1 Mini y ESP32-WROOM-32 D1 Mini segun `PDF-003`.
- IDs de inventario relacionados: `MCU-002` ESP32 Super Mini y `MCU-003` Live mini kit ESP32.
- Fuente: `PDF-003`, referencia inicial de publicacion de venta.
- Advertencia principal: el PDF mezcla variantes; identificar chip real antes de cablear.

## Alimentacion y logica

| Variante | Datos extraidos | Estado |
|---|---|---|
| ESP8266 D1 Mini | 11 I/O, 1 ADC 0-3.3 V, IO 3.3 V, alimentacion 5 V en placa | referencia inicial |
| ESP32-S2 Mini | ESP32-S2FN4R2, USB-C, 4 MB Flash, 2 MB PSRAM, 27 I/O, ADC, DAC, I2C, SPI, UART, USB OTG | referencia inicial |
| D1 Mini ESP32-WROOM-32 | WiFi + Bluetooth, USB-C, CH9102, 31 x 39 mm | referencia inicial |
| ESP32-C3 Super Mini del inventario | 5 V por placa; logica 3.3 V | inventario |
| Live mini kit ESP32 del inventario | 5 V por placa; logica 3.3 V | inventario |

## Pines

Los pines dependen de la variante fisica. Antes de usar cualquier pin:

1. Identificar chip y serigrafia.
2. Comparar con pinout de la placa real.
3. Confirmar pines reservados de arranque, USB, flash o funciones especiales.
4. Tratar GPIO como logica 3.3 V.

## Uso inicial

1. Tomar foto frontal y posterior de la placa.
2. Identificar chip: ESP8266, ESP32-S2, ESP32-C3 o ESP32-WROOM-32.
3. Instalar driver USB si Windows no reconoce la placa.
4. Cargar Blink o escaneo I2C segun placa.
5. Solo despues conectar sensores externos.

## Riesgos

- GPIO no toleran 5 V.
- Pinout puede no coincidir con el titulo del PDF.
- Algunas placas tienen pines de arranque sensibles.
- No alimentar motores, servos ni LEDs de potencia desde GPIO.
- Validar salida de sensores de 5 V antes de conectar.

## Prueba recomendada

- Prueba USB sin perifericos.
- Blink en LED integrado si existe.
- Escaneo I2C con sensor conocido y alimentacion compatible.
- Medir 3.3 V del regulador antes de conectar sensores.

## Relacion con proyectos

- Nodo ambiental IoT.
- Comunicacion WiFi/Bluetooth.
- Control de sensores y actuadores mediante drivers.
- Interfaz de casco o pruebas portables, siempre separando potencia.

## Pendiente de validar

- Chip real de cada placa.
- Driver USB requerido.
- Pinout real de la variante disponible.
- Pines seguros para I2C, SPI, UART y PWM.
