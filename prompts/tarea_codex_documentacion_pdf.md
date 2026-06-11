# Tarea para Codex / Copilot Agent

## Objetivo

Continuar la organizacion del repositorio `xXURIELLXx/almacen-de-componentes` para que una IA pueda analizar inventario, PDFs, conexiones iniciales y prioridades de proyecto.

## Contexto

El repositorio ya contiene:

- `README.md`
- `AGENTS.md`
- `ai_context/AI_CONTEXT.md`
- `data/inventario_componentes.json`
- `data/documentos_pdf.json`
- `docs/pdf_revisados.md`
- `docs/conexiones_iniciales.md`

El enfoque del repositorio es documentar componentes reales disponibles para proyectos de robotica, embebidos, IoT, automatizacion, recuperacion de drones y cosplay electronico.

## Tarea principal

1. Revisar que `data/documentos_pdf.json` sea JSON valido.
2. Revisar que `docs/pdf_revisados.md` sea legible y consistente con `data/documentos_pdf.json`.
3. Revisar que `docs/conexiones_iniciales.md` no contradiga las advertencias de `AGENTS.md`.
4. Crear, si no existen, las carpetas:
   - `assets/pdfs/`
   - `assets/images/`
   - `docs/componentes/`
   - `proyectos/calibrador_servos/`
   - `proyectos/nodo_iot_ambiental/`
   - `proyectos/casco_ironman/`
5. Si los PDFs originales estan disponibles localmente, copiarlos a `assets/pdfs/` con nombres cortos y sin espacios excesivos.
6. Crear un indice `assets/pdfs/README.md` con nombre de archivo, componente asociado y estado de revision.
7. Crear fichas individuales en `docs/componentes/` para los componentes ya revisados:
   - `avr_isp_shield.md`
   - `tp4056.md`
   - `ttp223.md`
   - `ky037.md`
   - `sensor_llama_ir.md`
   - `ojos_led_cosplay.md`
   - `amplificador_bluetooth.md`
   - `esp32_variantes.md`
8. Cada ficha debe tener:
   - identificacion;
   - alimentacion;
   - pines;
   - uso inicial;
   - riesgos;
   - prueba recomendada;
   - relacion con proyectos.

## Reglas

- No inventar especificaciones.
- Si un dato no aparece, escribir `pendiente de validar`.
- Si el dato viene de publicacion de venta, marcarlo como `referencia inicial`.
- Mantener advertencias de seguridad sobre TP4056, LiPo, servos, ESP32 y placas recuperadas.
- No eliminar archivos existentes.
- Dejar commits claros.

## Validacion

Antes de terminar:

- Ejecutar una validacion de JSON, por ejemplo con Python:

```bash
python -m json.tool data/documentos_pdf.json > /tmp/documentos_pdf_validado.json
python -m json.tool data/inventario_componentes.json > /tmp/inventario_validado.json
```

- Revisar estado de Git:

```bash
git status
```

## Resultado esperado

Un commit con estructura mas clara, fichas por componente, indice de PDFs y validacion de JSON.
