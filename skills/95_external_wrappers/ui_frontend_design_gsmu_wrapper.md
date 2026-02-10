# Wrapper GSMU — UI Frontend Design (Anthropic)

## External Skill (source)
- Nombre: Frontend Design Skill
- URL: https://github.com/anthropics/claude-code/blob/main/plugins/frontend-design/skills/frontend-design/SKILL.md

## Objetivo (GSMU)
Diseñar y especificar una **UI pública** (landing / marketing / web institucional) con:
- identidad visual consistente
- jerarquía clara
- componentes reutilizables
- decisiones verificables (no “diseño por gusto”)

## Cuándo usar
- Landing pages, home, páginas de servicios, pricing, contacto
- Sitios marketing-first donde el objetivo es conversión (CTA, claridad, confianza)

## Cuándo NO usar
- Dashboards y herramientas internas (usar `ui_interface_design_gsmu_wrapper.md`)
- Si el problema es técnico/arquitectura (usar orquestador + skill técnico)

## Preconditions (antes de empezar)
Debe existir (o definirse en intake):
- target user + objetivo de la página
- propuesta de valor en 1 frase
- lista de secciones deseadas (aunque sea borrador)
- stack UI (Vanilla/React/Next) + restricciones (hosting, performance, etc.)

## Inputs requeridos (mínimos)
- Brand: nombre, tono (serio/tech/amigable), 2–3 colores si existen, tipografía si existe
- Contenido base: servicios principales + diferenciales + forma de contacto
- Restricciones: móvil primero, velocidad, SEO, assets disponibles (logos/imagenes)

## Flow GSMU (pasos)
### Paso 1 — Estructura (IA no diseña “bonito”, diseña “claro”)
- Definir sitemap mínimo (Home + Servicios + Nosotros + Contacto + FAQ opcional)
- Definir estructura de Home (sections) y orden:
  1) Hero (promesa + CTA)
  2) Proof (reseñas, números, marcas, garantías)
  3) Servicios (cards)
  4) Proceso (cómo trabajamos)
  5) CTA fuerte + Contacto

### Paso 2 — Design tokens (mínimo viable)
- Definir:
  - palette primaria/secundaria + neutrales
  - tipografías (si no hay: elegir 1 sans limpia)
  - spacing scale (4/8/12/16…)
  - radius + shadow
- Output: tabla de tokens en markdown (o JSON si el proyecto lo pide)

### Paso 3 — Componentes
Especificar componentes:
- Navbar (sticky sí/no)
- Hero layout (split / centered)
- Cards (servicios)
- Badges (garantía, tiempos, etc.)
- CTA button styles
- Footer (links + redes)

### Paso 4 — Estados y accesibilidad
- Hover/focus/active
- Contraste y tamaños mínimos
- Responsive breakpoints

### Paso 5 — Hand-off a implementación
- Si el proyecto ya tiene skill de `20_web/landing_baseline.md`, delegar ahí el HTML/CSS/JS real.

## Outputs obligatorios
- `ui_spec.md` con:
  - Secciones y contenido por sección (titulares sugeridos)
  - Design tokens
  - Lista de componentes + comportamiento responsive
  - Checklist de accesibilidad mínimo
- Si aplica (opcional):
  - `wireframe_notes.md` (texto) para guiar layout

## Checklist de verificación (antes de cerrar)
- ¿El hero responde “qué hacés + para quién + por qué confiar” en 5 segundos?
- ¿Hay 1 CTA principal, no 5?
- ¿Mobile-first está contemplado?
- ¿Tokens y componentes son reutilizables (no únicos por sección)?
- ¿No se inventaron claims (números/estadísticas) sin fuente?

## Hard Rules GSMU
- No inventar testimonios, números, “clientes”, certificaciones.
- No sobrecargar con animaciones ni efectos por defecto.
- Si falta contenido, proponer placeholders marcados como [TODO].
