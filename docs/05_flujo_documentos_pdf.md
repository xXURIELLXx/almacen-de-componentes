# Flujo para procesar PDFs tecnicos

Este documento define como convertir PDFs, manuales, publicaciones de compra y transcripciones en datos utiles para el inventario.

## Principio principal

No todo dato extraido de un PDF es un dato confirmado. En este repositorio se separan tres niveles:

- `confirmado`: dato medido, verificado fisicamente o confirmado por el usuario.
- `referencia`: dato tomado de PDF, manual, datasheet o publicacion de compra.
- `pendiente`: dato no encontrado, ambiguo, mezclado entre variantes o no validado.

## Entradas del proceso

Un documento puede venir de:

- datasheet oficial;
- manual de uso;
- publicacion de compra;
- transcripcion de chat anterior;
- foto o captura con informacion tecnica;
- nota propia del usuario.

## Salidas esperadas

Cada documento procesado debe producir al menos una de estas salidas:

1. Entrada en `data/documentos_pdf.json`.
2. Ficha Markdown en `documentos/procesados/fichas_componentes/`.
3. Actualizacion del inventario solo si el dato es util y se marca su origen.
4. Lista de pendientes si faltan modelo exacto, pinout, voltaje o validacion.

## Campos minimos por PDF

Usar este esquema como base:

```json
{
  "id": "PDF-011",
  "archivo": "nombre-del-documento.pdf",
  "componente_relacionado": "ID o nombre del componente",
  "tipo": "datasheet | manual | publicacion_compra | transcripcion | foto | mixto",
  "estado_revision": "nuevo | procesado | pendiente_revision | requiere_validacion",
  "nivel_fuente": "oficial | referencia | usuario | desconocido",
  "datos_clave": {
    "modelo": "No especificado",
    "descripcion": "No especificado",
    "voltaje_nominal": "No especificado",
    "rango_voltaje": "No especificado",
    "corriente": "No especificado",
    "potencia": "No especificado",
    "capacidades": "No especificado",
    "limitantes": "No especificado",
    "metodo_uso": "No especificado"
  },
  "pines_conexiones": "No especificado",
  "uso_inicial": "No especificado",
  "riesgos": [],
  "validaciones_pendientes": [],
  "fuente": "pagina o seccion revisada"
}
```

## Ficha Markdown recomendada

Cada componente o documento importante puede tener una ficha asi:

```md
# Nombre del componente

## Fuente

- Archivo original:
- Tipo de fuente:
- Estado de revision:
- Nivel de confianza:

## Identificacion

- Modelo:
- Fabricante/marca:
- Variante:
- Componente relacionado en inventario:

## Descripcion

Resumen tecnico breve sin inventar datos.

## Metodo de uso

- Alimentacion:
- Conexion:
- Senal o protocolo:
- Prueba inicial segura:

## Datos electricos

- Voltaje nominal:
- Rango de voltaje:
- Corriente:
- Potencia:
- Nivel logico:

## Capacidades

- Sensado, comunicacion, actuacion o funcion principal:
- Rango de operacion:
- Resolucion, frecuencia, torque, potencia o salida, si aplica:

## Limitantes

- Condiciones donde no debe usarse:
- Variantes mezcladas o datos ambiguos:
- Restricciones mecanicas o electricas:

## Riesgos y seguridad

- Riesgos principales:
- Validaciones antes de energizar:
- Protecciones recomendadas:

## Pendientes

- Datos faltantes:
- Mediciones requeridas:
- Fotos o pruebas necesarias:
```

## Reglas de extraccion

1. Mantener el nombre del archivo original.
2. Indicar pagina, seccion o evidencia usada cuando sea posible.
3. No mezclar variantes si el PDF habla de varios modelos.
4. Si el PDF contradice el inventario, no sobrescribir: agregar pendiente de revision.
5. Si el dato viene de publicacion de compra, marcarlo como `referencia`.
6. Si falta una unidad, conservar el dato como ambiguo y pedir validacion.
7. No modificar IDs existentes del inventario.
8. No borrar datos previos sin justificar la razon.

## Reglas especificas de hardware

- Para placas recuperadas: no energizar sin identificar polaridad, tension esperada y consumo con fuente limitada.
- Para servos: documentar voltaje, fuente externa, limites mecanicos, inversion de direccion y prueba sin carga.
- Para baterias: documentar quimica, voltaje nominal, voltaje maximo, conector, polaridad y cargador compatible.
- Para modulos boost: ajustar salida antes de conectar carga.
- Para ESP32: tratar GPIO como 3.3 V y evitar senales de 5 V sin adaptacion.
- Para jumpers y protoboard: tratarlos como conexiones temporales, no como montaje definitivo.

## Criterio para actualizar inventario

Actualizar `data/inventario_componentes.json` solo cuando el dato ayude a decidir uso, conexion, riesgo o prioridad. En caso de duda, registrar primero en `data/documentos_pdf.json` y dejar la validacion pendiente.

## Flujo de trabajo recomendado

1. Guardar PDF en `documentos/originales/` segun categoria.
2. Extraer texto o revisar paginas clave.
3. Identificar si el documento describe uno o varios modelos.
4. Crear o actualizar entrada en `data/documentos_pdf.json`.
5. Crear ficha Markdown si el documento aporta bastante informacion.
6. Comparar con el inventario existente.
7. Actualizar inventario solo con datos trazables.
8. Registrar pendientes de medicion o validacion fisica.

## Primer lote recomendado

Procesar primero documentos que reduzcan riesgo electrico:

1. TP4056 y baterias LiPo 1S.
2. Servos SG90 y PCA9685.
3. Modulos boost y fuentes.
4. Placas recuperadas de drones.
5. ESP32, NRF24L01 y sensores I2C.
