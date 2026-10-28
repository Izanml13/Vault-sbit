# 📋 Encargos sprint 4 · Front y comunicación (para pegar en OpenCode y Codex)

Volver a [[Tablero de tareas]] · Ver [[Flujo de ramas]] · [[Reparto por PCs]]

Cada PC copia **su** bloque entero y lo pega en su agente. Todos leen `AGENTS.md` del repo (arquitectura, carpetas permitidas y normas de ramas).

Antes de empezar, una sola vez y línea a línea (en PowerShell, sin `&&`):

```
git fetch origin --prune
git checkout develop
git pull
```

---

## ✅ Decisiones tomadas (2026-10-28)

| Tema | Decisión |
|---|---|
| Chat | **Un chat por alumno (por dossier)**: alumno, profe tutor, tutor de empresa e instituto en el mismo hilo. |
| Validar horas | **Doble validación**: el tutor de empresa valida las horas que registra el alumno; después el profe valida las que ya validó la empresa. Botón sencillo en los dos casos. |
| Clases | **Ciclo + curso + grupo** (ej. DAM 2º A). Las crea el instituto y les asigna alumnos. El profe navega Clases → Alumnos → Ficha. |
| Instituto | Gestiona **profesores** y qué alumnos tiene cada uno, no a los alumnos sueltos. |
| Footer | **Inicio · Calendario · Chat · Perfil** para todos los roles. Fuera el botón de registrar del footer; se queda el de Inicio. |
| Informes | Gráficos adaptados a cada rol (alumno: horas totales y por mes; profe: progreso de su clase; instituto: por profe y empresa; Generalitat: por centro). |
| SBIT | Solo estudiar **funciones y flujos** a partir de capturas y uso propio. **Sin datos personales.** |
| Diseño | UI UX Pro Max + Liquid Glass de Apple (cristal nativo en iOS, alternativa opaca en Android y web) + animaciones limpias. |

## 🗺️ Orden

1. **Fase 0 · Diseño** (PC 3 y PC 4, ya): sistema de diseño, cristal, animaciones, leyenda, estudio del SBIT.
2. **Fase 1 · Navegación** (PC 2, ya): footer nuevo.
3. **Fase 2 · Núcleo y migraciones** (PC 1: Claude + Codex): chat, clases, validación, profes del instituto, estadísticas.
4. **Fase 3 · Pantallas** (PC 2, según PC 1 avise): todo lo que usa la fase 2.
5. **Fase 4 · Calidad** (PC 4): e2e de lo nuevo.

---

## 🧠 PC 1 · Claude Code (Izan)

Lo hace Claude en esta sesión, en este orden:

1. `ops/pc1-selector-fecha`: cerrar la dependencia del selector de fecha (lo necesita el calendario desplegable de la Generalitat).
2. `feature/pc1-chat-dossier`: migración `chats` (un hilo por dossier, mensajes, RLS por participante del dossier), dominio, puerto, casos de uso, adaptadores memoria y Supabase.
3. `feature/pc1-informes`: casos de uso de estadísticas por rol (solo lectura, sin migración si es posible).

---

## 🤖 PC 1 · Codex

```
Eres Codex trabajando como PC 1 del proyecto Kampus. Lee AGENTS.md y respétalo (arquitectura hexagonal, ESLint de fronteras, migraciones nuevas nunca editando las de main). Trabaja desde develop actualizado. Una rama y una PR contra develop por tarea, en este orden. Claude está haciendo a la vez el chat y los informes: NO toques archivos de chat ni de informes.

1. feature/pc1-clases — Entidad Grupo (ciclo, curso, letra, centro_id) y alumnos asignados a un grupo. Migración nueva con RLS (instituto de su centro y Generalitat gestionan; profe y alumno leen los suyos). Dominio, puerto, casos de uso (crear, listar por centro, asignar alumno, listar alumnos de un grupo), adaptador memoria con datos demo (usa IDS_DEMO) y adaptador Supabase. Registrar en container.ts. Tests.

2. feature/pc1-validar-horas — Doble validación del registro de horas: primero el tutor de empresa del dossier valida el registro del alumno; después el profe tutor valida lo que ya validó la empresa. Migración nueva: columnas de validación (quién y cuándo, para empresa y para profe) y trigger que impida que el profe valide algo no validado por la empresa y que nadie edite un registro ya validado. Casos de uso validarComoEmpresa, validarComoProfe y pendientesDeValidar. Adaptadores y tests.

3. feature/pc1-profes-instituto — Casos de uso para el instituto: listar profesores del centro con sus alumnos asignados y reasignar alumnos de un profe a otro (en bloque). Reutiliza asignarProfe del puerto de gestión del centro. Tests.

Prueba cada migración en local (npm run db:reset). Antes de abrir cada PR: npm run lint, npm run typecheck, npm test y npm run format:check en verde. Commits tipo(área): qué hace, en español, a nombre de Izan.
```

---

## 📱 PC 2 · Pantallas

```
Eres PC 2 del proyecto Kampus. Lee AGENTS.md y respétalo: solo puedes tocar src/app/, src/ui/hooks/, src/ui/vistas/ y src/ui/utils/. Si necesitas cambiar un puerto, un caso de uso, container.ts o package.json, NO lo hagas: descríbelo en la PR.

Una rama y una PR contra develop por tarea, en este orden:

1. feature/pc2-footer — Barra inferior igual para todos los roles: Inicio, Calendario, Chat y Perfil. Quita Registrar del footer (el registro se hace desde el botón de Inicio, que se mantiene). Chat de momento puede ser una pantalla vacía con "Próximamente". Lo que hoy cuelga de otras pestañas (Seguimiento, Centro) se abre desde Inicio.

2. feature/pc2-calendario — Rediseño completo del calendario (src/ui/vistas/agenda.tsx) usando los componentes nuevos de PC 3 (leyenda, chips, animaciones). Vista de mes clara, día seleccionado, lista del día debajo.

NO empieces lo siguiente hasta que PC 1 avise de que está en develop:
3. feature/pc2-formulario-dossier e feature/pc2-incidencias (ya desbloqueadas: los casos de uso están en develop).
4. feature/pc2-chat — pantalla de chat por alumno.
5. feature/pc2-clases-profe — Clases → Alumnos → Ficha, con botón Validar horas.
6. feature/pc2-validar-empresa — botón Validar horas para el tutor de empresa.
7. feature/pc2-profes-instituto — pantalla del instituto: profesores y sus alumnos.
8. feature/pc2-informes — gráficos por rol en Inicio.
9. feature/pc2-generalitat-fechas — selector de días con calendario desplegable.

Antes de abrir cada PR: npm run lint, npm run typecheck, npm test y npm run format:check en verde. Commits tipo(área): qué hace, en español.
```

---

## 🧩 PC 3 · Componentes, tema y datos de prueba

```
Eres PC 3 del proyecto Kampus. Lee AGENTS.md y respétalo: solo puedes tocar src/ui/components/, src/ui/theme/ y src/infrastructure/memory/. Si necesitas cambiar un puerto, un caso de uso, container.ts o package.json (por ejemplo instalar expo-glass-effect), NO lo hagas: pídelo en la PR para que lo haga PC 1.

Usa la skill UI UX Pro Max para todas las decisiones visuales. Una rama y una PR contra develop por tarea:

1. feature/pc3-sistema-diseno — Revisa theme.ts con UI UX Pro Max y deja tokens claros (colores, espaciados, radios, tipografía, sombras) para claro y oscuro. Documenta en la PR las decisiones.

2. feature/pc3-cristal — Componente Cristal (tarjeta/HUD estilo Liquid Glass de Apple): efecto nativo en iOS, alternativa opaca en Android y web. Si hace falta expo-glass-effect, pídelo en la PR.

3. feature/pc3-animaciones — Animaciones limpias y cortas (entrada de tarjetas, pulsación de botones, cambio de pestaña) respetando "reducir movimiento" del sistema.

4. feature/pc3-leyenda — Componente Leyenda reutilizable (calendario y gráficos), accesible y sin depender solo del color.

5. feature/pc3-graficos — Componentes de gráfico sencillos (barra de progreso de horas, barras por mes) para los informes por rol.

Antes de abrir cada PR: npm run lint, npm run typecheck, npm test y npm run format:check en verde. Commits tipo(área): qué hace, en español.
```

---

## 🖥️ PC 4 · Diseño, estudio y e2e

```
Eres PC 4 del proyecto Kampus. Lee AGENTS.md y respétalo: tu zona es el panel web, e2e/ y diseño.

1. docs/pc4-estudio-sbit — Documento en el vault (02 - Investigación) con las funciones y flujos del SBIT por rol (alumno, profe, empresa, instituto, Generalitat), a partir de capturas y uso propio. NUNCA copies nombres, correos, DNI ni ningún dato personal; tapa o describe. Compara con Kampus: qué tenemos, qué falta, qué hacemos mejor.

2. Diseño en Figma de las pantallas nuevas (footer, calendario, chat, clases del profe, informes) siguiendo el sistema de diseño de PC 3.

3. test/pc4-pantallas — Rehacer el test de pantallas que se quitó, y e2e de: footer nuevo, chat, validar horas (empresa y profe) y clases (cuando estén en develop).

Antes de abrir cada PR: npm run lint, npm run typecheck, npm test y npm run format:check en verde. Commits tipo(área): qué hace, en español.
```
