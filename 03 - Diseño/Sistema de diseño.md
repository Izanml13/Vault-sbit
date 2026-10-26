# 🎨 Sistema de diseño — Kampus

Volver a [[Inicio]] · Ver [[Arquitectura y stack]]

**Monocromo, profesional y minimalista** (decidido el 2026-10-26, descartada la versión índigo/coral).
Lo implementa **PC 3** en `src/ui/theme/` y lo usa **PC 4** en Figma.

## Estilo
Negro, blanco y grises. Sin color decorativo: el único color son **puntos pequeños de estado**. Bordes finos de 1 px, sin sombras (solo modales), iconos de trazo, sin emoji.

## Colores

| Token | Claro | Oscuro | Uso |
|---|---|---|---|
| primary | `#0A0A0A` | `#FAFAFA` | Botones principales, tab activa, progreso, hoy en el calendario |
| onPrimary | `#FFFFFF` | `#0A0A0A` | Texto sobre primary |
| subtle | `#F4F4F5` | `#27272A` | Fondos suaves, pistas de progreso |
| background | `#FAFAFA` | `#09090B` | Fondo de pantalla |
| surface | `#FFFFFF` | `#18181B` | Tarjetas, inputs |
| border | `#E4E4E7` | `#27272A` | Bordes de 1 px |
| text | `#0A0A0A` | `#FAFAFA` | Texto principal |
| textMuted | `#71717A` | `#A1A1AA` | Texto secundario |
| danger | `#B91C1C` | `#F87171` | Errores y acciones destructivas |

## Estados — punto de color + texto (nunca fondo de color)

| Estado | Punto claro | Punto oscuro |
|---|---|---|
| Validado | `#15803D` | `#4ADE80` |
| Registrado | `primary` | `primary` |
| Pendiente | `#A16207` | `#FACC15` |
| Ausencia | `#B91C1C` | `#F87171` |
| Festivo | `#A1A1AA` | `#71717A` (número en gris) |

Chip de estado: fondo `surface`, borde `border`, punto de 6 px + texto 11-12 px peso 500.

## Tipografía — Inter (400/500/600), números tabulares
| Rol | Tamaño | Peso |
|---|---|---|
| Métrica grande | 34-40 | 600, tracking -3 % |
| Título de pantalla | 22-28 | 600, tracking -2 % |
| Título de tarjeta | 15-17 | 600 |
| Cuerpo | 14-16 | 400 |
| Secundario / etiqueta | 12 | 400-500 |

## Espaciado, radios y componentes
- Espaciado base 4: 4 · 8 · 12 · 16 · 20 · 24 · 32 — margen 16-20, padding de tarjeta 14-16.
- Radios: 8 controles pequeños · 10 botones e inputs · 14 tarjetas · 999 chips.
- **Botón principal:** fondo `primary`, texto `onPrimary`, 46-52 alto, peso 500. Uno por pantalla.
- **Secundario:** fondo `surface` con borde `border`. **Fantasma:** solo texto.
- Área táctil mínima 44×44; foco visible; transiciones 150-200 ms; respetar "reducir movimiento".

## Reglas
1. Si dudas, gris. El negro marca **lo importante** (acción principal, dato principal).
2. El color solo informa de un estado, y siempre acompañado de texto.
3. Jerarquía con tamaño y peso tipográfico, no con color.
