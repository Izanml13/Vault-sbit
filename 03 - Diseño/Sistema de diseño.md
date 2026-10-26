# 🎨 Sistema de diseño — Kampus

Volver a [[Inicio]] · Ver [[Arquitectura y stack]]

Definido el 2026-10-26 con la skill *ui-ux-pro-max* y revisado por el agente UI Designer. **Todos los pares pasan WCAG AA (4.5:1) en claro y oscuro.**
Lo implementa **PC 3** en `src/ui/theme/` y lo usa **PC 4** en Figma.

## Estilo
Flat moderno, neutro por defecto. El color sale de los datos (estados, progreso) y de **una sola acción por pantalla**. Sin sombras (solo modales), iconos de trazo, sin emoji.

## Colores

| Token | Claro | Oscuro | Uso |
|---|---|---|---|
| primary | `#4F46E5` | `#818CF8` | Marca, navegación, botones primarios, progreso |
| onPrimary | `#FFFFFF` | `#0B1020` | Texto sobre primary |
| primarySoft | `#EEF0FF` | `#1E2147` | Fondos tintados, botón secundario |
| accent | `#C2410C` | `#FB923C` | **Solo** la acción principal (CTA, FAB, badge) — máx. 1 por pantalla |
| onAccent | `#FFFFFF` | `#1A1205` | Texto sobre accent |
| background | `#F5F7FF` | `#0B1020` | Fondo de pantalla |
| surface | `#FFFFFF` | `#151B2E` | Tarjetas |
| surfaceAlt | `#EEF0FF` | `#1E2440` | Superficies secundarias |
| border | `#E0E3F5` | `#2A3350` | Bordes de 1 px |
| text | `#1E1B4B` | `#E2E8F0` | Texto principal |
| textMuted | `#575A7A` | `#94A3B8` | Texto secundario |
| success | `#15803D` | `#4ADE80` | |
| warning | `#B45309` | `#FBBF24` | |
| danger | `#DC2626` | `#F87171` | |
| info | `#0369A1` | `#38BDF8` | |

> `#EA580C` (naranja original) **no pasa AA** con texto: solo para iconos o decoración grande.

## Estados (fondo / texto) — nunca solo color

| Estado | Claro | Oscuro | Icono | Pista de forma |
|---|---|---|---|---|
| Validado | `#DCFCE7` / `#166534` | `#0F2A1C` / `#86EFAC` | check-circle | — |
| Registrado | `#E0E7FF` / `#3730A3` | `#1E2147` / `#A5B4FC` | clock-check | — |
| Pendiente | `#FEF3C7` / `#92400E` | `#2E2208` / `#FCD34D` | hourglass | Borde discontinuo |
| Ausencia | `#FEE2E2` / `#991B1B` | `#3A1414` / `#FCA5A5` | x-circle | — |
| Festivo | `#F1F5F9` / `#475569` | `#1F2937` / `#CBD5E1` | calendar-off | Relleno rayado |

Hoy en el calendario: anillo de 2 px en `primary`.

## Tipografía — Plus Jakarta Sans (400/500/600/700), números tabulares

| Rol | Tamaño / línea | Peso |
|---|---|---|
| Métrica grande | 40/44 (36 en pantallas pequeñas) | 700 |
| Título de pantalla | 28/34 | 700 |
| Título de sección | 20/26 | 600 |
| Título de tarjeta | 17/22 | 600 |
| Cuerpo | 16/24 | 400 |
| Cuerpo pequeño | 14/20 | 400 |
| Etiqueta | 12/16 | 500 |
| Botón | 16/20 | 600 |

Respetar el tamaño de texto del sistema (`allowFontScaling`), máx. 1.3× en métricas.

## Espaciado, radios y componentes
- Espaciado (base 4): 4 · 8 · 12 · 16 · 20 · 24 · 32 · 48 — margen de pantalla 20, padding de tarjeta 16, separación 12.
- Radios: 8 inputs pequeños · 12 botones/inputs · 16 tarjetas · 24 hojas inferiores · 999 chips/avatares.
- **Botón primario:** 52 alto, radio 12, `primary`/`onPrimary`, peso 600; al pulsar 90 % opacidad y escala 0.98.
- **Botón CTA:** igual con `accent` — uno por pantalla.
- **Secundario:** `primarySoft` + texto `primary`. **Fantasma:** sin fondo, texto `primary`, 44 alto.
- **Destructivo:** fantasma en `danger`; sólido solo en diálogos de confirmación.
- **Chip de estado:** 28 alto, radio total, icono 16 + texto 12/16 peso 600.
- Área táctil mínima 44×44; foco visible con anillo 2 px `primary`.
- Transiciones 150-200 ms ease-out; respetar "reducir movimiento".

## Reglas de personalidad
1. **Coral = "haz esto ahora".** Solo CTA principal, FAB y badge de pendientes.
2. **Índigo = marca y navegación.** Tab activa, enlaces, primarios, progreso. Superficies tintadas con `primarySoft`, nunca índigo sólido.
3. **El estado nunca depende solo del color:** icono + texto + forma.
4. **Neutro por defecto:** el color lo ponen los datos y una acción.
