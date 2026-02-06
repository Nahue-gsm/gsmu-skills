# Tech Stack Catalog (GSMU)

## Desktop (Electron)
### Opción A (default): Electron + React + TypeScript
- Ideal para: apps que crecen, paneles, formularios, tablas, dashboards
- Pros: mantenible, componentes reutilizables, escalable
- Contras: build/tooling y estructura inicial

### Opción B: Electron + Vanilla (HTML/CSS/JS)
- Ideal para: apps simples, utilidades rápidas, 1–3 pantallas
- Pros: mínima complejidad, rápido de arrancar
- Contras: cuando crece, el DOM se vuelve difícil de mantener

## Persistencia
### Local SQLite + better-sqlite3 (default)
- Ideal para: offline, 1 PC o pocos puestos, performance y simplicidad
### Nube (API + MySQL)
- Ideal para: multi-sucursal, acceso remoto, suscripción
### Híbrido (sync)
- Ideal para: offline + sync eventual (más complejo)

## Packaging
- electron-builder (default): instalador/portable, firma, auto-update opcional

## Nota
Si el proyecto no define stack explícito, usar defaults GSMU.
