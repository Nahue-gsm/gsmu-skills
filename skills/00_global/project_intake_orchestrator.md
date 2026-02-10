# Skill: Project Intake Orchestrator (GSMU) — Flow de trabajo

## Objetivo
Transformar una idea en:
1) Decisiones generales cerradas (tipo + stack + restricciones)
2) `project_context.md` completo
3) `project_brief.md`
4) Contexto suficiente para que el Skill Router seleccione skills específicas

---

## Hard Rules
- No generar código de producción en esta fase.
- No decidir orden de ejecución de skills.
- Preguntar SOLO lo que cambie arquitectura, stack, persistencia, deploy, costos o riesgos.
- Máximo recomendado: 8–14 preguntas (con branching).
- Si `project_context.md` ya contiene una respuesta, NO preguntar.

---

## Skill Registry & Routing (obligatorio)
- La selección de skills se basa en `skills/registry.yml`.
- El enrutamiento determinístico de skills se resuelve exclusivamente en:
  - `skills/00_global/skill_router.md`
- Este archivo (intake) NO define:
  - orden de ejecución
  - combinación de skills
- Si un skill es externo, el router debe usar un wrapper GSMU en:
  - `skills/95_external_wrappers/` (si existe)
- Si NO existe wrapper GSMU para un skill externo:
  - se debe crear uno mínimo antes de su aplicación.

---

## Diagrama de flujo (alto nivel)

START
  |
  v
[Leer project_context.md]
  |
  v
¿Falta info crítica?
  |--- no ---> [Generar/actualizar Project Brief] ---> END
  |
  '--- sí ---> [Fase 1: Definir QUÉ] ---> [Fase 2: Definir CON QUÉ] ---> [Fase 3: Cierre] ---> END

(La selección de skills ocurre luego mediante Skill Router)

---

## Fase 1 — Definir QUÉ vamos a hacer (clasificación)
Preguntas (condicionales):

1) Tipo de proyecto:
   - Desktop (Electron)
   - Web (Landing / Ecommerce / Panel)
   - Backend / API
   - Automatización / Scripts

2) Caso de uso y entorno:
   - uso interno / cliente final
   - una PC / múltiples puestos / multi-sucursal

3) Restricciones principales:
   - offline requerido (sí/no)
   - hardware especial (impresoras, lector QR, tablets, etc.)
   - plazos y riesgos (corto / medio / largo)

### Salida mínima de Fase 1
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
- Persistencia:
  - local (SQLite)
  - nube (API + MySQL)
  - híbrido (sync)
- Requisitos:
  - impresión (ESC/POS)
  - export Excel / PDF
  - roles / usuarios

**Default GSMU (si no se especifica):**
- Electron + React + TypeScript
- SQLite local con better-sqlite3
- Packaging con electron-builder

---

### Si es Web
Preguntar:
- Hosting disponible:
  - PHP
  - Node
  - solo estático
- ¿Necesita base de datos o solo contacto?
- SEO / performance / analytics
- ¿Admin / panel interno? (sí/no)

---

## Fase 3 — Cierre (resumen y decisiones)
1) Presentar:
   - 1 recomendación principal
   - 1 alternativa razonable (si aplica)
2) Confirmar decisiones finales (sin extenderse).
3) Declarar explícitamente:
   - tipo de proyecto
   - tipo de UI (si aplica)
   - stack confirmado
   - restricciones finales
   - **stage del proyecto**: `MVP | Iteración | Refactor | Release`
4) Escribir o actualizar:
   - `project_context.md`
   - `project_brief.md` (usando template oficial)

---

## Fase 4 — Preparación para selección de skills
El intake **NO selecciona skills concretas**.

Su responsabilidad es garantizar que:
- `project_context.md` contiene toda la información necesaria
- las decisiones están cerradas y explícitas
- el proyecto puede ser enrutado automáticamente por el Skill Router

La selección y el orden de ejecución de skills se resuelven luego mediante:
- `skills/00_global/skill_router.md`

---

## Output final (obligatorio)
- Un `project_brief.md` completo
- `project_context.md` actualizado y consistente
- Contexto suficiente para generar un `skill_plan` vía Skill Router

