# Revision de PDFs y datos utiles

Fecha: 2026-06-11

Este documento resume la informacion tecnica extraida de los PDFs compartidos en el chat. La fuente principal son publicaciones/manuales de AliExpress, por lo que cada dato debe tratarse como referencia inicial y no como verdad final de diseno. Antes de energizar un modulo debo validar polaridad, voltaje real, reguladores, continuidad y consumo con multimetro.

## 1. AVR ISP Shield

Archivo: Escudo de expansion programable AVR ISP con zumbador para Arduino R3 Mega2560 Pro Mini Atmega328P modulo SPI de quemador de arranque.

Datos extraidos:

- Uso: quemar bootloader y modificar fusibles en chips AVR externos o placas Arduino compatibles.
- Voltaje de trabajo indicado: 5 V.
- Corriente maxima indicada: 500 mA.
- Compatibilidad indicada: Arduino R3, Mega2560, Nano y Pro Mini 5 V / 16 MHz.
- Zocalo: ZIF 28 pines para ATmega328P, ATmega168P y ATmega8.
- Interfaces: ISP 6 pines, ISP 10 pines, SPI/ICSP y USB a TTL FT232RL/CH340G.
- Indicadores: HEART BEAT, PROG, ERROR y buzzer.

Uso inicial:

1. Montar el shield sobre Arduino UNO/R3 o Mega compatible.
2. Insertar chip DIP-28 respetando la orientacion.
3. Usar el flujo de Arduino como ISP para cargar bootloader.
4. Detener si el LED ERROR se enciende o si el buzzer no confirma el proceso.

Riesgos: no usar con objetivos de 3.3 V sin adaptacion de nivel. No invertir el chip en el zocalo.

## 2. ATmega328P-PU / ATmega328P-U DIP-28

Archivo: 1pcs_lot ATMEGA328P-PU ATMEGA328P-U ATMEGA328P DIP-28 IC.

Datos extraidos:

- Producto: microcontrolador ATmega328P en encapsulado DIP-28.
- La publicacion no confirma con claridad si trae bootloader.
- Uso probable: repuesto para Arduino UNO/Nano o chip externo programado con AVR ISP Shield.

Uso inicial:

1. Verificar orientacion del encapsulado.
2. Grabar bootloader con el AVR ISP Shield si no lo trae.
3. Para montaje independiente, usar cristal/resonador si se desea Arduino 16 MHz, capacitores y desacoplo.

Riesgos: no asumir bootloader; no alimentar sin circuito minimo correcto.

## 3. ESP32 S2 Mini / ESP8266 D1 Mini / D1 Mini ESP32

Archivo: ESP32 S2 Mini / ESP8266 D1 Mini placa CH340 / ESP32-S2FN4R2 4MB FLASH 2MB PSRAM.

Advertencia: el PDF mezcla variantes. No debo cablear o cargar firmware sin identificar fisicamente el chip real.

Datos extraidos por variante:

- ESP8266 D1 Mini: basado en ESP8266EX, 11 pines I/O, 1 ADC 0-3.3 V, IO a 3.3 V, alimentacion 5 V en placa.
- ESP32-S2 Mini: ESP32-S2FN4R2, USB-C, 4 MB Flash, 2 MB PSRAM, 27 I/O, ADC, DAC, I2C, SPI, UART, USB OTG, firmware MicroPython indicado.
- D1 Mini ESP32-WROOM-32: WiFi + Bluetooth, USB Type-C, chip serial CH9102, dimensiones aproximadas 31 x 39 mm.

Uso inicial:

1. Identificar chip real con foto frontal.
2. Instalar driver USB correcto si Windows no reconoce la placa.
3. En Arduino IDE o MicroPython seleccionar placa segun chip real.
4. Usar siempre logica de 3.3 V en GPIO.

Riesgos: GPIO no tolera 5 V. El pinout depende de la variante.

## 4. Amplificador Bluetooth 302T / LT21

Archivo: Mini Bluetooth 5.1 DC 9-24V modulo de placa amplificadora digital de audio.

Datos extraidos:

- Variante visible: 302T.
- Alimentacion 302T indicada: 9-24 V / 3 A.
- Salida 302/302T: 30 W + 30 W.
- Salida LT21: 15 W + 15 W + 30 W.
- Entradas: Bluetooth 5.1, AUX, USB drive y USB sound card.
- Bocinas: 10-50 W, 4-8 ohm. Se recomienda 8 ohm.
- Nota critica: si se usan bocinas de 4 ohm, no exceder 12 V segun tabla del PDF.

Uso inicial:

1. Probar con fuente DC estable y fusible.
2. Usar bocinas de 8 ohm para prueba inicial.
3. Conectar primero a bajo volumen.
4. No cortocircuitar salidas de bocinas.

Riesgos: consumo alto; no alimentar desde microcontrolador; no usar bateria 12 V sin fusible.

## 5. TP4056 / 4056 USB-C

Archivo: 20 piezas - Modulo de carga de bateria de litio, proteccion de carga 2 en 1, Micro USB / Type-C, 1A, 5V, TP4056.

Datos extraidos:

- Entrada: 5 V por USB-C o Micro USB.
- Corriente maxima de carga: 1000 mA.
- Corte de carga: 4.2 V +/- 1%.
- Proteccion de sobredescarga: 2.5 V.
- Proteccion de sobrecorriente: 3 A.
- Pines: B+, B-, OUT+, OUT-.
- Tamano aproximado: 2.6 x 1.7 cm o 28 x 17 mm segun imagen.

Conexion inicial:

- B+ y B-: bateria Li-ion/LiPo 1S de 3.7 V.
- OUT+ y OUT-: salida protegida hacia la carga.
- USB: entrada de 5 V para carga.

Riesgos: solo para una celda de litio 1S. No usar con bateria sellada de 12 V. Validar polaridad antes de soldar. Puede calentarse cerca de 1 A.

## 6. Sensor de llama IR

Archivo: Modulo de Sensor de llama IR, Detector Smartsense para Arduino.

Datos extraidos:

- Deteccion de flama por infrarrojo en rango aproximado 760-1100 nm.
- Angulo de deteccion: 60 grados aproximado.
- Distancia de prueba indicada: hasta 80 cm con flama pequena, segun descripcion.
- Voltaje: 3.3-5 V.
- Comparador: LM393.
- Salida: digital DO 0/1.
- Pines visibles: VCC, GND, DO.
- Ajuste: potenciometro de sensibilidad.

Uso inicial:

1. VCC a 3.3 V o 5 V.
2. GND comun.
3. DO a entrada digital.
4. Ajustar potenciometro hasta lograr deteccion estable.

Riesgos: puede activarse con otras fuentes IR o luz intensa. No acercar demasiado a una flama real.

## 7. KY-037 sensor de sonido

Archivo: Modulo de deteccion de sensor de microfono de sonido KY-037.

Datos extraidos:

- Chip: LM393.
- Sensor: microfono electret.
- Voltaje indicado: 3.3-5 V en una seccion y 4-6 V en otra. Usar 5 V para Arduino y validar salida antes de usar con ESP32.
- Salida: digital por umbral; en el PDF se indica salida efectiva en nivel bajo cuando detecta sonido.
- Pines comunes: VCC, GND, OUT. Algunas variantes traen AO/DO.
- Ajuste: potenciometro de sensibilidad.
- Limitacion: detecta presencia/intensidad de sonido, no reconoce palabras ni frecuencia.

Uso inicial:

1. Alimentar a 5 V para primera prueba con Arduino.
2. Leer OUT como entrada digital.
3. Ajustar potenciometro.
4. Verificar si la salida es activa en bajo.

Riesgos: no usarlo como medidor de decibeles. Para ESP32 verificar nivel logico.

## 8. Ojos LED flexibles para cosplay

Archivo: Cosplay ojos LED flexibles DIY para mascara.

Datos extraidos:

- Modelo: AAA-0221-07.
- Alimentacion: 2 baterias AAA, no incluidas.
- Tamano de lente: 27.5 x 76.5 mm.
- Area efectiva aproximada: 27.5 x 69.5 mm.
- Material: PVC flexible, recortable.
- Uso: ojos iluminados para casco o mascara tipo Iron Man.

Uso inicial:

1. Probar antes de cortar.
2. Medir huecos de ojos del casco.
3. Recortar con cuidado dejando protegida la zona del LED.
4. Fijar por dentro del casco.

Riesgos: reduce vision. No cortar cerca del LED. El PDF advierte no retirar indebidamente la pelicula reflectiva porque se pueden desprender LEDs.

## 9. Manual de ojos LED cosplay

Archivo: Sa1f348513347422ab79d351befdf1b94A.pdf.

Datos extraidos:

- Probar con bateria correcta antes de cortar o pegar.
- Retener la estructura trapezoidal del LED.
- Adhesivo recomendado: silicon caliente / hot melt adhesive.
- Adhesivos prohibidos: 502, instantaneo, pegamento liquido o similares.
- Version USB: 5 V / 1 A.
- Versiones de bateria: CR2032, 2xAAA o CR2025 para control remoto segun variante.
- Si se almacena por largo tiempo, retirar baterias.

Riesgos: no mirar directamente luz intensa por tiempo prolongado, no sumergir, no exponer a fuego/calor alto, no usar de noche si reduce visibilidad.

## 10. TTP223 / HW-139 modulo touch

Archivo: Modulo de interruptor tactil TTP223/TTP223B.

Datos extraidos:

- Chip: TTP223B.
- Voltaje: 2.0-5.5 V DC.
- Pines: SIG, VCC, GND.
- Estado inicial: bajo; al tocar entrega alto en modo momentaneo.
- VOH aproximado: 0.8 VCC.
- VOL maximo: 0.3 VCC.
- Respuesta: 220 ms en bajo consumo, 60 ms en modo rapido.
- Tamano: 23.7 x 23.7 mm.

Uso inicial:

1. VCC a 3.3 V o 5 V.
2. GND comun.
3. SIG a entrada digital.
4. Probar primero como boton momentaneo.

Riesgos: no montar detras de metal; confirmar si el modulo esta en modo momentaneo o latch segun soldaduras.

## Prioridad despues de revisar PDFs

1. Seguridad de alimentacion: LiPo 1S, 5 V, 3.3 V y 12 V.
2. TP4056 para baterias LiPo 1S, nunca para bateria sellada 12 V.
3. AVR ISP Shield + ATmega328P para aprender bootloader.
4. TTP223, KY-037 y sensor de llama para entradas digitales simples.
5. Ojos LED para proyecto casco Iron Man con prueba antes de corte.
6. Amplificador Bluetooth solo con fuente y bocinas adecuadas.
