# Cuentas, datos y validación

Decisiones del equipo (pizarra del 28 oct 2026). Relacionado: [[Análisis SBIT]], [[Requisitos funcionales]].

## Cuentas

- **Alta:** el instituto crea las cuentas, se las pasa al tutor y el tutor las entrega a sus alumnos con contraseña incluida.
- **Primer login:** se obliga a cambiar la contraseña, para que el tutor no conozca la definitiva.
- **¿Has olvidado tu contraseña?:** está en el login; el enlace llega al email del alumno. No hay cambio de contraseña en el perfil.
- **Identidad bloqueada:** el alumno no puede cambiar su nombre (ni DNI, dirección o NUSS). Lo gestionan su tutor y su instituto, así nadie usa la cuenta de otro sin pasar por el tutor.

## Datos personales

- **Edita el propio usuario:** teléfono, idioma, avisos y los datos de su rol.
  - Profe: departamento y horario de tutoría.
  - Empresa: cargo, teléfono de trabajo y centro de trabajo.
  - Instituto: cargo.
- **Contacto de emergencia:** lo introduce el alumno y lo valida su tutor; mientras no lo valide se muestra como "pendiente". Si es menor, es obligatorio y tiene que ser un familiar responsable.
- **Menor de edad:** se calcula con la fecha de nacimiento que pone el instituto al crear la cuenta.
- **Datos sensibles (pendiente de confirmar con el DPD del centro):**
  - DNI/NIE, fecha de nacimiento y NUSS van en una tabla aparte. La editan el instituto y el profe, el alumno la ve en solo lectura y la empresa no la ve.
  - En pantalla se muestran enmascarados y cada cambio queda registrado.
  - La dirección solo se guarda si se generan documentos con ella.
  - Salud e IBAN no se guardan.
- **El tutor ya ve el teléfono del alumno:** no hace falta un interruptor para compartirlo.

## Validación de horas

1. El alumno ficha sus horas.
2. Al acabar el mes, la empresa valida el mes. Desde ese momento el alumno ya no puede tocar esas horas.
3. El profe confirma: revisa las horas y que la empresa las ha validado.

- **Si el profe ve un error:** lo comunica a la empresa y avisa al alumno. Si es grave, también al instituto o a la generalitat.
- **Si la empresa no valida a tiempo:** recibe un recordatorio automático el día 1 del mes siguiente y otro el día 5 si sigue sin validar.

## Retirar las prácticas ("beca")

- La empresa pide quitar las prácticas a un alumno, con un motivo, y el instituto lo aprueba.
- El dossier queda cerrado como baja, en solo lectura, con las horas hechas hasta ese día.
- Se avisa al profe y al alumno.

## Inicio por rol

- **Alumno:** total de horas, registro y tareas pendientes.
- **Profe:**
  - Clase con la lista de su alumnado (barra de abajo en la app, header en la web). Suele tener una sola clase.
  - Inbox de recientes.
  - Horas validadas por la empresa, pendientes de confirmar.
  - Usuarios que no entran o no registran horas, con un "toque" (notificación push).
- **Empresa:** validar las horas de sus alumnos e inbox de lo importante.
- **Instituto:** tutores y clases que gestiona, e inbox.
- **Generalitat:** institutos que gestiona.

## Notificaciones push

- Decisión: se compila un **APK de Android** y se instala directamente (`eas build -p android --profile preview` o compilado en local). Con Firebase las push funcionan gratis.
- En Expo Go no funcionan del todo, por eso hace falta el APK.
- iPhone queda fuera por ahora: las push en un iPhone real necesitan Apple Developer (99 €/año). En el simulador se pueden probar gratis.

## Orden de trabajo (acordado)

1. Recuperar la contraseña desde el login y obligar a cambiarla en el primer acceso.
2. Alta de cuentas por el instituto, con datos de identidad y fecha de nacimiento.
3. Doble validación mensual (empresa y profe) y bloqueo de las horas.
4. Inicio del profe (clase, inbox, pendientes, alumnos inactivos).
5. Notificaciones push.
6. Retirada de las prácticas.
