# 📋 Encargos sprint 3 (para pegar en OpenCode)

Volver a [[Tablero de tareas]] · Ver [[Flujo de ramas]] · [[Reparto por PCs]]

Cada PC copia **su** bloque entero y lo pega en OpenCode. OpenCode ya lee `AGENTS.md` del repo (arquitectura, carpetas permitidas y normas de ramas).

Antes de empezar, una sola vez y línea a línea (en PowerShell, sin `&&`):

```
git fetch origin --prune
git checkout develop
git pull
```

Si `git checkout develop` falla porque no existe en local: `git checkout -b develop --track origin/develop`.

---

## 📱 PC 2 · Pantallas

```
Eres PC 2 del proyecto Kampus. Lee AGENTS.md y respétalo: solo puedes tocar src/app/, src/ui/hooks/, src/ui/vistas/ y src/ui/utils/. Si necesitas cambiar un puerto, un caso de uso, container.ts o package.json, NO lo hagas: descríbelo en la PR.

Trabaja desde develop actualizado. Una rama y una PR contra develop por tarea, en este orden:

1. fix/pc2-tareas-fechas — Revisa las pantallas de tareas (src/ui/vistas/tareas.tsx) y fechas (src/ui/vistas/agenda.tsx) con los cinco roles de prueba (botones del login, contraseña kampus) en web y en móvil estrecho. Arregla lo que se vea mal o sea incómodo: espaciados, textos largos, botones pequeños, estados vacíos.

2. feature/pc2-ficha-dossier — Pantalla de solo lectura con la ficha del dossier: alumno, ciclo, centro, empresa, tutores, fechas, horas totales y la lista de actividades con las horas registradas en cada una. Usa container.dossiers.obtener(id) y los casos de uso de @/core/application. Se abre al tocar el alumno en Seguimiento (profe, instituto, Generalitat) y desde el panel del alumno.

Más adelante (no empezar hasta que PC 1 avise de que está en develop): formulario de crear/editar dossier e incidencias.

Antes de abrir cada PR: npm run lint, npm run typecheck, npm test y npm run format:check en verde. Commits con formato tipo(área): qué hace, en español.
```

---

## 🧩 PC 3 · Componentes, tema y datos de prueba

```
Eres PC 3 del proyecto Kampus. Lee AGENTS.md y respétalo: solo puedes tocar src/ui/components/, src/ui/theme/ y src/infrastructure/memory/. Si necesitas cambiar un puerto, un caso de uso, container.ts o package.json, NO lo hagas: descríbelo en la PR.

IMPORTANTE: tu rama antigua "botones" ya está en develop, pero los datos de prueba han cambiado (IDS_DEMO en src/infrastructure/memory/datos-demo.ts, cinco roles, dos centros). Empieza siempre desde develop actualizado y no reutilices ramas viejas.

Una rama y una PR contra develop por tarea, en este orden:

1. feature/pc3-iconos-pestanas — Iconos reales en la barra inferior (app-tabs.tsx y app-tabs.web.tsx): ahora Registrar y Perfil muestran un icono genérico. Iconos coherentes entre sí, con etiqueta accesible.

2. feature/pc3-pestana-centro — Mostrar la pestaña Centro también al rol generalitat (ahora solo al instituto).

3. feature/pc3-componentes-tareas — Componentes reutilizables: CasillaTarea (marcar hecha, 44 px mínimo, accesible), ChipTipoEvento (evento, entrega, reunion, festivo) e InsigniaVencida. Siguiendo el tema monocromo de theme.ts. Avisa en la PR para que PC 2 los use.

4. fix/pc3-teclado — En el componente Pantalla: keyboardShouldPersistTaps="handled" y keyboardDismissMode="on-drag".

5. fix/pc3-modo-oscuro — Repasa todas las pantallas en modo oscuro: contraste mínimo 4.5:1 y nada de colores escritos a mano fuera del tema.

Antes de abrir cada PR: npm run lint, npm run typecheck, npm test y npm run format:check en verde. Commits con formato tipo(área): qué hace, en español.
```

---

## 🎨 PC 4 · Diseño, web y QA

```
Eres PC 4 del proyecto Kampus. Lee AGENTS.md y respétalo: tu zona es e2e/, el diseño y la experiencia web. Si necesitas cambiar código de src/core, src/config, src/infrastructure o package.json, NO lo hagas: descríbelo en la PR. Si necesitas tocar src/ui/vistas, avisa antes a PC 2.

Trabaja desde develop actualizado. Una rama y una PR contra develop por tarea, en este orden:

1. test/pc4-e2e-flujos — Amplía los tests E2E con Playwright (contra npx expo start --web con backend memoria): login con cada uno de los cinco roles (alumno, empresa, profe, instituto, generalitat; contraseña kampus), el alumno registra un día, la empresa valora un mes, el instituto asigna un profe a un alumno desde Centro.

2. test/pc4-pantallas — Rehacer el test de pantallas con Jest que se apartó (está en el historial: commit "Rescata de pc1-correcciones-pantallas", archivo src/ui/__tests__/pantallas.test.tsx). Comprobaba que no se sobrescribe un día mientras carga otro mes y que los paneles recargan y muestran errores con reintento. Busca una forma menos frágil que simular React Native a mano.

3. feature/pc4-web-ancha — Que la web se vea bien en pantalla ancha (paneles de instituto y Generalitat, que se usarán desde ordenador): ancho máximo de contenido, columnas cuando quepan.

4. Figma (sin rama): diseño de las pantallas que faltan (ficha y formulario de dossier, incidencias, vista de la Generalitat) con el sistema de diseño monocromo, para que PC 2 tenga referencia.

Antes de abrir cada PR: npm run lint, npm run typecheck, npm test y npm run format:check en verde. Commits con formato tipo(área): qué hace, en español.
```
