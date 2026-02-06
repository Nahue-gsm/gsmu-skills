# Skill: Packaging con electron-builder (GSMU Standard)

## Objetivo
Empaquetar apps Electron de forma consistente usando electron-builder.

## Cuándo aplicar
Cuando `project_context.md` indique:
- Desktop Electron
- Packaging/Deploy: electron-builder

## Reglas
- Mantener `build/` (iconos, resources) organizado
- `dist/` y `node_modules/` NO se versionan
- Versionado semver (x.y.z)

## Config recomendada (alto nivel)
- Target Windows:
  - nsis (instalador)
  - portable (opcional)
- Iconos:
  - `.ico` para Windows
- Artifact naming:
  - `AppName-Setup-x.y.z.exe`
  - `AppName-Portable-x.y.z.exe`

## Checklist release
- [ ] App version actualizada
- [ ] Iconos correctos
- [ ] `appId` definido y estable
- [ ] `productName` coherente
- [ ] Firma (si aplica)
- [ ] Prueba instalación limpia
