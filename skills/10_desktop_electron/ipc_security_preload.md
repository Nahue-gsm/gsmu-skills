# Skill: Seguridad IPC + Preload (GSMU)

## Objetivo
Evitar que el renderer tenga acceso libre a Node y reducir superficie de ataque.

## Reglas
- `contextIsolation: true`
- `nodeIntegration: false`
- Exponer API mínima por `contextBridge`
- Whitelist de canales IPC
- Validación estricta de inputs en main

## Patrón recomendado
- `preload` expone `window.api`
- `window.api` solo tiene métodos necesarios
- En main: `ipcMain.handle('channel', handler)` con validación
