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
| Chat de mensajes por dossier | `feature/pc2-db-chat` | 👀 En revisión (PR #13) | Tabla `mensajes_chat`. Leen y escriben alumno, profe tutor, empresa e instituto; Generalitat solo lee. ✅ Aprobada por PC 4. ⚠️ **Solapa con `chat_directo`** (Izan, ya en `main`): chat de persona a persona. Decidir si se cierra la #13 o si queda como chat de grupo del dossier. El chat de persona a persona ya tiene backend en `develop`: ver [[2026-11-02]] |
| Clases (grupos) y clase de cada alumno | `feature/pc2-db-clases` | ✅ Integrada en develop (PR #14) | Tabla `grupos` + `perfiles.grupo_id`. Instituto y Generalitat gestionan. ✅ Aprobada por PC 4 |
| Doble validación de horas: el profe confirma el mes | `feature/pc2-db-validar-mes` | ✅ Integrada en develop (PR #26) | **Sustituye a la #15 (cerrada)**: la validación es mensual. La empresa ya valida el mes con la valoración mensual; esto añade `confirmada_por`/`confirmada_en` en `valoraciones_mensuales`. Solo el profe tutor confirma; un mes confirmado no lo toca la empresa |
| Profe: Inicio (inbox, horas por validar, sin apuntar con toque) y pestaña Seguimiento | `feature/pc2-inicio-profe` | ✅ Hecho (PR #16, en `develop`) | Según la pizarra del 28/10. Toca `app-tabs` (pestaña Seguimiento para el profe): revisar PC 1. 💬 Comentarios de PC 4: también toca `package.json` (+`react-native-svg`) y arrastra commits de `feature/pc1-calendario-apple`; que decidan PC 1 e Izan |
| Profe con el estilo del alumno: Inicio y Seguimiento (lista compacta) | `feature/pc2-estilo-profe`, `feature/pc2-estilo-seguimiento` | ✅ Hecho (PR #19 y #21, en `develop`) | |
| Toques de atención del profe al alumno | `feature/pc2-db-toques` | ✅ En `develop` (PR #18) | Tabla `toques`, uno al día, se resuelve al apuntar. Falta `ToquePort` (PC 3) y aviso en el Inicio del alumno (PC 1). ✅ Aprobada por PC 4 |

| Correo del tutor de empresa: `perfiles.email` sigue a `auth.users.email` | `feature/pc2-db-correo` | 👀 En revisión (PR #27, CI ✅) | Trigger en `auth.users` + `proteger_perfil` solo deja poner el correo de la cuenta. La app no cambia |
| Seguridad e índices del asesor de Supabase | `fix/pc2-db-seguridad` | 👀 En revisión (PR #28, CI ✅) | `comparten_dossier`, `gestiona_alumno` y los triggers de incidencias ya no se llaman sin sesión; 4 índices de claves foráneas |

Base de datos pendiente de revisión: #18, #27 y #28. La #13 sigue pendiente de decisión sobre el chat de grupo.

### ⚙️ PC 3 · Backend · OpenCode

| Tarea | Rama | Estado | Notas |
|---|---|---|---|
| Profesores del centro con sus alumnos y reasignar en bloque | `feature/pc3-profes-instituto` | Código en rama | `obtenerRepartoProfes` (cada profe con sus alumnos y los que no tienen tutor) y `reasignarAlumnos`; puerto con `asignarProfeEnBloque`, una sola consulta en Supabase. 12 tests. Reutiliza `container.centros`. Pendiente integrar la rama y probar la separación entre centros |
| Informes por rol | `feature/pc3-informes` | ✅ En `develop` | Solo lectura: alumno (horas totales y por mes), profe y empresa (progreso de sus alumnos), instituto (por profe y por empresa), Generalitat (por centro). 16 tests. ✅ PC 1 lo registró en `container.ts` el 2026-10-29 (`informes`) |
| Chat por dossier | `feature/pc3-chat` | ⛔ Bloqueado | Espera a `feature/pc2-db-chat` (PR #13). ⚠️ El chat directo de persona a persona ya está en `develop` con su propio módulo: ver [[2026-11-02]] |
| Clases (grupos) y "mis clases" del profe | `feature/pc3-clases` | Disponible para PC 3 | Migración integrada (#14) |
| Doble validación de horas | `feature/pc3-validar-horas` | Disponible para PC 3 | Migración integrada (#26, sustituye a la #15). `ValoracionMensual` con `confirmadaPor`/`confirmadaEn` y `confirmarMes`/`quitarConfirmacion`. El Inicio del profe (PR #16) necesita listar los días ya validados por la empresa y pendientes del profe, y validar varios de una vez |
| Toques de atención | `feature/pc3-toques` | ⏳ Desbloqueado (02/11) | Espera a `feature/pc2-db-toques` (PR #18). `ToquePort`: `dar(dossierId, diasSinApuntar)`, `pendientesDelAlumno()`, `ultimosPorDossier(ids)` y `marcarVisto(id)`; adaptadores memoria y Supabase. Detalle en la PR #18 |
| Conectar el chat de la empresa al chat real | `feature/pc3-chat-empresa` | ⏳ Pendiente (revisión 02/11) | `chat-empresa.tsx` guarda los mensajes en memoria (`ui/estado/chat-empresa.ts`). Usar el `ChatPort` de `chat_directo` que ya está en `main` |

PC 3 puede empezar clases y confirmación mensual desde el develop actual. Toques depende de #18. El progreso por clase depende del módulo de grupos.

### 🧠 PC 1 · Izan · Claude Code + Codex

| Tarea | Rama | Estado | Notas |
|---|---|---|---|
| Revisar las PR de base de datos restantes | — | En curso | #14 y #26 integradas. Revisar #18, #27 y #28. Decidir el alcance de #13 |
| Revisar y fusionar el Inicio del profe (PR #16) | — | ✅ Hecho (fusionada por Bouba) | Sale de `feature/pc1-calendario-apple`. Toca `app-tabs.tsx` y `app-tabs.web.tsx`: la pestaña del profe se llama Seguimiento. 💬 PC 4 comentó: también `package.json` (+`react-native-svg`) y commits de esa rama sin fusionar dentro del diff |
| Aviso de toque en el Inicio del alumno | `feature/pc1-aviso-toque` | ⛔ Bloqueado | Espera a `feature/pc3-toques`. Arriba de `panel-alumno.tsx`: "Tu tutor te ha dado un toque: llevas N días sin apuntar" + botón "Apuntar ahora" (`/registro`); al verlo, `marcarVisto` |
| Primera release `develop → main` | — | ✅ Hecho (PR #23, 29/10) | La nube ya tiene `datos_personales`, `identidad_alumno`, `chat_directo` y `chat_realtime`. Desde entonces `develop` suma `historial_dossier`: falta otra release |
| Segunda release develop → main | — | Pendiente | 29 commits de develop no están en main al comprobar b6c320f. Ver [[2026-11-02]] |
| Revisar las PR restantes | — | En curso | Ver [PR abiertas en GitHub](https://github.com/bose069-web/SBIT_BIRM/pulls). La #25 corresponde a la auditoría UI de PC 3 |
| Decidir con PC 2 qué hacer con la #13 (chat por dossier) | — | ⏳ Pendiente | Solapa con `chat_directo`: cerrarla o dejarla como chat de grupo del dossier |
| Activar la protección de contraseñas filtradas en Supabase | Panel de Supabase | ⏳ Pendiente (revisión 02/11) | *Authentication → Passwords → Leaked password protection*. No es código: lo hace quien administra el proyecto |
| Registrar en `container.ts` los backends nuevos de PC 3 | — | 🔄 En curso | `chat` e `informes` hechos (2026-10-29); profes del instituto amplía `centros`. Coordinar clases, confirmación mensual y toques con PC 3 |
| Fusionar PR #17 (test de pantallas, PC 4) | `test/pc4-pantallas` | ⏳ Pendiente | 7 tests sobre las pantallas de develop; 126/126 en local |

### 🧪 PC 4 · Ayudante general · Marco

| Tarea | Rama | Estado | Notas |
|---|---|---|---|
| Pulsar el panel del instituto | `feature/pc4-inicio-instituto` | ✅ Hecho (PR #20 fusionada) | Cifras arriba, dos columnas en web ancha, mismos colores y componentes. Ya en `develop` |
| Revisar las PR #16 (Inicio del profe) y #18 (toques) | — | ✅ Hecho | #18 aprobada; #16 con comentarios (zona de PC 1). Como con #13-#15 |
| Rehacer el test de pantallas | `test/pc4-pantallas` | 👀 En revisión (PR #17) | 7 tests: registro-dia no pisa días, recarga del panel al volver, dossiers por nombre, retry, `useDatos` descarta respuestas viejas. 126/126 en local |
| Test automático de permisos (RLS) en el CI | `test/pc4-rls` | 💡 Propuesta | Que el CI compruebe con los cinco roles quién ve y cambia cada tabla, para no romper permisos en migraciones futuras |
| Revisar las PR #27 y #28 de base de datos | — | ⏳ Pendiente (revisión 02/11) | Como con #13-#18 |
| e2e del profe: Inicio, pestaña Seguimiento y darle un toque | `test/pc4-e2e-profe` | ⛔ Bloqueado | Espera a que se fusione la PR #16 |
| Estudio del SBIT por rol | — | ⏳ Pendiente | Funciones y flujos en `02 - Requisitos`; necesita aporte de Marco |

### 🏢 Empresa · rama `feature/pc3-informes` (✅ en `develop`, PR #22)

| Tarea | Zona | Estado | Notas |
|---|---|---|---|
| Inicio de la empresa: ritmo por calendario, avisos, informes por validar, últimas valoraciones, fechas y mensajes | `ui/vistas/panel-empresa.tsx`, `ui/utils/ritmo.ts` | ✅ Hecho | La marca de la barra son las horas que tocan hoy; avisos de sin apuntar, por debajo del ritmo y fin de prácticas |
| Pestaña Validaciones (antes Calendario) para la empresa | `app/validaciones.tsx`, `ui/vistas/validaciones.tsx`, `app-tabs` | ✅ Hecho | Pendientes arriba, validadas abajo en tono flojo; Calendario se mantiene para los demás roles |
| Chat de la empresa (un hilo por alumno y por profe) | `ui/vistas/chat-directo.tsx`, `ui/utils/chat.ts`, `ui/estado/chat-empresa.ts` | ✅ Hecho (con backend) | Desde el 2026-10-29 lee de `ChatPort`: tablas `chat_mensajes` y `chat_lecturas` con realtime. La pantalla pasó a `chat-directo.tsx`, compartida con alumno y profe; `chat-empresa.tsx` es un envoltorio |
| Correo editable por el tutor de empresa | `core/domain/perfil.ts`, `core/application/perfil.ts`, `ports/perfil-port.ts`, adaptadores, `ui/vistas/perfil.tsx` | ✅ Hecho (falta migración) | `auth.updateUser` en Supabase; `perfiles.email` y `proteger_perfil` necesitan migración de PC 2 |
| La valoración final del profe cierra los pendientes de la empresa | `ui/utils/validaciones.ts` | ✅ Hecho | Antes la empresa seguía viendo meses que ya no podía validar |
| Revisar pestañas, `BarraProgreso` y Validaciones | PC 1 | ⏳ Pendiente | Zona de PC 1: `app-tabs.tsx`, `app-tabs.web.tsx`, `ui/components/barra-progreso.tsx` |
| Migración del correo (`perfiles.email` + `proteger_perfil`) | PC 2 | 👀 En revisión (PR #27) | Trigger en `auth.users` y ajustar el trigger de perfiles, o retirar la columna |
| Módulo de chat real y registro de informes en `container.ts` | PC 3 / PC 1 | ✅ Hecho | `chat` e `informes` registrados el 2026-10-29 (`ChatSupabase`/`ChatMemory`, `InformesSupabase`/`InformesMemory`) |
| e2e del flujo empresa → profe y del cambio de correo | PC 4 | ⏳ Pendiente | Arreglar también `login` y `registro-dia` (botón "Registrar hoy") |

Ver [[2026-10-29]] y [[2026-11-02]].

## Sprint 3 · Base completa · cerrado el 2026-10-28

**Objetivo:** que la base esté entera (dossiers, tareas, incidencias, generalitat) para dedicarnos después solo a mejorar el front.

**Punto de partida (en `develop`):** los cinco roles con sus pantallas, registro diario, valoraciones, Centro del instituto, tareas y fechas del calendario, datos demo de los cinco roles y 65 tests.

**Cómo se trabajó:** ver [[Flujo de ramas]]. `git pull` en `develop` → rama `tipo/pcN-...` → `npm run lint`, `npm run typecheck`, `npm test` y `npm run format:check` → PR **contra `develop`**.

**Encargos del sprint:** [[Encargos sprint 3]].

### 🧠 PC 1 · Izan · Claude Code + Codex

| Tarea | Rama | Estado | Notas |
|---|---|---|---|
| Gestión de dossiers: crear y editar dossier con actividades | `feature/pc1-gestion-dossiers` | ✅ Hecho | Dominio (`BorradorDossier`, `comprobarDossier`), casos de uso (`guardarDossier`, `borrarDossier`, `obtenerOpcionesDossier`, `listarTutoresEmpresa`), adaptadores memoria y Supabase y migración `20261028074336_guardar_dossier.sql` (transacción + RLS). 17 tests nuevos |
| `listarCentros()` y crear centros (Generalitat) | `feature/pc1-centros-generalitat` | ✅ Hecho | Puerto, casos de uso y adaptadores. Pedido en la PR #8; la pantalla la hace PC 1 en el sprint 4 |
| Incidencias: migración, núcleo y adaptadores | `feature/pc1-incidencias` | ✅ Hecho | Migración `20261028090000_incidencias.sql`, dominio y puerto, casos de uso (abrir, corregir, atender, escalar, resolver, borrar y mensajes entre participantes) y adaptadores memoria y Supabase. El profe tutor sigue las de sus alumnos |
| Selector de fecha (dependencia nueva) | `ops/pc1-selector-fecha` | ⏳ Pendiente | Pasa al sprint 4 (`ops/pc1-selector-fecha`) |
| Primera release `develop → main` | — | ⏳ Pendiente | `main` va 43 commits por detrás; falta probar los cinco roles en web y simulador |
| Revisar y fusionar PR | — | ✅ Hecho | Revisadas las cinco tareas de PC 3 y las dos PR de PC 2; todo integrado en `develop` el 2026-10-28 |

### 📱 PC 2 · Pantallas · OpenCode
Solo `src/app/`, `src/ui/hooks/`, `src/ui/vistas/` y `src/ui/utils/`.

| Tarea | Rama | Estado | Notas |
|---|---|---|---|
| Probar en el móvil las pantallas de tareas y fechas y pulirlas | `fix/pc2-tareas-fechas` | ✅ Hecho | PR #9, en `develop` desde 2026-10-28. Probado en web a 320 y 1280 px; falta Expo Go en móvil real. La barra de pestañas web a 320 px la arregló PC 3 (`fix/pc3-pestanas-estrechas`) |
| Ficha del dossier (solo lectura): datos, actividades, horas por actividad | `feature/pc2-ficha-dossier` | ✅ Hecho | PR #10, en `develop` desde 2026-10-28. Se abre en Inicio con `?dossier=<id>` desde Seguimiento y desde el panel del alumno |
| Formulario de crear/editar dossier | `feature/pc2-formulario-dossier` | ⏳ Pendiente | Desbloqueado: ya está en `develop` el núcleo de dossiers. En el sprint 4 la pantalla la hace PC 1 |
| Pantalla de incidencias | `feature/pc2-incidencias` | ⏳ Pendiente | Desbloqueado: ya está en `develop` el núcleo de incidencias. En el sprint 4 la pantalla la hace PC 1 |

### 🧩 PC 3 · Componentes, tema y datos de prueba · OpenCode
Solo `src/ui/components/`, `src/ui/theme/` y `src/infrastructure/memory/`.

| Tarea | Rama | Estado | Notas |
|---|---|---|---|
| **Antes de nada:** actualizarse desde `develop` (los datos demo han cambiado) | — | ✅ Hecho | Empezado desde `develop` con los datos demo nuevos |
| Iconos reales en la barra inferior (Registrar y Perfil sin icono genérico) | `feature/pc3-iconos-pestanas` | ✅ Hecho | SF Symbols en iOS, Material en Android y SVG en la web, sin dependencias nuevas |
| Pestaña *Centro* también para la Generalitat | `feature/pc3-pestana-centro` | ✅ Hecho | En móvil y web; `centro.tsx` y `PanelInstituto` ya la admitían |
| Componentes: casilla de tarea, chip de tipo de evento, insignia "vencida" | `feature/pc3-componentes-tareas` | ✅ Hecho | `CasillaTarea`, `ChipTipoEvento` e `InsigniaVencida`; PC 2 puede usarlos ya en tareas y fechas |
| `Pantalla` con teclado cómodo (`keyboardShouldPersistTaps`, `keyboardDismissMode`) | `fix/pc3-teclado` | ✅ Hecho | Aplicado en el componente `Pantalla` |
| Repaso de modo oscuro y contraste en todas las pantallas | `fix/pc3-modo-oscuro` | ✅ Hecho | Todo el tema pasa 4,5:1. Queda el `opacity: 0.35` de los días fuera de periodo en `vistas/calendario-mes.tsx` (front de PC 1 en el sprint 4) |

Las cinco tareas entraron en `develop` el 2026-10-28 **sin PR**, a petición de PC 3. PC 1 las revisó y están fusionadas en `develop`.

### 🎨 PC 4 · Diseño, web y QA · OpenCode
Solo diseño, `e2e/` y el panel web.

| Tarea | Rama | Estado | Notas |
|---|---|---|---|
| E2E de los flujos: login de los 5 roles, registrar un día, valorar un mes, asignar profe | `test/pc4-e2e-flujos` | ⏳ Pendiente | En el sprint 4 pasa a `test/pc4-e2e` con lo nuevo: ver [[Encargos sprint 4]] |
| Rehacer el test de pantallas que se apartó en el rescate | `test/pc4-pantallas` | 👀 En revisión | Hecho en el sprint 4 (PR #17); ver la sección del sprint 4 |
| Web en pantalla ancha (paneles de instituto y Generalitat) | `feature/pc4-web-ancha` | ⏳ Pendiente | El front del sprint 4 lo hace PC 1 |
| Figma de las pantallas que faltan: dossier, incidencias, Generalitat | — | ⏳ Pendiente | El diseño del sprint 4 lo marca UI UX Pro Max (PC 1) |

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
| Sprint 3: crear, editar y borrar dossiers con actividades (dominio, casos de uso, adaptadores y migración) | Izan | 2026-10-28 |
| Sprint 3: incidencias (migración, núcleo, adaptadores y mensajes) | Izan | 2026-10-28 |
| Sprint 3: listar y crear centros desde la Generalitat (núcleo y adaptadores) | Izan | 2026-10-28 |
| Sprint 3: tareas y fechas pulidas (PR #9) y ficha del dossier (PR #10) | PC 2 | 2026-10-28 |
| Sprint 3: iconos de pestañas, pestaña Centro para la Generalitat, componentes de tareas, teclado y contraste en oscuro (directo a `develop`, sin PR) | PC 3 | 2026-10-28 |
| Sprint 4: la barra de pestañas web ya cabe a 320 px (rama `fix/pc3-pestanas-estrechas`) | PC 3 | 2026-10-28 |
| Sprint 4: revisión de PR #13-15 y #18 (aprobadas) y #16 (comentarios sobre zona de PC 1) | PC 4 | 2026-10-28 |
| Sprint 4: test de pantallas rehacido para las pantallas de `develop` (PR #17) | PC 4 | 2026-10-28 |
| Sprint 4: e2e de registro adaptados al calendario plegable (PR #12, esperando fusión) | PC 4 | 2026-10-28 |
| Sprint 4: chat directo de persona a persona (dominio, puerto, casos de uso, adaptadores, `chat_directo`, `chat_realtime` y realtime) | Izan | 2026-10-29 |
| Sprint 4: DNI del alumno en solo lectura (`identidad_alumno`) y perfil redistribuido | Izan | 2026-10-29 |
| Sprint 4: buscar alumno y empresa por nombre o correo en el formulario de dossier | Izan | 2026-10-29 |
| Sprint 4: script de datos de demostración con centros, empresas y personas inventadas | Izan | 2026-10-29 |
| Sprint 4: errores de sesión con reintento en vez de caer a «alumno» | Izan | 2026-10-29 |

Estados: ⏳ Pendiente · 🔄 En curso · 👀 En revisión · ✅ Hecho · ⛔ Bloqueado
