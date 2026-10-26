# 🔍 Análisis del SBIT — 2026-10-26

Volver a [[Inicio]] · Siguiente: [[Requisitos funcionales]]

> Capturas revisadas por el equipo (web y app móvil del alumno). **No se guardan aquí capturas con datos personales** (DNI, fechas de nacimiento, nombres reales…).

## Qué es
Herramienta de seguimiento de las prácticas de FP (FCT / Dual): el alumno registra cada día las horas dedicadas a cada actividad formativa de su dossier y el tutor lo revisa.

## Pantallas actuales
| Pantalla | Qué hace | Problemas |
|---|---|---|
| Inicio de sesión | Usuario genérico | Sin roles visibles, sin recuperación clara |
| Agenda (web) | Tareas pendientes/hoy + calendario mensual | Mucho espacio vacío; leyenda de colores confusa |
| Activitat diària | Datos del dossier (centro, empresa, tutor, periodo, horas máx./introducidas) + horas por cada actividad con un desplegable | Formulario muy largo, lento de rellenar, sin guardar borrador |
| Agenda (app) | Calendario con eventos por día | Textos cortados ("Ac…"), colores sin significado claro |
| Missatgeria | Bandeja de mensajes | Básica, sin tiempo real |
| Usuario | Pestañas Usuario (idioma, regenerar contraseña) y Personal (datos del alumno) | Solo lectura, sin ajustes útiles |
| Ajuda / Sortir | Ayuda estática y cerrar sesión | — |

## Esquema de la pizarra (TEAM BIRM)
- Perfil · menú (agenda, mensajes, ayuda, salir) · **chatbots**
- Tareas · Calendario · Agenda
- **Usuarios:** User (alumno), Profe, Admin
- Primer paso: **inicio de sesión**

## Entidades detectadas
`Usuario` (rol) · `Dossier` (alumno, centro, empresa, centro de trabajo, tutor, estudio, periodo, horas máximas) · `ActividadFormativa` (código, descripción, jerarquía 1 → 1.1) · `RegistroDiario` (fecha, horas por actividad, estado) · `Tarea` · `Mensaje` · `Evento de calendario` (festivo, ausencia, baja…)

## Conclusión
Kampus cubre todo lo del SBIT pero rediseñado desde cero: registro diario en segundos, panel "Hoy" con progreso, calendario con estados claros, vista del profesor para validar, chat y asistente con IA.
