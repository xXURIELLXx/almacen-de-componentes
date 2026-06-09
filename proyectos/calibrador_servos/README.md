# Proyecto: calibrador seguro de servos

## Objetivo

Construir una herramienta para probar y calibrar servos SG90 sin forzar el mecanismo.

## Componentes sugeridos

- Arduino Nano o ESP32.
- PCA9685.
- Servo SG90.
- Fuente externa de 5 V para servos.
- Pantalla TFT o monitor serial.
- Botones, teclado o modulo touch.

## Logica de seguridad

1. Iniciar siempre en posicion central.
2. Mover en pasos pequenos.
3. Registrar limite minimo seguro.
4. Registrar limite maximo seguro.
5. Permitir invertir direccion por software.
6. Bloquear cualquier comando fuera de limites.
7. Probar primero sin carga mecanica.

## Resultado esperado

El sistema debe mostrar angulo actual, limite minimo, limite maximo, direccion y estado del servo. Esta informacion debe servir para proyectos como casco Iron Man, compuertas o mecanismos pequenos.
