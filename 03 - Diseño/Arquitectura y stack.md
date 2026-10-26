# 🎨 Arquitectura y stack — Kampus

Volver a [[Inicio]] · Ver [[Plan de trabajo]]

## Stack elegido (todo gratuito)

| Pieza | Herramienta | Alojamiento |
|---|---|---|
| App móvil (Android + iOS) | React Native + Expo (TypeScript) | En el móvil (Expo Go / APK) |
| Backend, base de datos y login | Supabase (PostgreSQL + Auth + Storage) | Nube de Supabase (plan gratuito) |
| Lógica de servidor (emails, informes, tareas programadas) | Supabase Edge Functions | Nube de Supabase |
| Panel web de administración + página de presentación | Next.js | Vercel (plan gratuito) |
| Código, revisiones y comprobaciones automáticas | GitHub + GitHub Actions | GitHub |

Repo del código: https://github.com/bose069-web/SBIT_BIRM

```
[App Expo] ──┐
             ├──► Supabase (BD · Auth · Storage · Edge Functions)
[Panel web en Vercel] ──┘
```

## Registro de decisiones

| Fecha | Decisión | Motivo | Descartado |
|---|---|---|---|
| 2026-10-26 | Nombre de la app: **Kampus** | Moderno, fácil de reconocer como marca | BIRM Edu, Aula+, SBIT Go, Edubit, Pupitre |
| 2026-10-26 | App con **React Native + Expo** | Se prueba en cualquier móvil con Expo Go sin Mac; JS/TS, que ya conocemos; una sola base de código | Flutter (Dart desde cero, Mac para iOS), nativo (doble trabajo) |
| 2026-10-26 | Backend con **Supabase** | Datos muy relacionados (alumnos, grupos, notas): SQL encaja; permisos por perfil con Row Level Security; código abierto; plan gratuito sin cobros sorpresa | Firebase (NoSQL, cobra por lectura/escritura, solo existe en Google) |
| 2026-10-26 | **Sin Render** ni servidor propio | Supabase ya da API, login y BD; la lógica extra va en Edge Functions; el plan gratuito de Render se duerme y tarda ~50 s en despertar | Render |
| 2026-10-26 | **Vercel** para panel de administración y página web | Secretaría y dirección trabajan en ordenador; una página pública da buena imagen; plan gratuito | — |

## Límites de los planes gratuitos
- **Supabase:** 500 MB de BD, 50.000 usuarios al mes; el proyecto se pausa tras 1 semana sin uso (se reactiva con un clic).
- **Publicar en tiendas (opcional, no hace falta para la entrega):** Google Play 25 $ una vez, App Store 99 $ al año.

## Estándares de calidad
- [ ] **Diseño primero:** mockups en Figma y guía de estilo propia (colores, logo, tipografía)
- [ ] **TypeScript + ESLint + Prettier** en todo el código
- [ ] **Ramas `feature/...` y Pull Requests** revisadas por otro compañero antes de fusionar
- [ ] **GitHub Actions:** revisión y pruebas automáticas en cada Pull Request
- [ ] **Seguridad:** Row Level Security por perfil; ninguna clave secreta en el repo (`.env` en `.gitignore`)
- [ ] **Accesibilidad:** buen contraste, textos ampliables, compatible con lector de pantalla
- [ ] **Documentación en el vault:** decisiones, actas y avance de cada sprint
- [ ] **Demo preparada:** datos de ejemplo realistas, vídeo de la app y página web publicada
