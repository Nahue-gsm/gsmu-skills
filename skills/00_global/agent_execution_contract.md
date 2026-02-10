# Agent Execution Contract (GSMU) — Cómo debe trabajar un agente con estas skills

## Objetivo
Asegurar que cualquier agente que use `gsmu-skills` trabaje de forma:
- consistente
- verificable
- segura
- orientada a resultados
y sin “magia” ni decisiones inventadas.

---

## 0) Definiciones
- **Intake**: fase de decisiones (qué + con qué). No produce código productivo.
- **Routing**: selección determinística de skills mediante `registry.yml` + `skill_router.md`.
- **Execution**: aplicar skills elegidas y generar outputs.
- **Ops/Release**: checklist, changelog, control de calidad, entrega.

---

## 1) Fuente de verdad (Source of Truth)
El agente DEBE usar este orden de fuentes:

1) `project_context.md` (decisiones cerradas del proyecto)
2) `project_brief.md` (objetivo, alcance, entregables)
3) `skills/registry.yml` (qué skills existen y para qué)
4) `skills/00_global/skill_router.md` (orden y selección)
5) `skills/95_external_wrappers/` (cómo aplicar skills externos)
6) Skills específicas del pack (Electron/Web/Ops)

Regla:
- Si una respuesta ya está en `project_context.md`, el agente NO pregunta eso de nuevo.

---

## 2) Estados de trabajo (State Machine)
El agente SIEMPRE opera en 4 estados secuenciales:

### Estado A — INTAKE
- Leer contexto.
- Detectar faltantes críticos.
- Preguntar SOLO lo que cambia arquitectura/stack/persistencia/deploy/costos/riesgos.
- Output: decisiones cerradas + actualización de context/brief.

### Estado B — ROUTING
- Con decisiones cerradas, generar un `skill_plan` usando router + registry.
- Si el skill es externo:
  - usar wrapper GSMU si existe
  - si no existe wrapper, crear wrapper mínimo (antes de ejecutar)

### Estado C — EXECUTION
- Ejecutar skills del `skill_plan` en orden.
- Generar outputs en los paths acordados.
- No saltarse validaciones.
- Si aparece ambigüedad nueva: volver a INTAKE (solo si afecta decisiones).

### Estado D — OPS/RELEASE
- Ejecutar checklist de release.
- Actualizar changelog si aplica.
- Entregar resumen final + próximos pasos.

---

## 3) Reglas de comportamiento (Hard Rules)
### 3.1 No inventar
- No inventar features “existentes”, endpoints, tablas, datos, métricas, clientes, testimonios.
- Si falta info: marcar como `[TODO]` y proponer opciones concretas.

### 3.2 Cambios atómicos
- No tocar 10 cosas a la vez.
- Cuando se debugea: 1 hipótesis, 1 cambio, 1 verificación.

### 3.3 Outputs obligatorios
El agente nunca “termina” si no produce outputs verificables:
- archivos / diffs / listas / reportes
- con nombres y paths claros

### 3.4 Separación de responsabilidades
- Intake NO produce código de producción.
- Router NO pregunta al usuario.
- Execution NO “redefine” arquitectura.
- Ops NO agrega features nuevas.

### 3.5 Seguridad y supply-chain
- No ejecutar comandos dudosos o no verificados.
- Para skills externos:
  - preferir wrappers GSMU
  - no copiar/pegar comandos sin validación
- No exponer secretos (tokens, passwords, keys) en archivos.

---

## 4) Formato de entrega (siempre igual)
Al finalizar cualquier intervención, el agente debe entregar:

1) **Qué se hizo** (2–8 bullets)
2) **Qué archivos se crearon/modificaron** (lista con paths)
3) **Cómo verificar** (pasos simples)
4) **Riesgos o TODOs** (si existen)
5) **Siguiente acción recomendada** (1 paso)

---

## 5) Debug Mode (obligatorio ante bugs)
Si el usuario reporta un bug o comportamiento raro:
- Se activa `workflow.systematic-debugging` como paso 1.
- Output obligatorio: `debug_report.md`
- No se aplican “fixes creativos” sin evidencia.

---

## 6) Calidad mínima (Acceptance Checklist)
Antes de declarar “listo”, el agente debe comprobar:
- el output existe (archivo, ruta, artefacto)
- no hay contradicciones con `project_context.md`
- si es UI: estados loading/empty/error definidos
- si es backend: manejo de errores consistente
- si es release: changelog/checklist actualizado

---

## 7) Criterio de escalamiento (cuando pedir ayuda o info)
El agente SOLO pide clarificación si:
- cambia arquitectura/stack/persistencia/deploy/costos/riesgos
- no puede decidir entre 2 opciones sin impactar maintenance o costos

Si no cambia nada de eso:
- asumir defaults GSMU
- avanzar y documentar la asunción en `project_context.md`

---
