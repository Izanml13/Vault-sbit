# 📋 Encargos sprint 4 · Front y comunicación

Volver a [[Tablero de tareas]] · Ver [[Flujo de ramas]] · [[Reparto por PCs]]

Cada PC copia **su** bloque entero y lo pega en su agente. Todos leen `AGENTS.md` del repo. **En este sprint el reparto de carpetas cambia** (ver tabla); si choca con `AGENTS.md`, manda este documento hasta que PC 1 lo actualice.

Antes de empezar, una sola vez y línea a línea (en PowerShell, sin `&&`):

```
git fetch origin --prune
git checkout develop
git pull
```

---

## 👥 Reparto del sprint 4

| PC | Papel | Puede modificar |
|---|---|---|
| **PC 1** · Claude Code (Izan) | **Todo el front** e integración final | `src/app/`, `src/ui/`, `src/config/container.ts`, `package.json`; revisa y fusiona |
| **PC 2** · OpenCode | **Base de datos** | `supabase/migrations/` (solo migraciones nuevas), `supabase/seed.sql` |
| **PC 3** · OpenCode | **Backend** | `src/core/` (domain, ports, application y tests), `src/infrastructure/` (memory y supabase) |
| **PC 4** · OpenCode | **Ayudante general** | Tests, `e2e/`, documentación del vault, revisión de PR, estudio del SBIT |
| **Codex** (en PC 1) | Refuerzo de PC 1 | Revisa las PR de PC 2 y PC 3 antes de fusionar; arreglos pequeños que pida PC 1 |

**Lista de tareas de cada PC:** [[PC 1 · Front]] · [[PC 2 · Base de datos]] · [[PC 3 · Backend]] · [[PC 4 · Ayudante general]]

**Cadena de trabajo:** PC 2 hace la migración → PC 3 monta encima dominio, puerto, casos de uso y adaptadores → PC 1 hace la pantalla. Cada uno avisa al siguiente cuando su PR está en `develop`.

---

## ✅ Decisiones tomadas (2026-10-28)

| Tema | Decisión |
|---|---|
| Chat | **Un chat por alumno (por dossier)**: alumno, profe tutor, tutor de empresa e instituto en el mismo hilo. |
| Validar horas | **Doble validación**: el tutor de empresa valida las horas que registra el alumno; después el profe valida las que ya validó la empresa. Botón sencillo en los dos casos. |
| Clases | **Ciclo + curso + grupo** (ej. DAM 2º A). Las crea el instituto y les asigna alumnos. El profe navega Clases → Alumnos → Ficha. |
| Instituto | Gestiona **profesores** y qué alumnos tiene cada uno, no a los alumnos sueltos. |
| Footer | **Inicio · Calendario · Chat · Perfil** para todos los roles. Fuera Registrar del footer; se queda el botón de Inicio. |
| Informes | Gráficos adaptados a cada rol (alumno: horas totales y por mes; profe: progreso de su clase; instituto: por profe y empresa; Generalitat: por centro). |
| SBIT | Solo **funciones y flujos**, a partir de capturas y uso propio. **Sin datos personales.** |
| Diseño | UI UX Pro Max + Liquid Glass de Apple (cristal nativo en iOS, alternativa opaca en Android y web) + animaciones limpias. |

---

## 🎭 Reparto por usuario: pulir cada rol (2026-10-28)

Además de su parte del sprint, cada PC se encarga de **pulir las pantallas de un rol**, en móvil y en web. La referencia es el **alumno**, que ya tiene el estilo nuevo: Inicio en dos columnas en la web ancha (≥ 1000 px) y en una sola en el móvil, tarjetas de cristal, quesito de horas, calendario estilo Apple y un único azul (`#2563EB`) en claro y oscuro.

| Rol | Quién | Pantalla principal |
|---|---|---|
| **Alumno** | PC 1 · Izan (Claude Code) | `src/ui/vistas/panel-alumno.tsx` (+ calendario y registro) |
| **Profe** | PC 2 · Bouba | `src/ui/vistas/panel-profe.tsx` (+ ficha del dossier) |
| **Empresa** | PC 3 | `src/ui/vistas/panel-empresa.tsx` |
| **Instituto** | PC 4 | `src/ui/vistas/panel-instituto.tsx` |
| Generalitat | Sin asignar de momento | — |

**Normas para todos:**
- Rama propia que sale de la rama del alumno hasta que esté en `develop`: `feature/pcN-inicio-<rol>` (ej. `feature/pc2-inicio-profe`). PR contra `develop`.
- Solo tocáis **la vista de vuestro rol**. Los componentes compartidos (`src/ui/components/`, `theme.ts`, `pantalla.tsx`, cabecera y pestañas) son de PC 1: si necesitáis uno nuevo o un cambio, pedidlo en la PR.
- Reutilizad lo que ya hay: `Tarjeta`, `Quesito`, `Leyenda`, `GraficoBarras`, `SelectorFecha`, `Pantalla amplia` y el patrón `Columnas` de `panel-alumno.tsx`.
- El móvil no se cambia de orden ni de aspecto salvo que haga falta: lo horizontal es solo para la web ancha.
- Antes de la PR: `npm run lint`, `npm run typecheck`, `npm test` y `npm run format:check` en verde, y una captura de web (1280 px) y otra de móvil en la descripción.

**Encargo para pegar en el agente** (cambiad ROL, PC y archivo):

```
Eres PCN del proyecto Kampus. Lee AGENTS.md. Tu tarea es pulir la pantalla de Inicio del rol ROL (archivo src/ui/vistas/panel-ROL.tsx) siguiendo el estilo de src/ui/vistas/panel-alumno.tsx: en la web ancha (Platform.OS === 'web' y ancho ≥ 1000) el panel va en dos columnas con <Pantalla amplia>; en el móvil se queda en una columna como ahora. Usa solo los componentes que ya existen (Tarjeta, Quesito, Leyenda, GraficoBarras...). No toques src/ui/components/, theme.ts ni pantalla.tsx: si necesitas algo de ahí, descríbelo en la PR para PC 1. Rama feature/pcN-inicio-ROL y PR contra develop con capturas de web y móvil. Commits tipo(área): qué hace, en español.
```

---

## 🧠 PC 1 · Claude Code · Todo el front

Lo hace Claude, en este orden:

1. Sistema de diseño con UI UX Pro Max (tokens claro y oscuro).
2. Footer nuevo: Inicio · Calendario · Chat · Perfil.
3. Componentes: Cristal (Liquid Glass), animaciones, Leyenda y gráficos.
4. Calendario rediseñado y selector de días desplegable de la Generalitat (`ops/pc1-selector-fecha`).
5. Formulario de dossier y pantalla de incidencias (el backend ya está en `develop`).
6. Según vayan llegando PC 2 y PC 3: chat, clases del profe con Validar horas, validar de la empresa, profesores del instituto e informes por rol.

---

## 🗄️ PC 2 · Base de datos

```
Eres PC 2 del proyecto Kampus y en este sprint te encargas de la BASE DE DATOS. Lee AGENTS.md (arquitectura y normas de ramas); este encargo sustituye su tabla de carpetas. Solo puedes tocar supabase/migrations/ (SOLO migraciones nuevas, con npm run db:nueva nombre_corto; NUNCA edites una que ya esté en main) y supabase/seed.sql. No toques src/.

Prueba cada migración en local con npm run db:reset y comprueba la RLS entrando como cada rol (set role authenticated + set_config de request.jwt.claims y request.jwt.claim.sub). Reutiliza las funciones que ya existen: administra_centro, gestiona_dossier, puede_ver_dossier, es_generalitat, centro_actual.

Una rama y una PR contra develop por tarea, en este orden. Cuando se fusione cada una, avisa a PC 3:

1. feature/pc2-db-chat — Mensajes de chat por dossier (dossier_id, autor_id, texto de 1 a 2000 caracteres, creado_en). Trigger que pone el autor. RLS: leen y escriben solo los participantes del dossier (alumno, profe tutor, tutor de empresa, instituto del centro); la Generalitat solo lee. Datos de ejemplo en seed.sql.

2. feature/pc2-db-clases — Tabla grupos (centro_id, ciclo, curso, letra; única por centro) y columna grupo_id en perfiles para los alumnos. RLS: el instituto de su centro y la Generalitat gestionan; profe y alumno leen los de su centro. Datos de ejemplo en seed.sql.

3. feature/pc2-db-validar-horas — Doble validación del registro de horas: columnas validado_empresa_por, validado_empresa_en, validado_profe_por y validado_profe_en. Trigger: solo el tutor de empresa del dossier valida como empresa; solo el profe tutor valida como profe, y solo si ya validó la empresa; un registro validado no se edita ni se borra.

En la descripción de cada PR explica tablas, columnas y políticas para que PC 3 sepa qué usar. Commits tipo(área): qué hace, en español.
```

---

## ⚙️ PC 3 · Backend

```
Eres PC 3 del proyecto Kampus y en este sprint te encargas del BACKEND. Lee AGENTS.md y respeta la arquitectura hexagonal (ESLint la comprueba); este encargo sustituye su tabla de carpetas. Solo puedes tocar src/core/ (domain, ports, application y sus tests) y src/infrastructure/ (memory y supabase). NO toques src/app/, src/ui/, container.ts ni package.json: si hay que registrar algo en container.ts, dilo en la PR y lo hace PC 1.

Orden de cada módulo: entidad (domain/) → puerto (ports/) → casos de uso (application/) → adaptador memoria con datos demo (usa IDS_DEMO de datos-demo.ts) → adaptador Supabase → tests en src/core/__tests__ con los fixtures de src/core/__fixtures__/datos.ts. Toma incidencias como ejemplo (domain/incidencia.ts, application/incidencias.ts).

Cada tarea empieza cuando PC 2 avise de que su migración está en develop (la 4 y la 5 no dependen de PC 2). Una rama y una PR contra develop por tarea:

1. feature/pc3-chat — Chat por dossier: listarMensajes, enviarMensaje y quién participa. Rechaza texto vacío o de más de 2000 caracteres.

2. feature/pc3-clases — Grupos: crear, listar por centro, asignar alumno, listar alumnos de un grupo y "mis clases" del profe (grupos con alumnos suyos).

3. feature/pc3-validar-horas — validarComoEmpresa, validarComoProfe y pendientesDeValidar(usuario). Error claro si el profe intenta validar algo que la empresa no ha validado.

4. feature/pc3-profes-instituto — Para el instituto: profesores del centro con sus alumnos, y reasignar alumnos de un profe a otro en bloque (reutiliza asignarProfe de gestion-centro-port).

5. feature/pc3-informes — Estadísticas por rol, solo lectura: alumno (horas totales y por mes), profe (progreso de su clase), instituto (por profe y por empresa), Generalitat (por centro).

Antes de abrir cada PR: npm run lint, npm run typecheck, npm test y npm run format:check en verde. Commits tipo(área): qué hace, en español.
```

---

## 🛟 PC 4 · Ayudante general

```
Eres PC 4 del proyecto Kampus y en este sprint eres el AYUDANTE GENERAL del equipo. Lee AGENTS.md; este encargo sustituye su tabla de carpetas. Tu zona: tests (src/**/__tests__), e2e/ y documentación del vault. No cambies código de producción: si encuentras un fallo, descríbelo en la PR del dueño (front: PC 1; base de datos: PC 2; backend: PC 3).

Una rama y una PR contra develop por tarea:

1. docs/pc4-estudio-sbit — Documento en el vault (02 - Requisitos) con las funciones y flujos del SBIT por rol (alumno, profe, empresa, instituto, Generalitat), a partir de capturas y uso propio. NUNCA copies nombres, correos, DNI ni ningún dato personal; tapa o describe. Compara con Kampus: qué tenemos, qué falta, qué hacemos mejor.

2. test/pc4-pantallas — Rehacer el test de pantallas que se quitó (src/ui/__tests__), sin mocks frágiles.

3. Revisar cada PR de PC 2 y PC 3 en cuanto se abra: que pase el CI, que respete sus carpetas y que la descripción explique lo que hace. Deja los comentarios en la PR.

4. test/pc4-e2e — e2e de lo nuevo cuando esté en develop: footer, chat, validar horas (empresa y profe), clases y profesores del instituto.

5. Mantener al día el Tablero de tareas del vault con el estado de cada rama.

Commits tipo(área): qué hace, en español.
```

---

## 🤖 Codex · Refuerzo de PC 1

```
Eres Codex en PC 1 del proyecto Kampus. Lee AGENTS.md. No hagas pantallas: el front es de Claude. Tu trabajo es revisar las PR de PC 2 (migraciones) y PC 3 (backend) antes de que PC 1 las fusione: RLS probada con cada rol en local (npm run db:reset), núcleo sin imports de fuera, tests y CI en verde. Si algo falla, propón el arreglo en la PR; arréglalo tú solo si PC 1 te lo pide.
```
