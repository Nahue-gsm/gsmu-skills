# Skill: Impresión térmica ESC/POS (GSMU)

## Objetivo
Implementar impresión de tickets/comandas en impresoras térmicas (ESC/POS).

## Cuándo aplicar
Cuando el proyecto requiera:
- Tickets de caja
- Comandas de cocina
- Impresión rápida y confiable

## Preguntas mínimas
- ¿Windows? (normalmente sí)
- ¿USB / red? ¿nombre de impresora?
- ¿Formato: 58mm o 80mm?
- ¿Corte automático? ¿apertura de cajón?

## Reglas
- Mantener templates de ticket como funciones puras (entrada -> salida)
- Probar con caracteres especiales (ñ, tildes)
- Manejar fallback si impresora offline

## Nota
La implementación concreta depende del driver y librería elegida (node-escpos u otro).
No instalar librerías nuevas sin justificar.
