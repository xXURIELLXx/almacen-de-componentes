# Conexiones iniciales recomendadas

## Arduino Nano con servo SG90

- Servo rojo a fuente externa de 5 V.
- Servo marron a tierra de fuente externa.
- Servo amarillo a pin PWM del Arduino.
- Tierra de fuente externa unida a GND del Arduino.

## ESP32 con AHT10

- VIN del AHT10 a 3.3 V o a VIN si el modulo lo permite.
- GND a GND.
- SCL a pin I2C SCL definido en software.
- SDA a pin I2C SDA definido en software.

## ESP32 con HC-SR501

- VCC del PIR a 5 V.
- GND a GND comun.
- OUT a entrada digital del ESP32.
- Validar que la salida sea de 3.3 V antes de conectar.

## Arduino o ESP32 con PCA9685

- SDA y SCL al bus I2C.
- VCC del modulo a tension logica compatible.
- V+ a fuente externa de servos.
- GND comun entre microcontrolador y fuente de servos.

## NRF24L01

- VCC a 3.3 V estable.
- GND a GND.
- SCK, MOSI, MISO al bus SPI.
- CE y CSN a pines digitales definidos por software.
- Colocar capacitor cercano entre alimentacion y tierra.

## Motores DC

No conectar directo al microcontrolador. Usar L298, MOSFET o driver adecuado. Primero medir corriente sin carga y despues con carga.
