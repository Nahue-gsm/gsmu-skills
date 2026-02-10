# Skill: Skill Router (GSMU) — Selección determinística de skills

## Objetivo
Dado un `project_context.md` y/o decisiones finales del intake, elegir **qué skills ejecutar y en qué orden** usando:
- `skills/registry.yml` (fuente de verdad de IDs)
- Wrappers en `skills/95_external_wrappers/` si el skill es externo

## Hard Rules
- Siempre devolver una lista ordenada: `skill_plan`
- Si un skill es `external`, preferir wrapper GSMU si existe.
- Si NO existe wrapper GSMU para un external skill: crear wrapper mínimo antes de “aplicar” el skill externo.
- No mezclar intake con ejecución: acá NO se pregunta al usuario, solo se enruta.

---

## Inputs esperados
- `project_type`: Desktop | Web | Backend/API | Automatización/Scripts
- `ui_type` (si aplica): Public/Marketing | Dashboard/Tool
- `stack`: (React/Vanilla/Next, PHP/Node, DB, etc.)
- `constraints`: (offline, multi-sucursal, impresoras, export, etc.)
- `stage`: MVP | Iteración | Refactor | Release

---

## Routing base (determinístico)

### A) Web — UI pública / marketing (Landing / institucional)
Orden sugerido:
1) `ui.frontend-design` (wrapper: `95_external_wrappers/ui_frontend_design_gsmu_wrapper.md`)
2) `20_web/landing_baseline.md` (si existe en tu pack)
3) `react.vercel-best-practices` (solo si stack = React/Next)
4) `ops.changelog-generator` (si stage incluye release)

### B) Web/App — Dashboard / Admin / herramienta interna
Orden sugerido:
1) `ui.interface-design` (wrapper: `95_external_wrappers/ui_interface_design_gsmu_wrapper.md`)
2) Skill base del proyecto (web/app interna) según tu pack
3) `backend.error-handling-patterns` (si hay API/DB)
4) `react.vercel-best-practices` (solo si stack = React/Next)

### C) Desktop (Electron)
Orden sugerido:
1) Baseline Electron (según tu pack):
   - `10_desktop_electron/electron_react_baseline.md` o `electron_vanilla_baseline.md`
2) `10_desktop_electron/ipc_security_preload.md`
3) Persistencia:
   - `10_desktop_electron/db_local_better_sqlite3.md` (si local)
   - o skill de API (si nube)
4) Packaging:
   - `10_desktop_electron/packaging_electron_builder.md`
5) Opcionales por requerimiento:
   - impresión ESC/POS, export PDF/Excel, roles, etc.

### D) Backend / API
Orden sugerido:
1) `backend.api-design-principles`
2) `backend.error-handling-patterns`
3) DB:
   - `db.postgresql` (si Postgres)
   - (si MySQL, usar skill interno tuyo cuando exista)
4) `ops.changelog-generator` (si stage incluye release)

### E) Debug / Bugfix (cualquier proyecto)
Orden obligatorio:
1) `workflow.systematic-debugging` (wrapper: `95_external_wrappers/workflow_systematic_debugging_gsmu_wrapper.md`)
2) Luego recién skills específicos según el área (UI/API/DB/Electron)

---

## Output obligatorio: skill_plan
Formato recomendado:

- `skill_plan` (lista ordenada de IDs o paths)
- `notes` (por qué se eligieron)
- `wrappers_used` (si aplica)

Ejemplo:
skill_plan:
- ui.interface-design
- 10_desktop_electron/electron_react_baseline.md
- 10_desktop_electron/ipc_security_preload.md
wrappers_used:
- 95_external_wrappers/ui_interface_design_gsmu_wrapper.md
notes:
- "Es herramienta interna tipo dashboard; priorizar productividad y estados."
