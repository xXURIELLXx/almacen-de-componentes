# AVR ISP Shield

## Identificacion

- Componente: AVR ISP Shield.
- ID relacionado: `PROG-001`.
- Fuente: `PDF-001`, referencia inicial de publicacion de venta.
- Uso principal: quemar bootloader o programar chips AVR compatibles.
- Estado de validacion: pendiente de prueba fisica.

## Alimentacion

| Campo | Valor | Estado |
|---|---|---|
| Voltaje de trabajo | 5 V | referencia inicial |
| Corriente maxima indicada | 500 mA | referencia inicial |
| Objetivos compatibles | Arduino R3, Mega2560, Nano, Pro Mini 5 V 16 MHz; ATmega328P, ATmega168P, ATmega8 | referencia inicial |

## Pines y conectores

| Conector | Funcion | Nota |
|---|---|---|
| ZIF 28P | Zocalo para AVR DIP-28 | respetar orientacion del chip |
| ISP 6 pines | Programacion ISP | validar pinout antes de conectar |
| ISP 10 pines | Programacion ISP | validar pinout antes de conectar |
| SPI/ICSP | Comunicacion de programacion | usar solo con objetivos compatibles |
| USB-TTL FT232RL/CH340G | Interfaz serial indicada por la fuente | variante pendiente de confirmar |

## Uso inicial

1. Montar el shield sobre Arduino compatible.
2. Insertar el ATmega en el zocalo ZIF respetando la muesca/orientacion.
3. Usar el flujo de Arduino como ISP para cargar bootloader.
4. Observar LEDs `HEART BEAT`, `PROG`, `ERROR` y buzzer.
5. Detener la prueba ante LED `ERROR`, calentamiento o comportamiento no esperado.

## Riesgos

- No usar con objetivos de 3.3 V sin adaptar niveles.
- No invertir el chip DIP en el zocalo.
- No asumir compatibilidad con cualquier AVR sin validar pinout.
- Si el chip ATmega comprado no trae bootloader, debe tratarse como microcontrolador virgen.

## Prueba recomendada

- Probar primero con un ATmega328P conocido o reemplazable.
- Verificar continuidad y polaridad antes de energizar.
- Registrar resultado de bootloader como `confirmado` solo despues de una prueba exitosa.

## Relacion con proyectos

- Bootloader y recuperacion de ATmega328P.
- Banco de aprendizaje de Arduino.
- Preparacion de chips para proyectos simples con sensores.

## Pendiente de validar

- Variante exacta del chip USB-TTL.
- Pinout fisico real del shield recibido.
- Resultado de programacion con ATmega328P real.
