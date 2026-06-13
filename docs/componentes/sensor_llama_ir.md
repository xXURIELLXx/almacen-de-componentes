# Sensor de llama IR

## Identificacion

- Componente: sensor de llama infrarrojo.
- ID relacionado: `SEN-006` en documentos PDF.
- Fuente: `PDF-006`, referencia inicial de publicacion de venta.
- Estado de validacion: pendiente de prueba fisica y alta precaucion.

## Alimentacion

| Campo | Valor | Estado |
|---|---|---|
| Voltaje | 3.3-5 V | referencia inicial |
| Rango optico | 760-1100 nm aproximado | referencia inicial |
| Angulo de deteccion | 60 grados aproximado | referencia inicial |
| Comparador | LM393 | referencia inicial |
| Salida | digital `DO` 0/1 | referencia inicial |
| Ajuste | potenciometro | referencia inicial |

## Pines

| Pin | Funcion | Nota |
|---|---|---|
| `VCC` | alimentacion | 3.3 V o 5 V segun controlador |
| `GND` | tierra | tierra comun |
| `DO` | salida digital | entrada digital del microcontrolador |

## Uso inicial

1. Alimentar con el voltaje compatible con el microcontrolador.
2. Ajustar sensibilidad con el potenciometro.
3. Probar con una fuente IR o flama pequena a distancia segura.
4. Registrar falsos positivos por luz ambiente.

## Riesgos

- No usar como unico sistema de seguridad contra incendio.
- Puede activarse con luz IR o fuentes intensas.
- No acercar a calor excesivo.
- No exponer cables o plastico a una llama real.

## Prueba recomendada

- Hacer prueba corta, controlada y con distancia.
- Confirmar nivel logico de `DO` en reposo y deteccion.
- Documentar sensibilidad y distancia util en el entorno real.

## Relacion con proyectos

- Pruebas de entradas digitales.
- Deteccion experimental de flama para aprendizaje.
- Alarmas demostrativas, no sistemas criticos.

## Pendiente de validar

- Distancia real de deteccion.
- Respuesta ante luz solar, focos e IR de controles remotos.
- Compatibilidad electrica directa con ESP32.
