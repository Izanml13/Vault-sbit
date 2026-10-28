# ✅ Tablero de tareas

Volver a [[Inicio]] · Ver [[Reparto por PCs]]

## Sprint 4 · Front y comunicación (desde 2026-10-28)

**Objetivo:** front de calidad (UI UX Pro Max, Liquid Glass, animaciones) y comunicación real: chat por alumno, doble validación de horas, clases del profe y profes del instituto, informes por rol.

**Encargos y decisiones:** [[Encargos sprint 4]].

**Reparto:** PC 1 (Claude) todo el front · PC 2 base de datos · PC 3 backend · PC 4 ayudante general (tests, e2e, revisión, docs, estudio SBIT) · Codex revisa las PR de PC 2 y PC 3.

**Cadena:** PC 2 migración → PC 3 núcleo y adaptadores → PC 1 pantalla.

### 🗄️ PC 2 · Base de datos · Boubacar

| Tarea | Rama | Estado | Notas |
|---|---|---|---|
| Chat de mensajes por dossier | `feature/pc2-db-chat` | 👀 En revisión (PR #13) | Tabla `mensajes_chat`. Leen y escriben alumno, profe tutor, empresa e instituto; Generalitat solo lee |
| Clases (grupos) y clase de cada alumno | `feature/pc2-db-clases` | 👀 En revisión (PR #14) | Tabla `grupos` + `perfiles.grupo_id`. Instituto y Generalitat gestionan |
| Doble validación de horas | `feature/pc2-db-validar-horas` | 👀 En revisión (PR #15) | Empresa valida primero, luego el profe. Día validado = no se edita ni borra. PC 1: el dominio necesita los 4 campos nuevos |

Las tres PR añaden un bloque al final de `seed.sql`: si hay conflicto al fusionar, quedarse con todos. Probadas juntas.

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
| **Antes de nada:** actualizarse desde `develop` (los datos demo han cambiado) | — | ✅ Hecho | Empezado desde `develop` con los datos demo nuevos |
| Iconos reales en la barra inferior (Registrar y Perfil sin icono genérico) | `feature/pc3-iconos-pestanas` | ✅ Hecho | SF Symbols en iOS, Material en Android y SVG en la web, sin dependencias nuevas |
| Pestaña *Centro* también para la Generalitat | `feature/pc3-pestana-centro` | ✅ Hecho | En móvil y web; `centro.tsx` y `PanelInstituto` ya la admitían |
| Componentes: casilla de tarea, chip de tipo de evento, insignia "vencida" | `feature/pc3-componentes-tareas` | ✅ Hecho | `CasillaTarea`, `ChipTipoEvento` e `InsigniaVencida`; PC 2 puede usarlos ya en tareas y fechas |
| `Pantalla` con teclado cómodo (`keyboardShouldPersistTaps`, `keyboardDismissMode`) | `fix/pc3-teclado` | ✅ Hecho | Aplicado en el componente `Pantalla` |
| Repaso de modo oscuro y contraste en todas las pantallas | `fix/pc3-modo-oscuro` | ✅ Hecho | Todo el tema pasa 4,5:1. Queda el `opacity: 0.35` de los días fuera de periodo en `vistas/calendario-mes.tsx` (es de PC 2) |

Las cinco tareas entraron en `develop` el 2026-10-28 **sin PR**, a petición de PC 3: PC 1 solo tiene que revisarlas.

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
| Sprint 3: iconos de pestañas, pestaña Centro para la Generalitat, componentes de tareas, teclado y contraste en oscuro (directo a `develop`, sin PR) | PC 3 | 2026-10-28 |
| Flujo de ramas `main`/`develop` y limpieza de ramas | Izan | 2026-10-28 |


Estados: ⏳ Pendiente · 🔄 En curso · 👀 En revisión · ✅ Hecho · ⛔ Bloqueado
