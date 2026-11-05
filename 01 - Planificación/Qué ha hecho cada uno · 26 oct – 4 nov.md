# 📊 Qué ha hecho cada uno · 26 oct – 4 nov 2026

**Tablero Trello:** [Kampus · 26 oct – 4 nov 2026](https://trello.com/b/2xv3kOiw/kampus-26-oct-4-nov-2026)
**Periodo:** del 26 de octubre al 4 de noviembre. Ocho días laborables; el 31 de octubre y el 1 de noviembre fueron fin de semana.

**Cómo está contado:** por **tareas**, no por commits. Una tarea es una cosa que quedó hecha y funcionando, aunque haya costado cuatro PRs y dos días (como el sistema de idiomas) o un único commit. Contar commits mide quién teclea más, no quién entrega más: aquí se mide lo entregado.

---

## 1. De un vistazo

| Quién | Rol | Tareas |
|---|---|---:|
| Izan | PC 1 · núcleo, base de datos y diseño | 18 |
| Boubacar | PC 2 · pantallas y utilidades | 15 |
| Richard | PC 3 · componentes y backend | 12 |
| Marco | PC 4 · QA y panel web | 2 |
| **Todos** | releases y despliegue | 5 |

Cinco entradas en «Todos»: las subidas a producción y el despliegue en Vercel, que llevan dentro trabajo de varios.

---

## 2. Izan · PC 1 — 18 tareas

Núcleo, base de datos y sistema de diseño: la base sobre la que trabaja el resto.

1. Esquema y modelo de datos de Supabase (26–27 oct)
2. Núcleo hexagonal: dossier, registro diario, tareas y calendario (26–27 oct)
3. Marca Kampus y sistema de diseño (26–28 oct)
4. Base de datos por migraciones, con CI y despliegue automático (27 oct)
5. Login y navegación por rol (27 oct)
6. Tests unitarios con Jest en el CI (27 oct)
7. Incidencias: abrir, atender, escalar y resolver (28 oct)
8. Flujo de ramas con develop y ramas por tipo (28 oct)
9. Inicio del alumno, portada y barra inferior (28–29 oct)
10. Dossiers: crear, editar, borrar e historial (28–30 oct)
11. Perfil de usuario (28 oct – 3 nov)
12. Chat directo en tiempo real (29–30 oct)
13. Registro del día: rediseño y robustez (29–30 oct)
14. Validaciones mensuales en bloque (30 oct)
15. Panel de gestión del instituto (30 oct – 2 nov)
16. Recuperación de contraseña con aviso al profe (2 nov)
17. Seguimiento: calendario de horas y corrección por el tutor (2 nov)
18. Clases y toques conectados en la app (2 nov)

## 3. Boubacar · PC 2 — 15 tareas

Pantallas, utilidades y buena parte de las migraciones de datos.

1. Migración de roles y valoraciones mensual y final (26 oct)
2. Calendario mensual del alumno (27 oct)
3. Registro diario cómodo en el móvil (27 oct)
4. Estados de carga, error y vacío en los tres paneles (27 oct)
5. Pantallas de tareas y fechas del calendario (27–28 oct)
6. Ficha de solo lectura del dossier (28 oct)
7. Clases y toques en la base de datos (28 oct)
8. Inicio del profe con inbox, horas por validar y avisos (28–29 oct)
9. El profe confirma el mes que validó la empresa (2 nov)
10. El correo del perfil sigue al de la cuenta (2 nov)
11. Seguridad de la base de datos e índices (2 nov)
12. Calendario de la Generalitat con las fechas de toda la red (2 nov)
13. Sistema de idiomas: castellano y catalán (2–3 nov)
14. La Generalitat da de alta institutos desde Inicio (3 nov)
15. Enrutar cada incidencia según sobre qué va (4 nov)

## 4. Richard · PC 3 — 12 tareas

Componentes, accesibilidad y el lado de la empresa.

1. Logo de Kampus, calendario, accesibilidad y datos demo (27 oct)
2. Profes del centro con sus alumnos y reasignar en bloque (28 oct)
3. Informes con estadísticas por rol (28 oct)
4. Componentes de tareas e iconos de pestañas (28 oct)
5. Accesibilidad: contraste en modo oscuro y teclado (28 oct)
6. Inicio de la empresa con ritmo, avisos y Validaciones (29 oct)
7. Chat de la empresa por hilo con cada alumno y profe (29 oct)
8. El tutor de empresa cambia su correo de acceso (29 oct)
9. Clases: el instituto reparte y el profe ve las suyas (2 nov)
10. Toques: el profe avisa al alumno que no apunta (2 nov)
11. El profe confirma el mes valorado por la empresa (2 nov)
12. Distribución de pantallas y límite diario de copia (4 nov)

## 5. Marco · PC 4 — 2 tareas

1. Tests E2E con Playwright de login y registro de día (27 oct)
2. Panel del instituto: cifras arriba y dos columnas en web ancha (29 oct)

## 6. Todos — 5 entradas

1. Release: perfil, chat directo, Inicio por rol y calendario (29 oct)
2. Releases: alta de alumnos, registro atómico, clases y toques (2 nov)
3. Releases: catalán en toda la app y tema en el perfil (3 nov)
4. Release: enrutado de incidencias y ajustes de pantallas (4 nov)
5. Despliegue de la web en Vercel desde `main` (4 nov)

---

## 7. Cosas que conviene mirar

1. **Hay tres personas en un rango parecido** (18, 15 y 12 tareas) y una muy por debajo. Con Marco conviene hablar: puede que PC 4 (QA y panel web) tenga poco que tocar en este repo y su trabajo esté fuera de él, o puede que esté esperando a que alguien le desbloquee algo.
2. **Hay solapes entre personas.** Clases, toques y la confirmación del mes aparecen en tres listas a la vez: Bouba hizo las migraciones, Richard las pantallas e Izan las conectó. Funcionó, pero tres personas en la misma funcionalidad sin repartirlo antes es un riesgo de choque.
3. **Hay commits directos a `develop`.** Los dos de Richard del 4 de noviembre entraron sin PR y salieron a producción sin revisión. AGENTS.md dice que toda rama vuelve a `develop` por PR.
4. **`main` y `develop` siguen sin proteger.** Es lo que permite el punto anterior. Sigue pendiente (ver [[Flujo de ramas]]).
5. **Quedan 29 ramas de trabajo sin borrar en el remoto**, cuando la norma es borrarlas al fusionar.
6. **Vercel tiene 16 variables de entorno de más**, metidas por la integración de Supabase, entre ellas claves de administrador que esta app no usa.

> Una advertencia sobre el número de tareas: no todas pesan lo mismo. «Esquema y modelo de datos de Supabase» y «El tutor de empresa cambia su correo» cuentan las dos como una. La tabla sirve para ver el reparto a grandes rasgos, no para puntuar a nadie.
