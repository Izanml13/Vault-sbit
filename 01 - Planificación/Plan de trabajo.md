# 📋 Plan de trabajo — Kampus

Volver a [[Inicio]] · Tareas en [[Tablero de tareas]]

## Fase 0 — Arranque
- [ ] Repartir roles → [[Equipo y roles]]
- [ ] Todos con el vault clonado y Obsidian Git configurado
- [ ] Reunión de kick-off (usar plantilla de reunión)

## Fase 1 — Análisis
- [ ] Analizar el SBIT de Educación: qué funciones tiene, qué usuarios, qué datos
- [ ] Redactar [[Requisitos funcionales]] y no funcionales
- [ ] Definir perfiles de usuario y casos de uso
- [ ] Priorizar funciones (MVP vs. extras)

## Fase 2 — Diseño
- [x] Elegir stack → [[Arquitectura y stack]] (Expo + Supabase + Vercel)
- [ ] Confirmar si podemos usar Supabase (si no, elegir otro backend y crear su adaptador)
- [x] Arquitectura hexagonal en el código
- [ ] Modelo de datos / base de datos
- [ ] Wireframes y mockups de pantallas (Figma) + guía de estilo
- [ ] Diseño del backend en Supabase (tablas, Row Level Security, Edge Functions)
- [ ] Configurar GitHub Actions, ESLint y Prettier en SBIT_BIRM

## Fase 3 — Desarrollo (sprints)
- [ ] Sprint 1: autenticación + navegación base
- [ ] Sprint 2: funciones principales del MVP
- [ ] Sprint 3: funciones secundarias
- [ ] Sprint 4: pulido, accesibilidad, notificaciones

## Fase 4 — Pruebas y entrega
- [ ] Pruebas funcionales y de usuario
- [ ] Corrección de errores
- [ ] Panel de administración y página web publicados en Vercel
- [ ] Documentación final, vídeo demo y presentación
