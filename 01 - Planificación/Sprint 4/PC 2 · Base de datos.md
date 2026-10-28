# 🗄️ PC 2 · Base de datos · OpenCode

[⬅ Volver al reparto](../Encargos%20sprint%204.md) · **Prompt para pegar en OpenCode:** en [Encargos sprint 4](../Encargos%20sprint%204.md), bloque "PC 2"

**Persona:** _(escribe tu nombre)_
**Tu zona:** `supabase/migrations/` (solo migraciones nuevas, nunca editar una que ya esté en `main`) y `supabase/seed.sql`. No tocas `src/`.
**Cuando se fusione cada PR:** avisa a PC 3, que monta el backend encima.

## Tareas (en orden, marca `[x]` al terminar)

- [ ] **`feature/pc2-db-chat`**: mensajes de chat por dossier. RLS: leen y escriben alumno, profe tutor, tutor de empresa e instituto del centro; la Generalitat solo lee. Datos en el seed.
- [ ] **`feature/pc2-db-clases`**: tabla `grupos` (ciclo, curso, letra, centro) y `grupo_id` en los alumnos. RLS: instituto y Generalitat gestionan; profe y alumno leen.
- [ ] **`feature/pc2-db-validar-horas`**: doble validación (primero la empresa, luego el profe). Un registro validado no se edita ni se borra.

## Cómo comprobar cada una

1. `npm run db:reset` en local.
2. Entra como cada rol y comprueba qué ve y qué puede cambiar.
3. En la PR explica tablas, columnas y políticas para PC 3.
