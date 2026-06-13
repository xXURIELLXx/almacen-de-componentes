# Indice de PDFs

Fecha: 2026-06-12

Este indice registra los PDFs revisados en `data/documentos_pdf.json` y `docs/pdf_revisados.md`.

Los archivos PDF originales no estuvieron disponibles localmente en esta sesion de Codex, por lo que no se copiaron binarios a `assets/pdfs/`. Cuando esten disponibles, deben agregarse con nombres cortos, sin espacios excesivos y manteniendo la relacion con el ID `PDF-###`.

## Estado general

- Fuente de datos: `data/documentos_pdf.json`.
- Resumen humano: `docs/pdf_revisados.md`.
- Estado de binarios: pendiente de cargar.
- Nivel de confianza: referencia inicial, porque la mayoria de fuentes son publicaciones de venta o manuales genericos.

## Indice recomendado

| ID | Nombre corto sugerido | Componente asociado | PDF original | Estado |
|---|---|---|---|---|
| PDF-001 | `avr_isp_shield.pdf` | PROG-001 AVR ISP Shield | Escudo de expansion programable AVR ISP con zumbador para Arduino R3 Mega2560 Pro Mini Atmega328P modulo SPI de quemador de arranque - AliExpress 502.pdf | documentado, binario pendiente |
| PDF-002 | `atmega328p_dip28.pdf` | ATmega328P DIP-28 | 1pcs_lot ATMEGA328P-PU ATMEGA328P-U ATMEGA328P DIP-28 IC In Stock - AliExpress 502.pdf | documentado, binario pendiente |
| PDF-003 | `esp32_variantes_d1_mini.pdf` | ESP32-S2 Mini / ESP8266 D1 Mini / ESP32-WROOM-32 D1 Mini | ESP32 S2 Mini _ ESP8266 D1 Mini placa CH340 _ ESP32-S2FN4R2 4MB FLASH 2MB PSRAM Placa de desarrollo MicroPython - AliExpress 502.pdf | documentado, binario pendiente |
| PDF-004 | `amplificador_bluetooth_302t_lt21.pdf` | Amplificador Bluetooth 302T/LT21 | Mini Bluetooth 5,1 DC 9-24V modulo de placa amplificadora de potencia Digital de Audio 2,1 canales 2,0 estereo de doble canal 30W _ 2 15W _ 2 + 30W - AliExpress 44.pdf | documentado, binario pendiente |
| PDF-005 | `tp4056_usb_c_micro_usb.pdf` | PWR-002 TP4056 | 20 piezas-Modulo de placa de carga de bateria de litio, proteccion de carga 2 en 1, interfaz Micro USB_tipo c, 1A, 5V, TP4056 - AliExpress 502.pdf | documentado, binario pendiente |
| PDF-006 | `sensor_llama_ir.pdf` | SEN-006 sensor de llama IR | Modulo de Sensor de llama IR, Detector Smartsense para deteccion de temperatura adecuado para Arduino, envio gratis, venta al por mayor - AliExpress.pdf | documentado, binario pendiente |
| PDF-007 | `ky037_sensor_sonido.pdf` | SEN-002 KY-037 | Modulo de deteccion de Sensor de microfono de sonido de alta sensibilidad para AVR PIC KY-037 Modulo de Sensor de deteccion de sonido Sensor de sonido - AliExpress 502.pdf | documentado, binario pendiente |
| PDF-008 | `ojos_led_flexibles_cosplay.pdf` | LED-002 ojos LED flexibles | Cosplay ojos Led flexibles flexibles Diy para Halloween hierro exposicion difusa hombre mascara accesorios de luz de ojos puede recortar accesorios nuevo - AliExpress 200000532.pdf | documentado, binario pendiente |
| PDF-009 | `manual_ojos_led_cosplay.pdf` | LED-002 ojos LED flexibles | Sa1f348513347422ab79d351befdf1b94A.pdf | documentado, binario pendiente |
| PDF-010 | `ttp223_touch.pdf` | IN-002 TTP223/HW-139 | Modulo de Interruptor tactil TTP223 TTP223B Sensor tactil capacitivo Digital Jog de 1 canal para KIT de bricolaje arduino - AliExpress 502.pdf | documentado, binario pendiente |

## Regla para agregar PDFs

1. Confirmar que el PDF corresponde al componente correcto.
2. Renombrar con el nombre corto sugerido o uno equivalente.
3. No borrar el nombre original: conservarlo en este indice y en `data/documentos_pdf.json`.
4. Si se extraen datos nuevos, marcarlos como `referencia inicial` salvo que sean medidos fisicamente o vengan de datasheet oficial.
5. Si un dato no esta claro, usar `pendiente de validar`.
