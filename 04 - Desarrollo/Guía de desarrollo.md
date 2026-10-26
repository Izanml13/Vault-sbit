# 🧪 Guía de desarrollo

- Repo del código: https://github.com/bose069-web/SBIT_BIRM (propietario: Bouba)
- Ramas: `main` estable, `feature/<nombre>` por tarea, PR para fusionar.
- Commits descriptivos en español.
- Documentar en este vault cada módulo terminado.

## Esqueleto del proyecto (2026-10-26)
- Expo (TypeScript, Expo Router) con pestañas **Inicio** y **Perfil**.
- `src/lib/supabase.ts`: cliente de Supabase con la sesión guardada. La pantalla de Inicio indica si la conexión funciona.
- Variables en `.env.local` (copiar de `.env.example`): `EXPO_PUBLIC_SUPABASE_URL` y `EXPO_PUBLIC_SUPABASE_KEY`.
- Comandos: `npm start` · `npm run lint` · `npm run typecheck` · `npm run format`.
- GitHub Actions ejecuta lint, comprobación de tipos y formato en cada PR. Hay plantilla de PR con checklist.
- Paquetes nuevos siempre con `npx expo install <paquete>`.
