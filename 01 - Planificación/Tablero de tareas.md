# ✅ Tablero de tareas

Volver a [[Inicio]] · Ver [[Reparto por PCs]]

## Sprint 2 · MVP usable (desde 2026-10-27)

**Objetivo:** el alumno apunta sus días, la empresa valora el mes y el profe pone la valoración final, con datos reales en Supabase, en web y en móvil.

**Punto de partida (ya en `main`):** login, pestañas por rol, panel del alumno, registro diario, valoración mensual (empresa), seguimiento y valoración final (profe), componentes base y adaptadores Supabase y memoria. Para probar: `npx expo start --web` y las cuentas de prueba del login.

**Cómo trabajar:** `git pull` en `main` → rama `feature/pcN-...` → `npm run lint`, `npm run typecheck` y `npm run format:check` → PR. PC 1 revisa y fusiona.

### 🧠 PC 1 · Izan · Claude Code + Codex

| Tarea | Rama | Estado | Notas |
|---|---|---|---|
| Aplicar en Supabase la migración de roles y valoraciones | — | ✅ Hecho | Con `npm run db:subir`; la web ya funciona en Supabase con los 3 roles |
| Nombre del alumno y del tutor en el dossier | `feature/pc1-dossier-nombres` | ✅ Hecho | `alumnoNombre`, `tutorNombre`, `tutorEmpresaNombre` en `Dossier` |
| Tests unitarios con Jest (registro, valoraciones, fechas) | `feature/pc1-tests` | ✅ Hecho | 35 tests; `npm test` en el CI |
| Modelo ER: centros, empresas, convenios y alumnos por centro | `feature/pc1-centros-empresas` | ✅ Hecho | Migración `20261027000000`; el profe solo ve su centro. Aplicada en Supabase |
| Migraciones con la CLI: CI desde cero, despliegue automático y backup | `feature/pc1-migraciones-ci` | ✅ Hecho | Al fusionar una migración en `main` se aplica sola en Supabase. Normas en `AGENTS.md` |
| Cinco roles del ER: generalitat, instituto, profe, empresa y alumno | `feature/pc1-cinco-roles` | ✅ Hecho | Migración `20261027010000` (desplegada sola). Sustituye la PR 2. Faltan pantallas de instituto (asignar alumnos) y generalitat |
| Núcleo de tareas y calendario (dominio, puerto, casos de uso, adaptadores) | `feature/pc1-tareas` | ⏳ Pendiente | Tablas ya creadas en Supabase |
| Revisar y fusionar las PR de PC 2, 3 y 4 | — | 🔄 Continuo | |

### 📱 PC 2 · Pantallas · OpenCode
Solo `src/app/`, `src/ui/hooks/` y `src/ui/vistas/`.

| Tarea | Rama | Estado | Notas |
|---|---|---|---|
| Calendario mensual del alumno con el estado de cada día | `feature/pc2-calendario` | ⏳ Pendiente | Usa `listarRegistros`; tocar un día abre el registro de ese día |
| Pulir el registro diario en móvil (teclado, scroll, botones) | `feature/pc2-registro-movil` | ⏳ Pendiente | Probar en Expo Go |
| Estados vacíos y de carga en los tres paneles | `feature/pc2-estados` | ⏳ Pendiente | |
| Nombre del alumno en las tarjetas de empresa y profe | `feature/pc2-nombres` | ⏳ Pendiente | Ya se puede: `dossier.alumnoNombre` |

### 🧩 PC 3 · Componentes, tema y datos de prueba · OpenCode
Solo `src/ui/components/`, `src/ui/theme/` y `src/infrastructure/memory/`.

| Tarea | Rama | Estado | Notas |
|---|---|---|---|
| Cambiar el logo animado de Expo por la K de Kampus | `feature/pc3-logo-animado` | ⏳ Pendiente | `animated-icon.tsx` y `.web.tsx`; logo en `assets/brand/` |
| Datos de prueba realistas en memoria (2-3 alumnos, días de septiembre y octubre) | `feature/pc3-datos-demo` | ⏳ Pendiente | Mismos IDs que `supabase/seed.sql` donde se pueda |
| Componente `CeldaCalendario` (día, estado, horas) | `feature/pc3-celda-calendario` | ⏳ Pendiente | Lo usará PC 2 en el calendario |
| Repaso de accesibilidad de los componentes base | `feature/pc3-accesibilidad` | ⏳ Pendiente | Contraste, 44 px mínimo, etiquetas para lector de pantalla |

### 🎨 PC 4 · Diseño, web y QA · OpenCode
Solo diseño, `e2e/` y el panel web.

| Tarea | Rama | Estado | Notas |
|---|---|---|---|
| Mockups en Figma de las pantallas actuales y del calendario | — | ⏳ Pendiente | Tema monocromo, Inter y el logo del archivo "Kampus · Logo" |
| Tests E2E con Playwright de la web: login y registrar un día | `feature/pc4-e2e` | ⏳ Pendiente | Contra `npx expo start --web`, backend memoria |
| Revisión de experiencia de uso con los tres roles | — | ⏳ Pendiente | Apuntar las propuestas como tareas en este tablero |

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

Estados: ⏳ Pendiente · 🔄 En curso · 👀 En revisión · ✅ Hecho · ⛔ Bloqueado
