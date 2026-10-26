# 📑 Requisitos funcionales — Kampus

Volver a [[Inicio]] · Basado en [[Análisis SBIT]]

## Perfiles
| Rol | Descripción |
|---|---|
| **Alumno** (User) | Registra sus horas diarias, ve tareas, calendario y mensajes |
| **Profe** (tutor de centro) | Sigue a sus alumnos, valida días, envía tareas y mensajes |
| **Admin** | Gestiona usuarios, centros, empresas, dossiers y periodos |

> A valorar: rol **tutor de empresa** (valida desde la empresa).

## Funciones
| ID | Función | Perfil | Prioridad | Estado |
|---|---|---|---|---|
| RF-01 | Inicio de sesión por rol, recuperar contraseña, sesión guardada | Todos | MVP | Esqueleto hecho |
| RF-02 | Panel "Hoy": horas del día, progreso del periodo, tareas, avisos | Alumno | MVP | |
| RF-03 | Registro diario: horas por actividad formativa, copiar día anterior, notas | Alumno | MVP | |
| RF-04 | Calendario mensual/semanal con estados (registrado, pendiente, validado, festivo, ausencia) | Alumno, Profe | MVP | |
| RF-05 | Tareas: pendientes, hoy, hechas | Alumno, Profe | MVP | |
| RF-06 | Datos del dossier (centro, empresa, tutor, periodo, horas) | Alumno, Profe | MVP | |
| RF-07 | Lista de alumnos, validar/rechazar días con comentario | Profe | MVP | |
| RF-08 | Alertas de días sin registrar | Profe | MVP | |
| RF-09 | Perfil: idioma (ca/es/en), modo oscuro, cambiar contraseña | Todos | MVP | |
| RF-10 | Notificaciones push (tareas, validaciones, recordatorio diario) | Todos | Extra | |
| RF-11 | Chat en tiempo real alumno–profe con adjuntos | Alumno, Profe | Extra | |
| RF-12 | Asistente con IA (ayuda, resumen semanal, sugerir actividades) | Alumno | Extra | |
| RF-13 | Cuaderno de prácticas en PDF y estadísticas | Alumno, Profe | Extra | |
| RF-14 | Panel web de administración (usuarios, centros, empresas, periodos, CSV) | Admin | Extra | |
| RF-15 | Registro sin conexión y sincronización | Alumno | Extra | |
| RF-16 | Fotos/adjuntos en el registro diario | Alumno | Extra | |

## Requisitos no funcionales
- Android e iOS (Expo) + web para el panel de administración
- Accesible (WCAG AA), modo oscuro, textos ampliables
- Multidioma: catalán, castellano, inglés
- Protección de datos (RGPD): mínimo de datos personales, permisos por rol
- Respuesta rápida: registrar un día en menos de 30 segundos
