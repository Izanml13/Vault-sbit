# 🌿 Flujo de ramas (DEV · OPS · QA · DOCS)

Volver a [[Inicio]] · Ver [[Guía de desarrollo]] · [[Reparto por PCs]] · [[Tablero de tareas]]

Desde el 2026-10-28 el repo [SBIT_BIRM](https://github.com/bose069-web/SBIT_BIRM) sigue un **GitFlow ligero**: dos ramas fijas y ramas de trabajo con un prefijo según el tipo de cambio.

## Ramas fijas

| Rama | Para qué | Quién fusiona | Qué pasa al fusionar |
|---|---|---|---|
| `main` | **Producción.** Lo que está desplegado y se enseña. | PC 1, solo desde `develop` (release) o `hotfix/` | CI + las migraciones nuevas se suben solas a Supabase |
| `develop` | **Integración.** Donde se junta el trabajo de los 4 PCs. | PC 1, por PR | CI (lint, tipos, tests, formato y migraciones desde cero) |

Nadie hace commits directos en `main` ni en `develop`.

## Ramas de trabajo: `tipo/pcN-descripcion-corta`

| Área | Prefijo | Cuándo | Ejemplo | Quién |
|---|---|---|---|---|
| **DEV** | `feature/` | Funcionalidad nueva | `feature/pc2-formulario-dossier` | Todos |
| **DEV** | `fix/` | Corregir un fallo | `fix/pc3-contraste-modo-oscuro` | Todos |
| **OPS** | `ops/` | CI, workflows, Supabase/config, scripts, dependencias | `ops/pc1-flujo-ramas` | Solo PC 1 |
| **QA** | `test/` | Tests unitarios o e2e sin cambiar funcionalidad | `test/pc4-e2e-login` | Todos (sobre todo PC 4) |
| **DOCS** | `docs/` | Documentación del repo | `docs/pc1-readme` | Todos |
| **Urgente** | `hotfix/` | Fallo en producción que no puede esperar | `hotfix/pc1-login-roto` | Solo PC 1 |

- Las migraciones de base de datos van en la rama `feature/` o `fix/` del cambio que las necesita, y solo las escribe PC 1.
- `hotfix/` sale de `main`, vuelve a `main` y después se fusiona también en `develop`.

## Día a día

```bash
git checkout develop
git pull
git checkout -b feature/pc2-formulario-dossier
# ...trabajar...
npm run lint && npm run typecheck && npm test && npm run format:check
git push -u origin feature/pc2-formulario-dossier
```

1. Abre la PR **contra `develop`** (no contra `main`) y rellena la plantilla, incluido el tipo.
2. El CI tiene que salir en verde.
3. PC 1 revisa y fusiona. La rama se borra al fusionar.
4. Si `develop` ha avanzado mientras trabajabas: `git pull origin develop` en tu rama y resuelve conflictos antes de pedir revisión.

## Commits

Formato `tipo(área): qué hace`, en español.

| Tipo | Uso |
|---|---|
| `feat` | Funcionalidad nueva |
| `fix` | Corrección |
| `ops` | CI, despliegue, configuración |
| `test` | Tests |
| `docs` | Documentación |
| `refactor` | Cambiar código sin cambiar lo que hace |
| `chore` | Mantenimiento (formato, dependencias menores) |

Ejemplos: `feat(app): pantalla de tareas` · `fix(memory): ids de los datos demo` · `ops(ci): CI también en develop`.

## Releases (de `develop` a `main`)

- PC 1 abre una PR `develop → main` titulada `Release AAAA-MM-DD` con la lista de lo que entra.
- Antes de fusionarla: CI en verde y prueba rápida de los cinco roles en web y en el simulador.
- Al fusionarla, las migraciones nuevas se aplican solas en Supabase. Luego se etiqueta la versión (`v0.2.0`, `v0.3.0`…).
- Ritmo propuesto: una release al final de cada sesión de trabajo o antes de cada demo.

## Pendiente (lo tiene que hacer Bouba, propietario del repo)

- [ ] GitHub → Settings → General → Default branch: **`develop`**, para que las PR vayan ahí por defecto.
- [ ] Settings → Branches: proteger `main` y `develop` (exigir PR y CI en verde, sin push directo).
- [ ] Settings → General: activar **Automatically delete head branches**.
