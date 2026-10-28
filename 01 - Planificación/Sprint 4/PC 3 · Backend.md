# ⚙️ PC 3 · Backend · OpenCode

[⬅ Volver al reparto](../Encargos%20sprint%204.md) · **Prompt para pegar en OpenCode:** en [Encargos sprint 4](../Encargos%20sprint%204.md), bloque "PC 3"

**Persona:** _(escribe tu nombre)_
**Tu zona:** `src/core/` (domain, ports, application, tests) y `src/infrastructure/` (memory y supabase). No tocas pantallas, `container.ts` ni `package.json`: pídelo en la PR.
**Orden de cada módulo:** entidad → puerto → casos de uso → adaptador memoria → adaptador Supabase → tests. Ejemplo a copiar: incidencias.

## Tareas (marca `[x]` al terminar)

Se pueden empezar ya (no dependen de PC 2):
- [ ] **`feature/pc3-profes-instituto`**: profesores del centro con sus alumnos y reasignar alumnos en bloque
- [ ] **`feature/pc3-informes`**: estadísticas por rol (alumno, profe, instituto, Generalitat)

Cuando PC 2 avise de su migración:
- [ ] **`feature/pc3-chat`**: listar y enviar mensajes por dossier · *espera a `feature/pc2-db-chat`*
- [ ] **`feature/pc3-clases`**: grupos, asignar alumnos, "mis clases" del profe · *espera a `feature/pc2-db-clases`*
- [ ] **`feature/pc3-validar-horas`**: validar como empresa, como profe y pendientes · *espera a `feature/pc2-db-validar-horas`*

Cuando se fusione cada una, avisa a PC 1 para que haga la pantalla.
