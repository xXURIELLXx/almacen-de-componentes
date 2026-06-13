# Amplificador Bluetooth 302T / LT21

## Identificacion

- Componente: modulo amplificador Bluetooth 302T/LT21.
- Fuente: `PDF-004`, referencia inicial de publicacion de venta.
- Categoria: audio / potencia.
- Estado de validacion: pendiente de confirmar variante fisica.

## Alimentacion

| Campo | Valor | Estado |
|---|---|---|
| Alimentacion 302T | 9-24 V / 3 A | referencia inicial |
| Salida 302/302T | 30 W + 30 W | referencia inicial |
| Salida LT21 | 15 W + 15 W + 30 W | referencia inicial |
| Entradas | Bluetooth 5.1, AUX, USB drive, USB sound card | referencia inicial |
| Bocinas | 10-50 W, 4-8 ohm; recomendado 8 ohm | referencia inicial |

## Conexiones

| Conector | Funcion | Nota |
|---|---|---|
| Jack DC 5.5 x 2.1 | alimentacion | usar fuente estable y fusible |
| L/R | salidas de bocina | no cortocircuitar |
| AUX | entrada de audio analogica | validar volumen bajo al inicio |
| USB | memoria o tarjeta de sonido USB segun variante | pendiente de confirmar |

## Uso inicial

1. Confirmar variante exacta impresa en la placa.
2. Usar fuente DC estable con fusible.
3. Conectar bocinas de 8 ohm para primera prueba.
4. Iniciar a bajo volumen.
5. Verificar calentamiento y consumo.

## Riesgos

- No alimentar desde microcontrolador.
- No cortocircuitar salidas de bocinas.
- Si se usan bocinas de 4 ohm, no exceder 12 V segun nota del PDF.
- La bateria sellada de 12 V requiere fusible y conexion segura.
- Corrientes altas pueden danar cables finos o protoboard.

## Prueba recomendada

- Probar con 12 V o menos y bocinas 8 ohm.
- Verificar polaridad de entrada antes de conectar.
- Medir consumo en reposo y a volumen bajo.

## Relacion con proyectos

- Audio para casco Iron Man o banco de pruebas.
- Reproductor Bluetooth auxiliar.
- Proyecto de potencia separado de microcontroladores.

## Pendiente de validar

- Variante fisica: 302, 302T o LT21.
- Potencia real segura con las bocinas disponibles.
- Consumo real y temperatura.
