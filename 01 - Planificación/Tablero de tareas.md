# ✅ Tablero de tareas

Volver a [[Inicio]] · Ver [[Reparto por PCs]]

## Sprint 3 · Base completa (desde 2026-10-28)

**Objetivo:** que la base esté entera (dossiers, tareas, incidencias, generalitat) para dedicarnos después solo a mejorar el front.

**Punto de partida (en `develop`):** los cinco roles con sus pantallas, registro diario, valoraciones, Centro del instituto, tareas y fechas del calendario, datos demo de los cinco roles y 65 tests.

**Cómo trabajar:** ver [[Flujo de ramas]]. Resumen: `git pull` en `develop` → rama `tipo/pcN-...` → `npm run lint`, `npm run typecheck`, `npm test` y `npm run format:check` → PR **contra `develop`**. PC 1 revisa y fusiona.

**Encargos listos para pegar en cada OpenCode:** [[Encargos sprint 3]].

### 🧠 PC 1 · Izan · Claude Code + Codex

| Tarea | Rama | Estado | Notas |
|---|---|---|---|
| Gestión de dossiers: crear y editar dossier con actividades | `feature/pc1-gestion-dossiers` | ⏳ Pendiente | Puerto + casos de uso + adaptadores. Desbloquea el formulario de PC 2 |
| `listarCentros()` y crear centros (Generalitat) | `feature/pc1-centros-generalitat` | ⏳ Pendiente | Pedido en la PR #8 |
| Incidencias: migración, núcleo y adaptadores | `feature/pc1-incidencias` | ⏳ Pendiente | Las abre cualquiera; las resuelven instituto y Generalitat |
| Selector de fecha (dependencia nueva) | `ops/pc1-selector-fecha` | ⏳ Pendiente | Hoy las fechas se escriben a mano |
| Primera release `develop → main` | — | ⏳ Pendiente | Tras probar los cinco roles en web y simulador |
| Revisar y fusionar PR | — | 🔄 Continuo | |

### 📱 PC 2 · Pantallas · OpenCode
Solo `src/app/`, `src/ui/hooks/`, `src/ui/vistas/` y `src/ui/utils/`.

| Tarea | Rama | Estado | Notas |
|---|---|---|---|
| Probar en el móvil las pantallas de tareas y fechas y pulirlas | `fix/pc2-tareas-fechas` | 👀 En revisión | PR #9. Probado en web a 320 y 1280 px; falta Expo Go en móvil real. Para PC 3: la barra de pestañas web no cabe a 320 px |
| Ficha del dossier (solo lectura): datos, actividades, horas por actividad | `feature/pc2-ficha-dossier` | 👀 En revisión | PR #10. Se abre en Inicio con `?dossier=<id>` desde Seguimiento y desde el panel del alumno |
| Formulario de crear/editar dossier | `feature/pc2-formulario-dossier` | ⛔ Bloqueado | Espera a `feature/pc1-gestion-dossiers` |
| Pantalla de incidencias | `feature/pc2-incidencias` | ⛔ Bloqueado | Espera a `feature/pc1-incidencias` |

### 🧩 PC 3 · Componentes, tema y datos de prueba · OpenCode
Solo `src/ui/components/`, `src/ui/theme/` y `src/infrastructure/memory/`.

| Tarea | Rama | Estado | Notas |
|---|---|---|---|
| **Antes de nada:** actualizarse desde `develop` (los datos demo han cambiado) | — | ⏳ Pendiente | `IDS_DEMO` en `datos-demo.ts` |
| Iconos reales en la barra inferior (Registrar y Perfil sin icono genérico) | `feature/pc3-iconos-pestanas` | ⏳ Pendiente | |
| Pestaña *Centro* también para la Generalitat | `feature/pc3-pestana-centro` | ⏳ Pendiente | `app-tabs.tsx` y `.web.tsx`. Pedido en la PR #8 |
| Componentes: casilla de tarea, chip de tipo de evento, insignia "vencida" | `feature/pc3-componentes-tareas` | ⏳ Pendiente | Para que PC 2 los use en tareas y fechas |
| `Pantalla` con teclado cómodo (`keyboardShouldPersistTaps`, `keyboardDismissMode`) | `fix/pc3-teclado` | ⏳ Pendiente | Pedido en la PR #4 |
| Repaso de modo oscuro y contraste en todas las pantallas | `fix/pc3-modo-oscuro` | ⏳ Pendiente | |

### 🎨 PC 4 · Diseño, web y QA · OpenCode
Solo diseño, `e2e/` y el panel web.

| Tarea | Rama | Estado | Notas |
|---|---|---|---|
| E2E de los flujos: login de los 5 roles, registrar un día, valorar un mes, asignar profe | `test/pc4-e2e-flujos` | ⏳ Pendiente | Backend memoria |
| Rehacer el test de pantallas que se apartó en el rescate | `test/pc4-pantallas` | ⏳ Pendiente | Ver commit "Rescata de pc1-correcciones-pantallas" |
| Web en pantalla ancha (paneles de instituto y Generalitat) | `feature/pc4-web-ancha` | ⏳ Pendiente | Coordinar con PC 2 si toca `vistas/` |
| Figma de las pantallas que faltan: dossier, incidencias, Generalitat | — | ⏳ Pendiente | Referencia para PC 2 |

## Hecho

| Tarea | Responsable | Fecha |
|---|---|---|
| Vault, análisis del SBIT, requisitos y stack | Equipo | 2026-10-26 |
| Esqueleto, arquitectura hexagonal y CI | Izan | 2026-10-26 |
| Supabase: esquema, permisos por rol y datos demo | Izan | 2026-10-26 |
| Dossier y registro diario (núcleo y adaptadores) | Izan | 2026-10-26 |
| Roles alumno, empresa y profe y valoraciones | Bouba | 2026-10-26 |
| Docker de la versión web | Izan | 2026-10-26 |
| Logo, icono, favicon y splash | Izan | 2026-10-26 |
| Login, pestañas por rol y pantallas de los tres roles | Izan | 2026-10-27 |
| Sprint 2: valoraciones, 5 roles, modelo ER (centros, empresas, convenios), pantalla Centro, migraciones con CI y despliegue | Izan · Bouba | 2026-10-27 |
| Sprint 2: calendario, registro móvil, estados vacíos, nombres, tareas y fechas, vista Generalitat (PR #3-#8) | PC 2 | 2026-10-28 |
| Sprint 2: logo, celda de calendario, accesibilidad y datos demo (rama `botones`) | PC 3 | 2026-10-28 |
| Sprint 2: tests E2E de login y registro (PR #7 fusionada; adaptados a develop) | PC 4 | 2026-10-27 |
| Flujo de ramas `main`/`develop` y limpieza de ramas | Izan | 2026-10-28 |


Estados: ⏳ Pendiente · 🔄 En curso · 👀 En revisión · ✅ Hecho · ⛔ Bloqueado
