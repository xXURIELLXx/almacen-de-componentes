# AGENTS.md

Este repositorio debe ser mantenido para que una IA pueda analizar inventario, documentacion tecnica y rutas de proyecto sin depender del historial de chat.

## Objetivo del agente

Mantener un almacen tecnico de componentes para robotica, sistemas embebidos, IoT, automatizacion, recuperacion de drones y electronica aplicada a cosplay.

## Reglas generales

1. No inventar datos tecnicos.
2. Separar datos confirmados, datos inferidos y pendientes de validacion.
3. Si una fuente viene de AliExpress u otra publicacion de venta, marcarla como referencia inicial y no como datasheet oficial.
4. Antes de proponer conexiones, indicar voltaje, tierra, senal, corriente y riesgo.
5. No recomendar energizar placas recuperadas sin fuente limitada en corriente.
6. No mezclar 5 V con GPIO de ESP32 sin adaptacion de nivel.
7. No usar TP4056 con baterias de 12 V; solo Li-ion/LiPo 1S.
8. Para servos SG90, usar alimentacion externa y calibracion de limites.
9. Mantener redaccion tecnica, clara y reutilizable.
10. Todo cambio debe dejar el repositorio consistente para lectura humana y analisis automatico.

## Estructura esperada

- `README.md`: resumen del repositorio y estado general.
- `ai_context/AI_CONTEXT.md`: contexto consolidado para otra IA.
- `data/inventario_componentes.json`: inventario estructurado.
- `data/documentos_pdf.json`: datos tecnicos extraidos de PDFs.
- `docs/pdf_revisados.md`: resumen humano de PDFs.
- `docs/conexiones_iniciales.md`: reglas de conexion y pruebas iniciales.
- `proyectos/`: rutas de proyecto y pruebas.
- `prompts/`: tareas listas para ejecutar con IA.

## Estilo de documentacion

Usar tablas cuando ayuden. Para cada componente documentar, cuando exista:

- nombre comun;
- categoria;
- cantidad;
- modelo o numero marcado;
- voltaje;
- corriente o potencia;
- tipo de senal o comunicacion;
- pines importantes;
- uso inicial;
- proyectos compatibles;
- restricciones y riesgos;
- fuente o PDF relacionado;
- estado de validacion.

## Prioridades tecnicas

1. Alimentacion segura: 3.3 V, 5 V, 12 V y LiPo 1S.
2. TP4056 y baterias LiPo 1S.
3. Calibrador seguro de servos con PCA9685.
4. Nodo ambiental IoT con ESP32, AHT10/DHT, PIR y TFT.
5. Entradas simples: TTP223, KY-037, sensor de llama IR.
6. Comunicacion NRF24L01.
7. Placas recuperadas de drones.
8. Proyecto casco Iron Man: servos, ojos LED, audio y control.

## Validacion minima

Para cambios de documentacion:

- Revisar que Markdown sea legible.
- Revisar que JSON sea valido.
- Revisar que los IDs no se repitan.
- Revisar que las advertencias de seguridad no contradigan documentos previos.

Para cambios de codigo futuro:

- Incluir instrucciones de prueba.
- Mantener codigo separado por proyecto.
- No borrar documentacion existente sin justificar.
