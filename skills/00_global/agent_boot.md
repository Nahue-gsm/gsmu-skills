# Agent Boot (GSMU) — Cómo debe arrancar SIEMPRE un agente

## Propósito
Definir el **procedimiento mínimo obligatorio** que un agente debe seguir al iniciar cualquier trabajo usando `gsmu-skills`.

Este archivo se lee **antes de ejecutar cualquier skill**.

---

## Secuencia obligatoria de arranque

### Paso 0 — Leer “Start Here” (si existe)
Leer primero, en este orden (si existen):
1) `AI_START.md`
2) `docs/ai/AI_START.md`

Reglas:
- Si existe `AI_START.md`, **NO adivinar** stack, DB, rutas, ni estructura: usar ese archivo como fuente de verdad.
- Si NO existe, crear uno ejecutando: `skills/00_global/project_ai_start_manifest.md`.

### Paso 1 — Leer contexto
Leer en este orden:
1) `project_context.md`
2) `project_brief.md` (si existe)

Regla:
- NO preguntar cosas que ya estén respondidas en estos archivos.

---

### Paso 2 — Determinar estado inicial
Clasificar el trabajo en uno de estos estados:
- INTAKE (faltan decisiones)
- ROUTING (decisiones cerradas, falta plan de skills)
- EXECUTION (hay `skill_plan`)
- OPS / RELEASE (solo cierre, checklist, changelog)

Si hay duda → asumir **INTAKE**.

---

### Paso 3 — INTAKE (si aplica)
Si faltan decisiones críticas:
- Ejecutar `skills/00_global/project_intake_orchestrator.md`
- Preguntar SOLO lo que impacte:
  - arquitectura
  - stack
  - persistencia
  - deploy
  - costos
  - riesgos

Output obligatorio:
- `project_context.md` actualizado
- `project_brief.md` actualizado o creado

---

### Paso 4 — ROUTING
Con decisiones cerradas:
- Consultar `skills/registry.yml`
- Ejecutar `skills/00_global/skill_router.md`
- Generar `skill_plan` (lista ordenada)

Reglas:
- El router NO pregunta al usuario.
- Si un skill es externo:
  - usar wrapper GSMU en `skills/95_external_wrappers/` si existe
  - si no existe wrapper → crear wrapper mínimo ANTES de ejecutar

Output obligatorio:
- `skill_plan`
- lista de wrappers usados (si aplica)

---

### Paso 5 — EXECUTION
- Ejecutar skills del `skill_plan` **en orden**.
- Generar outputs en los paths definidos por cada skill.
- No redefinir arquitectura ni stack.
- Si surge ambigüedad que afecta decisiones:
  - volver a INTAKE
  - documentar el cambio en `project_context.md`

Output obligatorio:
- Archivos/artefactos producidos por cada skill

---

### Paso 6 — OPS / RELEASE (si aplica)
- Ejecutar checklist de `90_ops/`
- Actualizar `CHANGELOG.md` si corresponde
- Verificar outputs finales

---

## Reglas de oro
- Sin contexto → no hay ejecución.
- Sin `skill_plan` → no hay ejecución.
- Sin outputs verificables → el trabajo NO está terminado.
- Ante bugs → activar `workflow.systematic-debugging` primero.

---

## Formato de cierre obligatorio
Al finalizar cualquier intervención, entregar siempre:

1) Qué se hizo  
2) Qué archivos se tocaron (paths)  
3) Cómo verificar  
4) Riesgos / TODOs  
5) Próximo paso recomendado
