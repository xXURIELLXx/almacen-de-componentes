# Seguridad de alimentacion

Este archivo define reglas minimas antes de conectar componentes.

## Lineas de voltaje

- 3.3 V: ESP32, NRF24L01, sensores I2C delicados.
- 5 V: Arduino Nano, algunos sensores, servos pequenos y modulos de entrada.
- 12 V: bateria sellada, cargas de potencia y pruebas especificas.
- LiPo 1S: baterias de 3.7 V nominal y 4.2 V cargadas.

## Reglas principales

1. No alimento motores, servos ni LEDs de potencia desde un GPIO.
2. Mantengo tierra comun entre controlador y fuente externa cuando controle servos o drivers.
3. No conecto senales de 5 V a GPIO de ESP32.
4. Al NRF24L01 le doy 3.3 V estable y capacitor cercano.
5. El TP4056 se usa solo para una celda de litio 1S.
6. La bateria sellada de 12 V no se carga con TP4056.
7. Antes de usar placas recuperadas, valido polaridad, continuidad y consumo con corriente limitada.

## Riesgos conocidos

- Servos SG90: pueden danarse por sobreesfuerzo mecanico, fuente debil o limites incorrectos.
- Placas de dron: no energizar hasta identificar bateria original y chips principales.
- LED IR de 3 W: requiere control de potencia; no usar GPIO directo.
- Modulos boost: ajustar la salida antes de conectar cualquier carga.
