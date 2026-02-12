# Skill: Project AI_START Manifest (GSMU) — “Start Here” para cualquier IA

## Objetivo
Evitar que el agente **invente** estructura, stack, DB o rutas.

Este skill crea/actualiza un archivo único de entrada:

- `AI_START.md` (preferido) **o** `docs/ai/AI_START.md` si el repo ya usa carpeta `docs/ai/`.

El archivo debe dejar claro:
- **Qué es el proyecto** (nombre + objetivo)
- **Qué tecnología se usa** (lenguaje, frameworks, runtime)
- **Cómo se ejecuta** (run/build/test)
- **Dónde está la DB** (local/nube, nombre de DB, cómo se conecta)
- **Dónde está la documentación** (paths reales)
- **Hard rules** (lo que NO se puede cambiar)
- **Qué leer primero** (fuente de verdad)

> Resultado: cualquier IA (Claude/Gemini/GPT/etc.) entra al repo, lee 1 archivo y sabe qué respetar.

---

## Cuándo usar
- Siempre que arranca un proyecto nuevo.
- Si se cambia de IA/modelo.
- Si el agente muestra señales de “asumir” (por ejemplo: propone crear DB local cuando ya existe en la nube).

---

## Entradas
Si existen, leer primero:
- `project_context.md`
- `project_brief.md`
- `docs/**`
- Cualquier diagrama (ej: `ARCHITECTURE_DIAGRAM.md`)

Si no existen, crear un primer borrador de `AI_START.md` con supuestos marcados como **PENDIENTE**.

---

## Output requerido
Crear/actualizar `AI_START.md` con esta plantilla (copiar tal cual y completar):

```md
# AI_START — <NOMBRE DEL PROYECTO>

## 1) Qué es (1–3 líneas)
- Objetivo: ...
- Usuario/operador: ...

## 2) Fuente de verdad (leer en este orden)
1. AI_START.md (este archivo)
2. project_context.md
3. project_brief.md
4. docs/** (mapas y contratos específicos)

## 3) Stack y ejecución
- Lenguaje/runtime: ...
- Frontend/Cliente: ...
- Backend/API: ...
- DB: ...

### Cómo correr (dev)
- ...

### Cómo buildear (prod)
- ...

## 4) Arquitectura
- Diagrama: <ruta al diagrama si existe>
- Flujo: Cliente → API → DB (o lo que corresponda)

## 5) Base de Datos (NO inventar)
- Ubicación: (local | nube)
- Motor: (MySQL/MariaDB/Postgres/SQLite/...)
- Nombres: ...
- Conexión: (archivo/servicio) ...

### Mapas de esquema
- <ruta a docs/db/... o equivalente>

## 6) Reglas duras (Hard rules)
- Ej: credenciales no van al cliente
- Ej: endpoints requieren token
- Ej: no React / sí React
- Ej: rutas físicas de upload

## 7) Módulos y navegación (si aplica)
- Sidebar: ...
- Pantallas: ...

## 8) Estado actual y próximo paso
- Fase actual: ...
- Próximo objetivo: ...
```

---

## Checklist antes de proponer cambios
- ✅ Leí `AI_START.md` completo.
- ✅ Ubico dónde vive la DB y cómo se conecta.
- ✅ No propongo crear tablas/DB “porque sí”.
- ✅ Si una ruta/tabla/columna no está documentada, **pregunto o marco PENDIENTE**.
