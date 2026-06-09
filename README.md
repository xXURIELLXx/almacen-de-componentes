# Almacen de Componentes

Repositorio tecnico para inventariar componentes de robotica, sistemas embebidos, IoT, automatizacion y material recuperado.

## Objetivo

Documentar los componentes disponibles con datos utiles para una persona o una IA: identificacion, cantidad, voltajes, comunicacion, pines, riesgos, estado de validacion y posibles proyectos.

## Estructura principal

- ai_context/AI_CONTEXT.md: contexto consolidado para que otra IA entienda el repositorio.
- data/inventario_componentes.json: inventario estructurado para analisis automatico.
- data/inventario_componentes.csv: version tabular del inventario.
- data/documentos_pdf.json: resumen de PDFs y datos extraidos.
- docs/: metodologia, seguridad, conexiones iniciales y prioridades.
- proyectos/: rutas de desarrollo iniciales.
- prompts/: prompt para continuar el repositorio con una IA.

## Fases registradas

1. Modulos, microcontroladores, sensores, motores, servos y potencia basica.
2. Placas recuperadas de drones y baterias LiPo 1S.
3. Documentacion tecnica desde PDFs de compra/manuales.

## Prioridad tecnica

1. Alimentacion segura: 3.3 V, 5 V, 12 V y LiPo 1S.
2. Calibrador seguro de servos SG90 con PCA9685.
3. Nodo ambiental IoT con ESP32, AHT10/DHT, PIR y TFT.
4. Comunicacion NRF24L01.
5. Investigacion controlada de placas recuperadas de drones.

## Nota de seguridad

Muchos datos provienen de modulos genericos o publicaciones de compra. Antes de energizar debo validar polaridad, voltaje, reguladores integrados y consumo real.

Ultima actualizacion: 2026-06-09.
