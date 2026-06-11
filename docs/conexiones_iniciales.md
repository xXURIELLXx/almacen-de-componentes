# Conexiones iniciales y reglas de prueba

Fecha: 2026-06-11

Este documento define una base de conexion segura para los componentes registrados. La idea es que una IA o una persona pueda iniciar pruebas sin revisar todo el historial del chat.

## Regla general

Antes de energizar cualquier modulo debo responder cuatro preguntas:

1. Que voltaje requiere.
2. Que corriente puede consumir.
3. Que pines son alimentacion, tierra y senal.
4. Que riesgo existe si se conecta mal.

Si alguna respuesta es desconocida, el componente queda en estado: pendiente de validacion.

## Lineas de alimentacion del laboratorio

| Linea | Uso | Componentes relacionados | Riesgo principal |
|---|---|---|---|
| 3.3 V | Logica ESP32, NRF24L01, sensores delicados | ESP32, NRF24L01, AHT10, MPU-6050 | No tolerar 5 V en GPIO |
| 5 V | Arduino Nano, sensores, servos pequenos | Arduino, TTP223, KY-037, SG90 | Corriente insuficiente desde USB |
| 12 V | Bateria sellada y cargas externas | BR-1201, audio, motores/LED con driver | Cortos y corrientes altas |
| LiPo 1S | Baterias 3.7 V | LiPo 952540, TP4056 | Sobrecarga, sobredescarga, polaridad invertida |

## Conexiones por modulo prioritario

### Arduino Nano

- 5V: alimentacion regulada de placa.
- VIN: entrada por regulador, usar solo si se conoce el rango del clon.
- GND: tierra comun.
- D2-D13: digitales.
- A0-A7: entradas analogicas.
- RX/TX: comunicacion serial.

Prueba inicial: Blink en LED integrado o LED externo con resistencia.

### ESP32 / ESP32-S2 / ESP32-C3

- Alimentacion por USB o pin 5V de la placa si tiene regulador.
- GPIO: logica 3.3 V.
- GND comun con sensores y drivers.

Regla: no conectar senales de 5 V directo a GPIO ESP32.

### NRF24L01

Pinout tipico:

| Pin | Funcion |
|---|---|
| VCC | 3.3 V estable |
| GND | Tierra |
| CE | Control RF |
| CSN | Chip select SPI |
| SCK | Reloj SPI |
| MOSI | Datos microcontrolador -> NRF |
| MISO | Datos NRF -> microcontrolador |
| IRQ | Interrupcion opcional |

Regla: usar capacitor cercano entre VCC y GND. En PA+LNA usar antena conectada antes de transmitir.

### Servo SG90

| Cable | Funcion |
|---|---|
| Marron/negro | GND |
| Rojo | 5 V externo |
| Amarillo/naranja | Senal PWM |

Regla: no alimentar varios servos desde el 5V del microcontrolador. Usar fuente externa y GND comun.

Secuencia segura:

1. Iniciar en 90 grados.
2. Mover en pasos pequenos.
3. Encontrar limite minimo.
4. Encontrar limite maximo.
5. Guardar direccion normal/invertida.
6. Bloquear software fuera de esos limites.

### PCA9685

- VCC: logica del controlador.
- GND: tierra comun.
- SDA/SCL: I2C.
- V+: alimentacion externa para servos.
- Canales 0-15: PWM, V+, GND por canal.

Regla: VCC y V+ no son lo mismo. V+ alimenta servos; VCC alimenta logica.

### TP4056

| Pin | Conexion |
|---|---|
| B+ | Positivo bateria LiPo/Li-ion 1S |
| B- | Negativo bateria |
| OUT+ | Positivo salida protegida |
| OUT- | Negativo salida protegida |
| USB | Entrada 5 V para carga |

Regla critica: solo usar con una celda de litio de 3.7 V nominal. No usar con bateria 12 V.

### TTP223 / HW-139

- VCC: 2.0 a 5.5 V.
- GND: tierra.
- SIG: salida digital.

Prueba inicial: leer SIG con Arduino/ESP32 y encender LED al tocar.

### KY-037 sensor de sonido

- VCC: 3.3-5 V segun modulo; iniciar con 5 V en Arduino.
- GND: tierra.
- OUT/DO: salida digital por umbral.
- AO: solo si la placa trae salida analogica.

Regla: confirmar si la salida es activa en bajo.

### Sensor de llama IR

- VCC: 3.3-5 V.
- GND: tierra.
- DO: salida digital.

Regla: probar con distancia segura y no usarlo como unico sistema contra incendio.

### Amplificador Bluetooth

- Entrada DC: 9-24 V segun variante.
- Bocinas: 4-8 ohm, preferir 8 ohm.
- Entrada audio: Bluetooth, AUX o USB.

Regla: si se usan bocinas de 4 ohm, no exceder 12 V segun nota del PDF. Usar fusible.

### Ojos LED flexibles

- Probar con baterias antes de cortar.
- Alimentacion segun version: 2xAAA, CR2032 o USB 5V.
- Fijacion recomendada: silicon caliente.
- No usar 502 o pegamento instantaneo.

Regla: medir la abertura del casco antes de cortar y no dañar la zona del LED.

## Secuencia de trabajo recomendada

1. Banco de alimentacion segura.
2. Arduino Nano: Blink y lectura digital.
3. TTP223: entrada tactil.
4. KY-037: deteccion de sonido.
5. Sensor de llama: entrada digital con umbral.
6. TP4056: prueba con LiPo 1S medida con multimetro.
7. PCA9685 + SG90: calibrador seguro de servos.
8. ESP32 + AHT10/DHT + TFT: nodo IoT ambiental.
9. NRF24L01: enlace de comunicacion.
10. Placas recuperadas de drones: solo despues de documentar fotos y baterias.

## Estado de riesgo por familia

| Familia | Estado | Comentario |
|---|---|---|
| Sensores digitales simples | Bajo | TTP223, PIR, KY-037, flama, siempre validando voltaje |
| Servos | Medio | requieren alimentacion externa y limite mecanico |
| LiPo | Alto | requiere cargador correcto y polaridad verificada |
| Audio 9-24 V | Alto | corriente elevada, usar fusible y bocinas adecuadas |
| Placas recuperadas | Alto | no energizar sin identificar y limitar corriente |
