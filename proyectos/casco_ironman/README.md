# Proyecto: casco Iron Man

## Objetivo

Definir una ruta tecnica segura para integrar servos, ojos LED, control tactil y audio en un casco/cosplay sin mezclar potencia con GPIO ni comprometer vision o seguridad.

## Componentes relacionados

| ID | Componente | Uso |
|---|---|---|
| `ACT-001` | Servos SG90 | mecanismo de apertura/cierre ligero |
| `DRV-002` | PCA9685 | control PWM de servos |
| `LED-002` | Ojos LED flexibles | iluminacion de ojos |
| `IN-002` | TTP223/HW-139 | entrada tactil |
| `PWR-002` | TP4056 | carga LiPo 1S si se valida alimentacion |
| `BAT-002` / `BAT-003` | LiPo 952540 | energia portable, pendiente de validacion |
| Amplificador Bluetooth 302T/LT21 | audio | potencia separada, pendiente de definir |

## Reglas de seguridad

- Probar ojos LED antes de cortar o pegar.
- No reducir vision de forma peligrosa.
- No alimentar servos desde GPIO ni desde el 5 V del microcontrolador.
- Usar fuente externa para servos y GND comun con el controlador.
- Separar audio de potencia de la logica del microcontrolador.
- No usar TP4056 con 12 V ni con celdas en serie.
- Validar peso, calor y puntos de pellizco del mecanismo.

## Flujo inicial

1. Medir huecos del casco y probar ojos LED fuera del casco.
2. Calibrar servos por separado con el proyecto `calibrador_servos`.
3. Probar TTP223 como boton tactil independiente.
4. Definir fuente de logica y fuente de servos.
5. Integrar mecanismo sin carga facial primero.
6. Evaluar audio solo cuando alimentacion y servos esten estables.

## Entregables pendientes

- Medidas reales del casco.
- Area segura de corte de ojos LED.
- Tabla de limites de servos.
- Diagrama de alimentacion separado por logica, servos, LEDs y audio.
- Prueba de seguridad visual.
