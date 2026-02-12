# Skill: UI Interface Dashboard (GSMU) — Vanilla Electron + Reference-driven

## Objetivo
Diseñar y construir la **base estética + layout** del dashboard de la app Electron (vanilla) de gestión (stock / pedidos / alertas / contenido web), **guiándose por una imagen de referencia**:

- Referencia obligatoria: `docs/ui/dashboard_reference.png`

Este skill entrega **estructura + sistema visual**, NO lógica de negocio.

---

## Alcance
**Usar para:**
- Dashboards, admin panels, herramientas internas, pantallas de settings, tablas/listados, cards de métricas.

**No usar para:**
- Landing pages / marketing / UI pública.

---

## Reglas duras (Hard rules)
1. **No React**. Solo HTML + CSS + JS modular (renderer).
2. **La referencia manda**: layout general debe conservar patrón (sidebar izquierda + topbar + cards + secciones).
3. **No lógica aún**: en esta fase solo mock/dummy data y estructura visual.
4. **Tokens primero**: no tirar hex al azar. Todo debe salir de variables CSS.
5. **Accesibilidad mínima**: contraste razonable, focus visible, estados hover/active/disabled.
6. **No romper CSP**: evitar inline `onclick`. Usar listeners en JS.

---

## Inputs requeridos (si faltan, pedirlos)
- `docs/ui/dashboard_reference.png` (obligatorio).
- Identidad mínima: nombre de la app + tono (serio/amigable) + densidad (compacta/normal).

---

## Proceso obligatorio (antes de escribir código)
El agente debe producir estos 4 entregables **en texto** primero:

### 1) Domain (mínimo 8)
Conceptos del mundo real del usuario (taller/stock/reparaciones/web/importaciones/alertas).
Ejemplos a cubrir: stock mínimo, reposición, pedido en tránsito, costo, proveedor, dueño, mensajes web (contacto), órdenes en efectivo (ordenes_simple), avisos temporales, publicaciones de desarrollo.

### 2) Color world (mínimo 6)
Colores del mundo real del producto (taller/depósito/caja).
Ej: cartón/etiquetas/estanterías/impresora térmica/herramientas/pantallas.
**Prohibido**: terminar con tokens genéricos tipo `--gray-700`.

### 3) Signature (1)
Un elemento **propio de GSMU** que aparezca en UI (componente o patrón).
Ejemplos de firma (elige 1):
- Panel “Alertas GSMU” unificado (stock bajo + órdenes_simple pendientes + mensajes contacto nuevos).
- Semáforo “Reposición” (stock vs mínimo) con micro-badge.
- “Owner badge” (dueño del ítem) visible en listados y detalle.

### 4) Defaults (3) + reemplazo
Nombrar 3 defaults típicos de dashboards y explicar cómo se evita cada uno (visual y estructura).

> Si el agente no puede completar estos 4 ítems con especificidad, debe frenar y pedir info.

---

## Dirección única
El agente debe proponer **1 sola dirección** (no 3 variantes) y esperar aprobación del usuario.

Formato:
- Domain: ...
- Color world: ...
- Signature: ...
- Rechazando defaults: ...
- Direction: ...
[Pregunta] “¿Aprobás esta dirección visual?”

---

## Outputs (archivos a generar)
Una vez aprobada la dirección, generar:

1) `docs/ui/ui_system.md`
Debe incluir:
- Dirección y “feel”
- Estrategia de profundidad (bordes vs sombras sutiles)
- Escala de spacing (base unit)
- Tokens: nombres + propósito (colores, texto, bordes, surfaces, semantic)
- Tipografía (jerarquía: h1, h2, body, label, meta)
- Component patterns: sidebar item, topbar, card, table, badge, button, input, empty/error/loading

2) `src/renderer/css/ui.css`
- Variables CSS `:root` con tokens (nombres con identidad del dominio)
- Base styles (body, headings, links)
- Utilities mínimas (grid, stack, gap)

3) `src/renderer/index.html`
- Layout del dashboard: sidebar + topbar + main content
- Cards KPI dummy
- Contenedor de “panel alertas” dummy
- Tabla/listado dummy (estructura realista)

4) `src/renderer/css/style.css` (o refactor)
- Debe consumir `ui.css` (import o integración)
- Sin estilos “sueltos” sin token

---

## Estructura UI requerida (Sidebar real del proyecto)
El sidebar debe incluir estas secciones (en este orden sugerido):

1. **Dashboard**
2. **Repuestos** (tabla `repuestos`)
3. **Tienda** (tabla `tienda`)
4. **Productos** (Servicios) (tabla `productos`)
5. **Órdenes Simple** (tabla `ordenes_simple`)
   - Objetivo UI: listar pendientes, marcar “listo/tenida en cuenta”
6. **Pedidos** (tabla `pedidos`) *(si existe en tu plan actual)*
7. **Proveedores** (tabla `proveedores`) *(si existe en tu plan actual)*
8. **Desarrollo** (tabla `desarrollo`)
9. **Aviso** (tabla `aviso`)
10. **Mensajes** (Contacto) (tabla `contacto`)
11. **Ajustes**
    - **Dólar** (tabla `dolar`)
    - **Info** (tabla `info`)

Notas:
- “Ajustes” agrupa cambios pequeños y frecuentes (dólar/info), no debe sentirse como “pantalla secundaria”.
- “Mensajes (Contacto)” debe tener contador/badge de “no leídos”.

---

## Topbar requerida
- Buscador global (placeholder visual)
- Indicador API (OK / error)
- Usuario / menú (placeholder)

---

## Checklist de calidad (antes de mostrar)
- **Squint test**: jerarquía clara sin bordes gritones.
- **Swap test**: si cambio fuente/layout por uno genérico, ¿se nota? Si no se nota, está genérico.
- **Signature test**: ¿la firma aparece en 3+ lugares reales?
- **States**: hover/focus/disabled/empty/error/loading presentes.
- **Consistencia**: spacing en múltiplos del base unit.

---

## Gate de cambios (obligatorio)
Si el agente detecta una “mejor idea” (layout, colores, navegación), debe:
1) Marcar “PROPUESTA DE MEJORA”
2) Explicar beneficio / riesgo / impacto
3) No ejecutar sin:
- “APROBADO: …” o “RECHAZADO: …”

---

## Notas para este proyecto
- Referencia: `docs/ui/dashboard_reference.png`
- Electron + Vite
- Evitar inline handlers por CSP (usar listeners)
- No avanzar a pantallas específicas (CRUD real) hasta que el dashboard base esté aprobado
