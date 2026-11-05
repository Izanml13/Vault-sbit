# 📊 Qué ha hecho cada uno · 26 oct – 4 nov 2026

**Fuente:** historial de git de `main` en `bose069-web/SBIT_BIRM`, del 26 de octubre al 4 de noviembre.
**Tablero Trello:** [Kampus · 26 oct – 4 nov 2026](https://trello.com/b/2xv3kOiw/kampus-26-oct-4-nov-2026)
**Qué cuenta:** 164 commits (sin contar merges) en 8 días laborables. El 31 de octubre y el 1 de noviembre fueron fin de semana y no hubo actividad.

---

## 1. De un vistazo

| Quién | Rol | Commits | Días activos | Peso |
|---|---|---:|---:|---|
| Izan | PC 1 · núcleo, base de datos, diseño | 115 | 7 | 70 % |
| Boubacar | PC 2 · pantallas y utilidades | 31 | 7 | 19 % |
| Richard | PC 3 · componentes y backend | 16 | 5 | 10 % |
| Marco | PC 4 · QA y panel web | 2 | 2 | 1 % |

Siete releases a producción en el periodo: 29 oct (1), 2 nov (3), 3 nov (2) y 4 nov (1).

```
         26  27  28  29  30  02  03  04
Izan      9  15  35  16  18  17   5   -
Boubacar  2   5   8   2   -  10   3   1
Richard   -   1   7   3   -   3   -   2
Marco     -   1   -   1   -   -   -   -
```

---

## 2. Izan · PC 1

Dueño del núcleo, la base de datos y el sistema de diseño. El 28 de octubre hizo 35 commits, el día más cargado de todo el periodo.

- **26 oct** — Esquema inicial de Supabase con RLS por rol. Núcleo de dossier y registro diario (dominio, puertos, casos de uso y adaptadores). Marca Kampus, tema monocromo e imagen Docker.
- **27 oct** — Base de datos por migraciones con CI y despliegue automático. Modelo ER con los cinco roles, centros, empresas y convenios. Login, pestañas por rol y pantalla del instituto. Núcleo de tareas y calendario, con tests en CI.
- **28 oct** — Incidencias de punta a punta. Dossiers, perfil editable y centros de la Generalitat. Sistema de diseño y calendario estilo Apple. Inicio del alumno rediseñado y barra inferior. Flujo de ramas con `develop`.
- **29 oct** — Chat directo en tiempo real y chat de empresa unificado. Registro del día más visual y perfil por secciones.
- **30 oct** — Registro robusto (autoguardado, sin conexión, guardado atómico). Historial del dossier con triggers y panel de gestión del instituto. Validaciones en bloque, avisos agrupados y arreglos de iOS.
- **2 nov** — Recuperación de contraseña con aviso al profe. Seguimiento con calendario de horas y corrección por el tutor. Clases y toques conectados, modo claro/oscuro y reasignación de alumnos.
- **3 nov** — Login con idioma y tema, rediseño de Validaciones y del panel del instituto.

## 3. Boubacar · PC 2

Pantallas, utilidades y buena parte de las migraciones de datos.

- **26 oct** — Migración de roles y valoraciones mensual y final.
- **27 oct** — Calendario mensual del alumno y registro diario en el móvil. Estados de carga, tareas y vista de la Generalitat.
- **28 oct** — Nuevo Inicio del profe con inbox, horas por validar y avisos. Ficha del dossier, y clases y toques en la base de datos.
- **29 oct** — Inicio y Seguimiento del profe con el estilo del alumno.
- **2 nov** — Confirmación del mes por el profe y correo sincronizado. Seguridad de la base (funciones fuera del alcance de `anon` e índices). Calendario de la Generalitat. Catalán, partes 1 y 2.
- **3 nov** — Catalán en el resto de la app (partes 3 y 4). Alta de institutos desde el Inicio de la Generalitat.
- **4 nov** — Enrutado de incidencias según sobre qué van.

## 4. Richard · PC 3

Componentes, accesibilidad y el lado de la empresa.

- **27 oct** — Logo de Kampus, calendario, accesibilidad y datos demo.
- **28 oct** — Profes del centro con sus alumnos y reasignar en bloque. Informes con estadísticas por rol. Componentes de tareas, iconos de pestañas y arreglos de contraste y teclado.
- **29 oct** — Inicio de la empresa con ritmo y avisos, Validaciones y chat por hilo.
- **2 nov** — Clases, toques y confirmación del mes valorado.
- **4 nov** — Distribución de pantallas y límite diario de copia.

## 5. Marco · PC 4

- **27 oct** — Tests E2E con Playwright de login y registro de día.
- **29 oct** — Panel del instituto con las cifras arriba y dos columnas en web ancha.

---

## 6. Cosas que conviene mirar

1. **El reparto está muy desequilibrado.** Izan ha hecho el 70 % de los commits; Marco, el 1 %. Puede ser que PC 4 (QA y panel web) tenga menos que tocar en el repo de la app, pero merece una conversación en la próxima reunión.
2. **Hay commits directos a `develop`.** Los dos de Richard del 4 de noviembre entraron sin PR y salieron a producción sin que nadie los revisara. AGENTS.md dice que toda rama vuelve a `develop` por PR.
3. **`main` y `develop` siguen sin proteger.** Es lo que permite el punto anterior. Sigue pendiente (ver [[Flujo de ramas]]).
4. **Quedan 29 ramas de trabajo sin borrar en el remoto.** AGENTS.md dice que la rama se borra al fusionar.
5. **Vercel tiene 16 variables de entorno de más**, metidas por la integración de Supabase, entre ellas claves de administrador que esta app no usa. No se filtran al navegador, pero sobran.
