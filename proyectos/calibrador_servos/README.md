# Proyecto: calibrador seguro de servos

## Objetivo

Crear una ruta de pruebas para calibrar servos SG90 sin forzar limites mecanicos ni alimentar servos desde el microcontrolador.

## Componentes relacionados

| ID | Componente | Uso |
|---|---|---|
| `ACT-001` | Servo Tower Pro SG90 | actuador principal |
| `DRV-002` | PCA9685 16 canales | generador PWM para varios servos |
| `MCU-001` | Arduino Nano | controlador inicial recomendado |
| `MCU-002` / `MCU-003` | ESP32 | controlador futuro con logica 3.3 V |
| `MAT-004` | Cable siliconado | cableado de potencia |
| `HTL-001` | Multimetro digital | verificacion de alimentacion |

## Reglas de seguridad

- Usar fuente externa para servos.
- Mantener GND comun entre controlador, PCA9685 y fuente de servos.
- No alimentar varios servos desde USB del microcontrolador.
- Iniciar cada servo en 90 grados.
- Mover en pasos pequenos y registrar limites.
- Bloquear por software cualquier valor fuera de limite validado.

## Flujo inicial

1. Probar un solo SG90 con fuente 5 V externa.
2. Confirmar cableado: marron/negro GND, rojo V+, amarillo/naranja senal.
3. Configurar PCA9685 con VCC logica y V+ de servos separados.
4. Mover de 90 grados hacia minimo y maximo por pasos.
5. Registrar limite minimo, maximo y direccion normal/invertida.

## Entregables pendientes

- Tabla de calibracion por servo.
- Sketch inicial Arduino.
- Prueba de PCA9685 con un servo.
- Criterio para detectar atasco mecanico.
