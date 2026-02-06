# GSMU Skills Pack (Flow-first)

Este repo contiene un set de *skills* reutilizables para agentes, con una forma de trabajo orientada a **flujo**:

1) **Definir lo general** (qué vamos a construir + restricciones + stack)
2) **Cerrar decisiones base** (persistencia, empaquetado, arquitectura)
3) **Ejecutar skills específicas** (DB, packaging, impresión, etc.)
4) **Operación / release** (git, checklist, versiones)

## Cómo usar
- Cada proyecto tiene su propio `project_context.md` en la raíz del repo (o dentro de una carpeta de proyecto).
- El agente siempre debe ejecutar primero:  
  `skills/00_global/project_intake_orchestrator.md`
- El resultado de esa fase debe producir/actualizar:
  - `project_context.md`
  - `project_brief.md` (usando el template)
  - una lista de skills específicas a aplicar

## Estructura
- `skills/00_global/` reglas y orquestación (intake + templates)
- `skills/10_desktop_electron/` baselines Electron + módulos (DB, packaging, impresión, IPC)
- `skills/20_web/` baselines web (landing, PHP)
- `skills/90_ops/` git, releases, checklist

## Principios (GSMU Stack)
- simple > complejo
- robusto > moderno
- mantenible > elegante
- pocas dependencias > muchos frameworks

## Nota
El objetivo es que el agente no improvise: **primero decide**, luego **ejecuta**.
