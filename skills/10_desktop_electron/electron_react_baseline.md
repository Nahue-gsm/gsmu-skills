# Skill: Electron + React Baseline (GSMU)

## Objetivo
Estandarizar proyectos Electron con React para una base mantenible y repetible.

## Reglas
- Preferir TypeScript salvo que el proyecto lo prohíba.
- Evitar acceso directo a Node en renderer: usar preload + IPC.
- UI por componentes, estado claro, rutas si aplica.

## Estructura sugerida
- `src/main/` (proceso main)
- `src/preload/` (contextBridge)
- `src/renderer/` (React UI)
- `assets/` (iconos, recursos)

## Stack recomendado
- Bundler: Vite (si se usa React)
- UI: React
- Estado: simple primero (useState/useReducer), luego Zustand/Redux si hace falta
- Forms: react-hook-form si el proyecto es heavy en forms
- Validación: zod si aplica

## Checklist mínimo
- [ ] Preload aislado (contextIsolation: true)
- [ ] Canales IPC whitelisted
- [ ] Logger básico (sin secretos)
- [ ] Manejo de errores de IPC con mensajes claros
