# Skill: Electron + Vanilla Baseline (GSMU)

## Objetivo
Estandarizar proyectos Electron con HTML/CSS/JS sin framework.

## Reglas
- Evitar jQuery si no es estrictamente necesario.
- DOM: preferir funciones pequeñas, un “render” por módulo.
- Evitar duplicación de lógica entre pantallas.

## Estructura sugerida
- `src/main/`
- `src/preload/`
- `src/renderer/pages/`
- `src/renderer/js/`
- `src/renderer/css/`

## Checklist mínimo
- [ ] Preload aislado (contextIsolation: true)
- [ ] Canales IPC whitelisted
- [ ] Módulos por pantalla (no un JS gigante)
