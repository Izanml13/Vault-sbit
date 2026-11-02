# 🗄️ PC 2 · Base de datos · OpenCode

[⬅ Volver al reparto](../Encargos%20sprint%204.md) · **Prompt para pegar en OpenCode:** en [Encargos sprint 4](../Encargos%20sprint%204.md), bloque "PC 2"

**Persona:** Boubacar
**Tu zona:** `supabase/migrations/` (solo migraciones nuevas, nunca editar una que ya esté en `main`) y `supabase/seed.sql`. No tocas `src/`.
**Cuando se fusione cada PR:** avisa a PC 3, que monta el backend encima.

## Tareas (en orden, marca `[x]` al terminar)

- [x] ~~**`feature/pc2-db-chat`** (PR #13): mensajes de chat por dossier.~~ **Cerrada el 02/11**: la cubre el chat directo de Izan (`chat_mensajes`). Se reabre si hace falta chat de grupo.
- [x] **`feature/pc2-db-clases`** (PR #14, en `develop`): tabla `grupos` (ciclo, curso, letra, centro) y `grupo_id` en los alumnos. RLS: instituto y Generalitat gestionan; profe y alumno leen. Migración `20261102140000_grupos_clase.sql`.
- [x] **Doble validación** · ~~PR #15 por día (cerrada)~~ → **`feature/pc2-db-validar-mes`** (PR #26, en `develop`): la empresa valida el mes con la valoración mensual y el profe tutor lo confirma (`confirmada_por`, `confirmada_en`). Un mes confirmado no lo toca la empresa. Migración `20261102090000_confirmar_mes.sql`.

### Añadidas durante el sprint

- [x] **`feature/pc2-db-toques`** (PR #18, en `develop`): toques de atención del profe al alumno, uno al día, se resuelven al apuntar. `20261102150000_toques.sql`.
- [x] **`feature/pc2-db-correo`** (PR #27, en `develop`): `perfiles.email` sigue al correo de la cuenta. `20261102160000_sincronizar_email.sql`.
- [x] **`fix/pc2-db-seguridad`** (PR #28, en `develop`): funciones internas fuera del alcance de `anon` y 4 índices de claves foráneas. `20261102170000_seguridad_y_indices.sql`.
- [x] **`fix/pc2-fecha-grupos`** (PR #29, en `develop`): dos migraciones tenían la misma fecha y el CI de `develop` fallaba.

### Pendiente de Bouba como propietario del repo (no se puede hacer desde Claude)

- [x] GitHub → Settings → General → Default branch: **`develop`** (02/11).
- [ ] Settings → Branches: proteger `main` y `develop` (PR y CI obligatorios). **Aplazado al martes 03/11.**
- [x] Settings → General: activar **Automatically delete head branches** (02/11).

**Regla para todos:** una migración nueva siempre con **fecha posterior a la última de `develop`**. Si coincide o es anterior, `supabase db push` no la aplica en la nube o choca en `schema_migrations`.

## Cómo comprobar cada una

1. `npm run db:reset` en local.
2. Entra como cada rol y comprueba qué ve y qué puede cambiar.
3. En la PR explica tablas, columnas y políticas para PC 3.
