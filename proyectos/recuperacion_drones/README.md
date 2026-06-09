# Proyecto: recuperacion de drones

## Objetivo

Investigar placas, controles, motores y baterias recuperadas de drones sin danar componentes.

## Material registrado

- 2 tarjetas YD-W6833-v.1c asociadas a camara o transmision.
- 2 tarjetas HY-2016R a asociadas a control de dron.
- Controles originales disponibles.
- Otro dron moderno con camara y motores de dos cables.
- Baterias LiPo 952540 de 3.7 V.

## Protocolo inicial

1. Tomar foto frontal y trasera de cada placa.
2. Identificar chips principales.
3. Marcar conectores y puntos de soldadura.
4. Medir continuidad entre tierra y puntos negativos.
5. Medir voltaje real de cada bateria.
6. Energizar solo con fuente limitada.
7. Probar motores por separado antes de usar la placa.

## Hipotesis inicial

Los motores de dos cables son motores DC brushed. Se pueden probar con polaridad controlada y driver adecuado, no directo desde GPIO.

## Riesgos

- Pin TX no identificado.
- Antena puede pertenecer a comunicacion RF o video.
- La placa podria usar protocolo propietario.
- No se conoce aun si todas las baterias son compatibles entre drones.
