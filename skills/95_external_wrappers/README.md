# GSMU External Wrappers (95)

## Objetivo
Estandarizar el uso de skills externos (links) para que sean:
- determinísticos (mismo input -> mismo output)
- compatibles con GSMU Hard Rules
- seguros (sin comandos dudosos o cambios inesperados)

## Regla de oro
En GSMU no se “usa un skill externo directo” en proyectos reales.
Primero se aplica un WRAPPER GSMU (este folder) que define:
- cuándo usarlo
- cómo integrarlo al flujo GSMU
- inputs mínimos y outputs obligatorios
- límites (qué NO hacer)

## Política de versiones (pinned refs)
- Preferir URL a commit/tag.
- Si el repo externo no permite pin fácil, usar `pinned_ref: main` y registrar la fecha en el registry.
- No ejecutar comandos que no estén verificados por docs oficiales del proyecto.

## Formato estándar de wrapper
Cada wrapper debe incluir:
1) Qué resuelve y qué NO
2) Preconditions (qué info ya debe existir)
3) Inputs requeridos
4) Steps (pasos concretos en GSMU)
5) Outputs obligatorios (archivos/artefactos)
6) Checklist de verificación

## Cómo se referencia
El `project_intake_orchestrator.md` selecciona skills por ID del `registry.yml`.
Si un skill es external, se usa el wrapper GSMU si existe.
