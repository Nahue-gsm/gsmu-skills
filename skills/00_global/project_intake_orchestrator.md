# Skill: Project Intake Orchestrator (GSMU) — Flow de trabajo

## Objetivo
Transformar una idea en:
1) Decisiones generales cerradas (tipo + stack + restricciones)
2) `project_context.md` completo
3) `project_brief.md`
4) Lista de skills específicas a ejecutar

## Hard Rules
- No generar código de producción en esta fase.
- Preguntar SOLO lo que cambie arquitectura, stack, persistencia, deploy, costos o riesgos.
- Máximo recomendado: 8–14 preguntas (con branching).
- Si `project_context.md` ya contiene una respuesta, NO preguntar.

## Skill Registry & Routing (obligatorio)
- La selección de skills se hace por `skills/registry.yml` (IDs).
- Si un skill es externo, se debe usar el wrapper GSMU en `skills/95_external_wrappers/` si existe.
- Si NO existe wrapper: crear un wrapper mínimo antes de aplicar el skill externo.

## Routing base (determinístico)
- UI pública / landing / marketing:
  - `ui.frontend-design` -> (si React/Next) `react.vercel-best-practices` -> `ops.changelog-generator`
- Dashboard / admin / herramienta interna:
  - `ui.interface-design` -> (si React/Next) `react.vercel-best-practices` -> `backend.error-handling-patterns`
- Backend/API:
  - `backend.api-design-principles` -> `backend.error-handling-patterns` -> (si aplica) `db.postgresql`
- Debug:
  - `workflow.systematic-debugging` (siempre primero)


---

## Diagrama de flujo (alto nivel)

START
  |
  v
[Leer project_context.md]
  |
  v
¿Falta info crítica?
  |--- no ---> [Generar/actualizar Project Brief] ---> [Seleccionar skills específicas] ---> END
  |
  '--- sí ---> [Fase 1: Definir QUÉ] ---> [Fase 2: Definir CON QUÉ] ---> [Resumen y cierre] ---> [Project Brief + skills] ---> END

---

## Fase 1 — Definir QUÉ vamos a hacer (clasificación)
Preguntas (condicionales):
1) Tipo de proyecto:
   - Desktop (Electron)
   - Web (Landing / Ecommerce / Panel)
   - Backend/API
   - Automatización/Scripts
2) Caso de uso y entorno:
   - uso interno / cliente final
   - una PC / múltiples puestos / multi-sucursal
3) Restricciones:
   - offline requerido (sí/no)
   - hardware especial (impresoras, lector QR, tablets, etc.)
   - plazos y riesgos (corto/medio/largo)

Salida mínima de Fase 1:
- Project type
- Target users / scope
- Constraints principales

---

## Fase 2 — Definir CON QUÉ lo vamos a hacer (stack)
### Si es Desktop (Electron)
Preguntar:
- UI: Vanilla o React
- Lenguaje: JS o TS
- Ventanas: single window (SPA) o multi-ventana
- Persistencia: local (SQLite) / nube (API + MySQL) / híbrido (sync)
- Requisitos: impresión (ESC/POS), export Excel/PDF, roles/usuarios

**Default GSMU (si no se especifica):**
- Electron + React + TypeScript
- SQLite local con better-sqlite3
- Packaging con electron-builder

### Si es Web
Preguntar:
- Hosting: ¿PHP disponible? ¿Node? ¿solo estático?
- ¿Necesita DB o solo contacto?
- SEO / performance / analytics
- Admin/panel: sí/no

---

## Fase 3 — Cierre (resumen y decisiones)
1) Presentar 1 recomendación principal y 1 alternativa.
2) Confirmar decisiones finales (sin extenderse).
3) Escribir/actualizar:
   - `project_context.md`
   - `project_brief.md` (usando template)

---

## Fase 4 — Selección de skills específicas
Con las decisiones finales, listar skills a ejecutar, por ejemplo:

- Desktop Electron:
  - `10_desktop_electron/electron_react_baseline.md` o `electron_vanilla_baseline.md`
  - `10_desktop_electron/ipc_security_preload.md`
  - `10_desktop_electron/db_local_better_sqlite3.md` (si SQLite local)
  - `10_desktop_electron/packaging_electron_builder.md` (si packaging)
  - `10_desktop_electron/printing_escpos.md` (si impresión térmica)

- Web:
  - `20_web/landing_baseline.md`
  - `20_web/php_backend_baseline.md` (si aplica)

---

## Output final (obligatorio)
- Un `project_brief.md` completo
- `project_context.md` actualizado
- Lista de skills a ejecutar en orden
