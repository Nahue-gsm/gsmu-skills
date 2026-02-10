# Wrapper GSMU — Interface Design (Dashboards / Tools)

## External Skill (source)
- Nombre: Interface Design
- URL: https://skills.sh/dammyjay93/interface-design/interface-design

## Objetivo (GSMU)
Diseñar interfaz para **producto/herramienta**:
- dashboards
- panel admin
- app de escritorio (UI interna)
- pantallas CRUD (stock, RMA, clientes, etc.)

Enfocado en:
- eficiencia operativa
- consistencia
- estados (loading/empty/error)
- escalabilidad de UI (no pantallas “arte”)

## Cuándo usar
- Paneles de control
- Apps Electron (renderer)
- Admin para e-commerce / gestión / RMA
- Formularios + tablas + filtros + acciones

## Cuándo NO usar
- Landing/marketing (usar wrapper de frontend design)
- Debugging/bugs (usar systematic debugging)

## Preconditions
Debe existir:
- lista de entidades (ej: Ordenes, Clientes, Productos)
- 3–10 acciones críticas (ej: crear orden, cambiar estado, imprimir, exportar)
- restricciones de rol/permisos si aplica

## Inputs requeridos
- Entidades + campos clave por entidad (mínimo)
- Flujos principales:
  - “crear”
  - “buscar”
  - “editar”
  - “cerrar/procesar”
- Reglas de negocio (validaciones y estados)
- Plataforma: Web o Electron (y tamaño mínimo de pantalla)

## Flow GSMU (pasos)
### Paso 1 — IA de producto: tareas primero
- Definir “Top tasks” (lo más usado)
- Definir navegación:
  - sidebar vs topbar
  - secciones principales
- Definir layout base:
  - Header (título + acciones)
  - Body (tabla/kanban/detalle)
  - Right panel (detalle opcional)

### Paso 2 — Component library mínima
- Botones (primary/secondary/danger)
- Inputs (text, select, date, search)
- Table pattern (sorting, pagination, row actions)
- Modal pattern (confirmaciones)
- Toast/alerts

### Paso 3 — Estados obligatorios (no negociable)
Para cada vista principal:
- Loading
- Empty state (sin datos)
- Error state (fallo API/DB)
- Permission denied (si hay roles)

### Paso 4 — Accesos rápidos y productividad
- Search global (si aplica)
- Filtros persistentes
- Atajos por teclado (opcional)
- Export (Excel/PDF) como acción consistente

### Paso 5 — Hand-off a implementación
- Mapear pantallas -> componentes -> endpoints (si ya existe API)
- Si es Electron, coordinar con IPC/Preload skill

## Outputs obligatorios
- `interface_spec.md` con:
  - Information architecture (mapa de pantallas)
  - Layout base (texto) por pantalla
  - Component patterns (tabla, formulario, modal, etc.)
  - Estados (loading/empty/error) definidos
  - Reglas de validación UI
- `ui_actions_map.md` (opcional pero recomendado):
  - Acción -> dónde vive -> permisos -> feedback al usuario

## Checklist de verificación
- ¿Las “Top tasks” se resuelven en 1–2 clicks?
- ¿La tabla tiene patrón consistente (acciones, orden, filtros)?
- ¿Cada pantalla tiene loading/empty/error?
- ¿Las acciones destructivas piden confirmación?
- ¿No hay dependencia de “scroll infinito” si es herramienta?

## Hard Rules GSMU
- No hacer “diseño de landing” acá.
- No mezclar 10 estilos distintos: 1 sistema, repetible.
- Si faltan reglas de negocio, marcarlas como [TODO] y proponer defaults.
