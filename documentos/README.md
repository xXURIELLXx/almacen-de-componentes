# Documentos

Esta carpeta guarda los documentos fuente usados como referencia tecnica del inventario.

## Objetivo

Conservar PDFs, manuales, publicaciones de compra y transcripciones de chats en una estructura ordenada para que una persona o una IA pueda volver a revisar la fuente original antes de actualizar el inventario.

Los documentos de esta carpeta no convierten automaticamente un dato en confirmado. Un dato extraido de un PDF o publicacion de venta debe marcarse como `referencia` hasta que se mida, valide fisicamente o se confirme con una fuente tecnica mas confiable.

## Estructura recomendada

```text
documentos/
  originales/
    datasheets/
    manuales/
    publicaciones_compra/
    transcripciones_chat/
    fotos_componentes/
  procesados/
    fichas_componentes/
    pendientes_revision/
  README.md
```

## Como clasificar archivos

- `originales/datasheets/`: hojas tecnicas de fabricante o documentacion tecnica formal.
- `originales/manuales/`: manuales de uso, guias de instalacion o instrucciones del producto.
- `originales/publicaciones_compra/`: PDFs generados desde AliExpress, Amazon u otras publicaciones de venta.
- `originales/transcripciones_chat/`: texto exportado o transcrito desde conversaciones anteriores.
- `originales/fotos_componentes/`: fotos propias usadas para identificar modelo, pinout, estado o marcas.
- `procesados/fichas_componentes/`: resumen tecnico ya extraido en formato Markdown.
- `procesados/pendientes_revision/`: material con datos incompletos, dudosos o mezclados entre variantes.

## Nombre de archivos

Usar nombres descriptivos y estables. Cuando sea posible:

```text
categoria_modelo_fuente_fecha.pdf
```

Ejemplos:

```text
programador_avr_isp_shield_aliexpress_2026-06.pdf
sensor_touch_ttp223_aliexpress_2026-06.pdf
manual_ojos_led_flexibles_2026-06.pdf
```

Si el archivo original ya tiene un nombre largo, se puede conservar, pero el indice `data/documentos_pdf.json` debe permitir ubicarlo.

## Relacion con data/documentos_pdf.json

Cada PDF procesado debe tener una entrada en `data/documentos_pdf.json` con:

- id unico, por ejemplo `PDF-011`;
- nombre exacto del archivo;
- componente relacionado, si existe;
- tipo de documento;
- datos clave extraidos;
- pines o conexiones;
- uso inicial;
- riesgos;
- fuente, pagina o seccion revisada;
- estado de revision.

## Regla de seguridad

Antes de usar un dato electrico extraido de un PDF, validar polaridad, voltaje nominal, rango permitido y consumo. No energizar placas recuperadas, baterias, motores, servos, LEDs de potencia o modulos boost sin revisar riesgos y limites.
