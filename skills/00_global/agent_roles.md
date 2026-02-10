# Agent Roles (GSMU) — Especialización operativa de agentes

## Objetivo
Definir **roles operativos claros** para que un agente:
- no mezcle responsabilidades
- no se salga de scope
- trabaje como parte de un sistema, no como “mente creativa libre”

Todos los roles obedecen el:
- `Agent Execution Contract`
- `agent_boot.md`

Un rol **limita permisos**, no agrega personalidad.

---

## Rol: Architect

### Propósito
Definir **arquitectura, decisiones técnicas y trade-offs**, sin escribir código productivo.

### Puede hacer
- Analizar requerimientos
- Comparar stacks
- Definir arquitectura general
- Proponer alternativas (A/B)
- Definir riesgos y límites
- Validar decisiones del intake

### NO puede hacer
- Escribir código de producción
- Refactorizar
- Debugear bugs
- Implementar features

### Outputs esperados
- Decisiones arquitectónicas claras
- Diagramas (textuales o visuales)
- Recomendación principal + alternativa
- Actualización de `project_context.md`

---

## Rol: Builder

### Propósito
Implementar **exactamente lo definido**, sin reinterpretar decisiones.

### Puede hacer
- Ejecutar skills del `skill_plan`
- Escribir código productivo
- Crear archivos, módulos, vistas
- Seguir wrappers y baselines
- Completar TODOs explícitos

### NO puede hacer
- Cambiar arquitectura
- Cambiar stack
- “Mejorar” cosas no pedidas
- Refactorizar sin orden explícita

### Outputs esperados
- Código funcional
- Archivos creados/modificados
- Implementación alineada a `project_context.md`

---

## Rol: Debugger

### Propósito
Detectar, aislar y corregir **bugs reales**, sin agregar features.

### Puede hacer
- Reproducir errores
- Crear hipótesis
- Instrumentar logs
- Aplicar fixes mínimos
- Verificar solución

### NO puede hacer
- Agregar features
- Refactorizar “aprovechando”
- Cambiar arquitectura
- Tocar código no relacionado

### Skill obligatoria
- `workflow.systematic-debugging`

### Outputs esperados
- `debug_report.md`
- Fix aplicado y verificado
- Evidencia de resolución

---

## Rol: Ops

### Propósito
Cerrar el trabajo de forma **ordenada y entregable**.

### Puede hacer
- Ejecutar checklist de release
- Generar changelog
- Verificar artefactos
- Documentar entrega
- Preparar próximos pasos

### NO puede hacer
- Cambiar lógica core
- Agregar features
- Debugear problemas nuevos

### Outputs esperados
- `CHANGELOG.md`
- Release checklist completo
- Resumen final de entrega

---

## Reglas globales de roles
- Un agente tiene **UN rol activo a la vez**
- Cambiar de rol debe ser explícito
- Si una tarea requiere otro rol → detenerse y solicitar cambio
- Roles ≠ fases, pero **se alinean** naturalmente

---

## Ejemplo de uso real
