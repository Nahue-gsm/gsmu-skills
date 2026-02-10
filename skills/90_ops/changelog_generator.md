# Skill: Changelog Generator (GSMU Wrapper)

## Objetivo
Generar `CHANGELOG.md` a partir del historial de commits y/o PRs, siguiendo formato consistente.

## Inputs
- Rango: última release tag -> HEAD (o último release date -> hoy)
- Lista de features/fixes relevantes (si existe)
- Convención de commits (si aplica)

## Output (obligatorio)
- `CHANGELOG.md` actualizado

## Reglas
- No inventar features.
- Si hay duda, marcar como "Uncategorized" o pedir confirmación en project context.

## Pasos
1) Identificar último tag/release o punto de corte.
2) Agrupar cambios por:
   - Added / Changed / Fixed / Security
3) Escribir entrada con fecha y versión.
4) Verificación final: que el texto refleje commits reales.
