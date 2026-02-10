# Wrapper GSMU — Systematic Debugging (Superpowers)

## External Skill (source)
- Nombre: Systematic Debugging Skill (Superpowers)
- URL: https://github.com/obra/superpowers

## Objetivo (GSMU)
Resolver bugs con un proceso repetible:
- reproducible
- medible
- con hipótesis
- con verificación final
Evitar el anti-patrón: “tocar cosas hasta que ande”.

## Cuándo usar
- Bug intermitente
- Error en producción
- Algo “no crea el archivo”, “no guarda”, “a veces falla”
- Problemas con APIs, CORS, permisos, packaging, rutas, build, etc.

## Cuándo NO usar
- Fase de ideación (usar brainstorming)
- Diseño UI (usar wrappers UI)
- Tareas triviales sin ambigüedad

## Inputs requeridos (mínimos)
- Qué debería pasar vs qué pasa
- Cómo reproducir (pasos)
- Logs / errores (stack trace) si existen
- Entorno:
  - OS
  - versión node/electron/php
  - modo (dev/prod)
  - rutas relevantes
- Último cambio antes de romperse (si se sabe)

## Flow GSMU (pasos)
### Paso 1 — Definir “Definition of Done”
- Se considera resuelto cuando:
  - reproduce 0/10 intentos (o criterio acordado)
  - tests/manual checklist pasa
  - no rompe casos relacionados

### Paso 2 — Reproducir (sin esto no se avanza)
- Crear “Minimal Repro Steps”
- Registrar:
  - frecuencia del fallo
  - input exacto
  - output actual

### Paso 3 — Hipótesis (máximo 3)
Ejemplos:
- path incorrecto en producción
- permisos/ESM/CJS
- dependencia no instalada en build
- race condition
- API responde distinto

### Paso 4 — Instrumentación (logs que sirven)
- Agregar logs/prints temporales:
  - entradas
  - rutas
  - valores clave
  - errores completos
- Si aplica: activar verbose mode
- Guardar evidencia: “antes/después”

### Paso 5 — Probar una hipótesis por vez
- Cambiar UNA cosa
- Repetir repro
- Documentar resultado:
  - confirmado / descartado

### Paso 6 — Fix mínimo + limpieza
- Aplicar fix mínimo
- Quitar logs temporales (o dejarlos detrás de flag)
- Agregar guardrails (validaciones)

### Paso 7 — Verificación final
- Checklist:
  - repro original pasa
  - 2–3 casos borde pasan
  - no hay regresiones obvias

## Outputs obligatorios
- `debug_report.md` con:
  - Repro steps
  - Entorno
  - Hipótesis + resultados
  - Root cause confirmado
  - Fix aplicado (resumen)
  - Verificación final (checklist)

## Hard Rules GSMU
- No tocar 5 cosas a la vez.
- No “asumir” root cause sin evidencia.
- Si no se puede reproducir: convertir en “observabilidad” primero.
