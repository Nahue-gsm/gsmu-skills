# GSMU Skills Pack (Flow-first)

Este repo contiene un set de *skills* reutilizables para agentes, con una forma de trabajo orientada a **flujo**:

1) **Definir lo general** (qué vamos a construir + restricciones + stack propuesto)
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

## Acceso a skills (entorno del agente)

Este repositorio asume que los skills existen como archivos versionados.

- Si el agente puede leer archivos o URLs, debe consultar directamente los skills.
- Si el agente NO puede leer archivos en su entorno:
  - debe trabajar bajo el supuesto de que estos skills existen
  - no debe inventar reglas que los contradigan
  - debe indicar explícitamente qué skill está aplicando en cada decisión

## Cierre de proyecto (Post-mortem)

El proyecto se considera finalizado solo cuando el usuario lo indica explícitamente.

Al cierre, el agente debe producir:
- qué funcionó
- qué no funcionó
- decisiones a corregir
- mejoras a skills existentes
- nuevos skills sugeridos

El objetivo es retroalimentar este repositorio.


## Gate de decisiones (notificar antes de cambiar)

Cuando el agente detecte una opción potencialmente mejor (stack, arquitectura, librería, flujo, seguridad, costos, mantenimiento), debe:

1) Notificarlo explícitamente como "PROPUESTA DE MEJORA".
2) Explicar brevemente:
   - Qué cambiaría
   - Por qué sería mejor (beneficio)
   - Riesgo / costo de cambio
   - Impacto en tiempo/alcance
3) No ejecutar ese cambio hasta recibir una respuesta del usuario con una de estas palabras clave:
   - "APROBADO: <opción>"
   - "RECHAZADO: <opción>"
   - "EVALUAR ALTERNATIVAS"

Mientras no haya respuesta, el agente continúa solo con lo ya aprobado.

Este gate aplica solo a cambios MATERIALES (seguridad, arquitectura, stack, costos, mantenimiento o alcance).





