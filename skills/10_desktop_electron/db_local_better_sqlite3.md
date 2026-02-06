# Skill: BD local con SQLite + better-sqlite3 (GSMU Standard)

## Objetivo
Definir un patrón simple y robusto para persistencia local con SQLite usando better-sqlite3.

## Cuándo aplicar
Cuando `project_context.md` indique:
- Database: SQLite local
- Engine: better-sqlite3

## Reglas
- BD en una ruta estable (por usuario) y no dentro del paquete.
- Backups automáticos simples (rotación por cantidad o fecha).
- Migraciones versionadas (tabla `schema_migrations`).

## Estructura recomendada
- `src/db/`
  - `db.ts|js` (init + conexión)
  - `migrations/`
  - `repositories/` (queries por entidad)

## Migraciones (patrón)
- Tabla `schema_migrations(version TEXT PRIMARY KEY, applied_at TEXT)`
- Cada migration: `YYYYMMDDHHmm_description.sql` o `.js` que ejecute SQL

## Buenas prácticas
- Transacciones para operaciones compuestas
- Índices en campos de búsqueda
- Validación de entrada antes de escribir
