# Skill: Project Bootstrap (AI-First)

## Objetivo
Garantizar que cualquier IA trabaje sobre el proyecto real sin inventar stack, base de datos, rutas ni arquitectura.

## Regla 1 — Fuente de verdad
Antes de escribir código, la IA debe:

1) Buscar `AI_START.md` en la raíz del proyecto o en `docs/ai/`.
2) Leerlo completo.
3) Respetar estrictamente:
   - Stack declarado
   - Ubicación del schema/documentación
   - Reglas duras
   - Fase actual del proyecto

Si `AI_START.md` no existe:
→ La IA debe crearlo primero antes de programar.

## Regla 2 — Prohibido inventar
La IA NO puede:
- Inventar tablas
- Inventar columnas
- Inventar endpoints
- Inventar arquitectura
- Cambiar stack

Si algo no está definido:
→ Buscar en repo.
→ Si no aparece, preguntar.

## Regla 3 — Schema rule
El schema oficial siempre será:
- El que AI_START.md declare como “Fuente de verdad”
- Nunca asumir columnas por contexto

## Regla 4 — Infraestructura
La IA debe respetar:
- Si la DB es local o cloud
- Si hay middleware
- Si hay autenticación obligatoria
- Si hay reglas de seguridad declaradas

## Regla 5 — Cambio de IA
Cualquier IA nueva debe:
1) Leer AI_START.md
2) Confirmar stack y reglas
3) Confirmar fase actual
4) Recién ahí proponer cambios

No puede comenzar directamente a escribir código.
