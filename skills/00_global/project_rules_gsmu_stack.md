# Skill Global: Reglas del Proyecto (GSM Universe Stack)

## Objetivo
Unificar criterios técnicos y de calidad para todos los proyectos y agentes.
Reducir reprocesos, decisiones improvisadas y stacks inconsistentes.

## Principios
- simple > complejo
- robusto > moderno
- mantenible > elegante
- pocas dependencias > muchos frameworks
- primero claridad, después optimización
- seguridad y datos del cliente primero

## Reglas operativas
1) No escribir “código final” hasta definir: tipo de proyecto + stack + persistencia + despliegue.
2) Preferir soluciones con menor superficie de fallas (menos moving parts).
3) Mantener consistencia entre proyectos: mismas libs por defecto, mismos patrones.
4) No introducir una librería nueva si el problema se resuelve razonablemente con las ya aprobadas.
5) Cualquier decisión de arquitectura debe quedar escrita en `project_context.md` o en el `project_brief.md`.

## Estándares por defecto (si el proyecto no especifica)
### Desktop (Electron)
- UI: React (si no se pide vanilla)
- Lenguaje: TypeScript (si el equipo lo tolera; sino JS con reglas estrictas)
- Persistencia local: SQLite
- Acceso a SQLite: better-sqlite3 (por simplicidad y performance)
- Empaquetado: electron-builder
- IPC seguro: preload + contextBridge + canales whitelisted

### Web
- Landing simple: estático o PHP (según hosting)
- Formularios: endpoint backend + validación server-side
- DB: MySQL si es hosting tradicional

## Calidad mínima
- Estructura de carpetas consistente
- Logs útiles (sin filtrar secretos)
- Manejo de errores: mensajes claros y fallback
- No hardcodear credenciales
- README actualizado con:
  - cómo correr
  - cómo build
  - cómo release
  - cómo configurar .env

## Gate de decisiones

Si durante el análisis o ejecución el agente detecta una alternativa potencialmente mejor,
debe:
- notificar como "PROPUESTA DE MEJORA"
- explicar impacto y trade-offs
- esperar aprobación explícita del usuario antes de ejecutar


