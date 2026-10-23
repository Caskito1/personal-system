# AppFinanciera — Documento de coordinación

Documento de coordinación de `personal-system` para el proyecto AppFinanciera: qué conoce y cómo coordina el Organizador. Contiene principios, roadmap, decisiones funcionales cerradas, estado y próximas acciones. **No es el lugar del conocimiento técnico de la aplicación**: ese vive en el repo de AppFinanciera (ver `opencode-AppFinanciera/docs/handoffs/HANDOFF-ETAPA-0-MAPA-CONTEXTO.md`).

## Principio arquitectónico

> **El Organizador planifica y coordina. El OpenCode de cada proyecto conserva y utiliza el conocimiento técnico necesario para ejecutar autónomamente esas planificaciones.**

`personal-system` no debe convertirse en el repositorio del conocimiento técnico de AppFinanciera.

**El Organizador conoce:** objetivos; prioridades; decisiones; roadmap; estado de cada proyecto; qué debe hacerse; qué resultado se espera; restricciones y criterios importantes.

**El repo de AppFinanciera conserva:** conocimiento técnico; arquitectura; funcionamiento real; modelo de dominio; estructura de datos; convenciones; agentes; reglas de trabajo; contexto específico de la aplicación; decisiones técnicas relevantes.

La intención es poder enviar a futuro HANDOFFs relativamente concisos al OpenCode de AppFinanciera y que este trabaje sin que vuelvan a explicarle toda la aplicación (resultado que construye la **Etapa 0**).

## Estado del documento

- **Auditoría inicial: completada** (previa al esquema de etapas 0–4). Read-only, `REPORT-02.md` en el repo de AppFinanciera. Base de partida, no verdad absoluta.
- **Etapa 0 (Relevamiento + construcción del contexto interno): COMPLETADA.** Contexto y agentes de Etapa 0 commiteados en `opencode-AppFinanciera` (commit `d0c6fec`), con `REPORT-ETAPA-0.md` incluido (no se copia a `personal-system`); commits commiteados y pusheados (verificado 23/09).
  - `opencode-AppFinanciera/docs/handoffs/HANDOFF-ETAPA-0-MAPA-CONTEXTO.md` aprobado y entregado: commiteado en el repo `opencode-AppFinanciera`.
  - Etapa 0 cerrada.
- **Etapa 1 (Base estructural): CERRADA (25/09/2026).** Commit `78e1461` en el repo `opencode-AppFinanciera`. Entregables: `opencode-AppFinanciera/docs/handoffs/HANDOFF-ETAPA-1-BASE-ESTRUCTURAL.md` y `opencode-AppFinanciera/docs/propuestas/PROPUESTA-ETAPA-1.md`. Etapa de diseño/estructura (NO implementa funcionalidades).
- **Etapa 2 (Correcciones y limpieza): CERRADA (11/10/2026).** 9/9 subetapas cerradas. Estructura de subetapas aprobada en `opencode-AppFinanciera/docs/handoffs/HANDOFF-ETAPA-2.md`:
  - **2.1 — Taxonomía de gastos fijos unificada + `Otros`: CERRADA (25/09/2026).** Commit de producción `b46b570`; validada en Local (build + 27 invariantes), Staging y Producción. Sin cambios en Firestore.
  - **2.2 — Totales del mes con gastos fijos: CERRADA (30/09/2026).** Commit `119cc4a`; Local (build + fixtures 24/24) y Producción PASS (cuenta real).
  - **2.3 — Ingresos (labels de bandas + sección `Otros`): CERRADA (30/09/2026).** Commit `7d71fb5`; gate read-only PASS, Local 8/8, Staging PASS y Producción PASS (cuenta real, solo lectura, 0 escrituras).
  - **2.8 — Header `Personal` / `Total registrado` en `/gastos-fijos`: CERRADA (30/09/2026).** Commit `66ba009`; verificada en Producción.
  - **2.9 — Totales del header acotados al período visible: CERRADA (06/10/2026).** Commit `bfbdda4`; gate read-only PASS (P1–P6) y runtime 17/17; verificada en Producción por el usuario.
  - **2.7 — Guard de integridad `groupId` en el alta de compartidos: CERRADA (08/10/2026).** Commit `96934c0`; gate Firestore PASS (41 entries, 0 corruptos) y harness 20/20; verificada en Producción por el usuario.
  - **2.4 — Robustez de sesión/redirección: CERRADA (10/10/2026).** Commit `1716a19`; verificada en Producción.
  - **2.5 — Retiro del flujo legacy de gastos fijos: CERRADA (11/10/2026).** Commit `3216095`; bloque de Transferencias intacto; verificada en Producción.
  - **2.6 — Limpieza de código muerto: CERRADA (11/10/2026).** Commit `10ab576`; transferencias excluida del alcance (conservados `Transferenciassections.jsx`, `gastosCalculations.js` y `origenCompra` para el diseño de la Etapa 3); verificada en Producción.
- **Etapa 3 (diseño): CERRADA (15/10/2026).** `PROPUESTA-ETAPA-3.md` aprobada por el usuario en la conversación de cierre (commiteada en `opencode-AppFinanciera`, `e665e3d`); decisiones PO-1…PO-8 y DC-1…DC-8 incorporadas. Los pendientes técnicos P-1…P-9 se abordan subetapa por subetapa durante la Etapa 4 (p. ej. P-2 en 4.0/D-6) y los vacíos de PO-4 (§12.6) quedaron resueltos en `PROPUESTA-ETAPA-4.md` §11 (17/10/2026). **Etapa 4 (implementación de Reintegros): EN CURSO** — Rondas 1 y 2 aprobadas por el usuario (15/10/2026, ver «Etapa 4 — decisiones de las Rondas 1 y 2»); `HANDOFF-ETAPA-4.md` **entregado** en el repo (`5ca4e35`, 15/10); `PROPUESTA-ETAPA-4.md` (**plan técnico; nombre ordenado por el usuario**, producido el 15/10, `294bab9`) **aprobada el 16/10/2026** (`e57f6f0`) y **enmendada el 17/10/2026** (`0ed53ab`: subetapa 4.6 eliminada, secuencia hasta 4.5, sin confirmación bilateral). Subetapas **4.0–4.3 implementadas** en rama `staging` con sus EVIDENCIA (4.3 cerrada 21–22/10, `EVIDENCIA-4.3`); **sigue 4.3-bis** (eliminar/condonar). Sin promoción a `main` ni despliegue a Producción (pendiente de aprobación del usuario).
- Regla de flujo: **LEER → ANALIZAR → PROPONER → USUARIO DECIDE → PLANIFICAR → USUARIO APRUEBA → EJECUTAR**.
- Regla permanente de despliegue (cuando haya implementación): **Local → Staging → Producción → Verificación**. Nunca asumir terminado solo porque funciona localmente; verificar tras producción; no modificar producción directamente.
- Relación con el Organizador: AppFinanciera es un proyecto separado. El Organizador coordina, prioriza, analiza, propone, registra decisiones y controla estado. El OpenCode de AppFinanciera ejecuta y trabaja sobre su repo. El cierre de Finanzas del Organizador **no implica terminar AppFinanciera como producto**.

### Etapa 4 — decisiones de las Rondas 1 y 2 (aprobadas 15/10/2026)

No reabrir. Detalle y límites exactos en `opencode-AppFinanciera/docs/handoffs/HANDOFF-ETAPA-4.md`; son la base de ese handoff.

**Ronda 1 — estructura y flujo:**

1. **Orden y alcance de subetapas:** `4.0 → 4.1 → 4.2 → 4.3 → 4.4 → 4.5`, con **4.5 (retiro de Transferencias) al final del núcleo**. Incluidas **4.3-bis (eliminar/condonar)** y **4.4-bis (bitácora)**, con detalles y criterios a definir y aprobar en sus subetapas correspondientes. **4.6 original fuera del alcance inicial**: BottomNav y vinculación de gastos quedan pendientes de planificación futura; esto **no revoca** PO-4 ni ninguna decisión funcional ya tomada. (La 4.6 volvió en la Ronda 2 vía D-11a/D-11b y fue **eliminada el 17/10/2026** por decisión del usuario; PO-4 quedó sin objeto con esa misma decisión — ver fila 4 y «Secuencia aprobada».)
2. **Herramientas de pruebas:** autorizadas **solo para análisis y propuesta** — sin instalar dependencias, modificar `package.json` ni ejecutar cambios en Firebase. La propuesta debe explicar qué se instalaría, para qué se usaría, su mantenimiento y cómo se garantizaría que las pruebas **no escriban en la base de datos compartida con Producción**.
3. **Flujo de planificación:** (1) Personal System (Organizador) coordina las decisiones y prepara `HANDOFF-ETAPA-4.md`; (2) el handoff se entrega al OpenCode de AppFinanciera; (3) ese OpenCode analiza el handoff contra el diseño aprobado y el código existente, identifica inconsistencias y prepara el **plan técnico detallado** (no implementa todavía); (4) revisión conjunta del plan y resolución de discrepancias; (5) el usuario **autoriza explícitamente** el plan de la subetapa 4.0; (6) solo entonces comienza la implementación autorizada, con Local → Staging → Producción y sus aprobaciones. El Organizador controla los estados y registra las decisiones; el OpenCode de AppFinanciera analiza y ejecuta el trabajo técnico autorizado.
4. **Confirmación bilateral (PO-4):** definida en la Ronda 2 (D-11a/D-11b); **sin objeto desde el 17/10/2026**: el usuario decidió **sin confirmación bilateral**, se eliminó la subetapa 4.6 y los vacíos de PO-4 quedaron resueltos en `PROPUESTA-ETAPA-4.md` §11; sin reabrir las decisiones funcionales ya confirmadas.

**Ronda 2 — decisiones técnicas de principio (resumen; sin reimplementar aquí):** **D-1** herramientas (emulador + `@firebase/rules-unit-testing` + un runner, sin instalar) · **D-2** criterios del gate §8.5 como objetivo, con revisión de reglas exactas en el plan · **D-3** bitácora `reintegros/{id}/eventos` create-only · **D-4** constancias en objetos embebidos (B) · **D-5** campo ausente = activo · **D-6** principio de atomicidad (el plan **debe demostrar** `devuelto == Σ entregas no eliminadas`; no asumir que la transacción sola basta) · **D-7** prueba automatizada de reconciliación como done de 4.1/4.3 · **D-8** matriz **E1 + C1 + (ii)** · **D-9** congelaciones con caso abierto resuelto: **opción B elegida (16/10/2026)** para «pago posterior a condonación» · **D-10** acción «Condonar» + estado **«Condonada»** · **D-11a** subetapa **4.6 Confirmación bilateral posterior a 4.5** (amplía el alcance; PO-4 decidida para v1) · **D-11b** guardrails: contraparte la ve pendiente de confirmación, sin entregas antes de confirmar, registrador edita/elimina libremente antes (después rige la matriz). **D-11a/D-11b y PO-4: sin objeto desde el 17/10/2026** (eliminación de la confirmación bilateral, ver «Secuencia aprobada»).

**Secuencia aprobada (enmienda 17/10/2026):** `4.0 → 4.1 → 4.2 → 4.3 → 4.3-bis → 4.4 → 4.4-bis → 4.5` — **4.6 eliminada** (decisión del usuario; sin renumeración de las subetapas). El plan técnico puede justificar reordenamiento con aprobación; nunca modificar el alcance en silencio.

**Estado (23/10/2026):** Ronda 1–2 aprobadas (15/10); `HANDOFF-ETAPA-4.md` **entregado** en el repo (`5ca4e35`, 15/10); `PROPUESTA-ETAPA-4.md` **aprobada 16/10/2026** (`e57f6f0`) y **enmendada 17/10/2026** (`0ed53ab`); subetapas **4.0–4.3 implementadas** en `staging` con sus EVIDENCIA (`EVIDENCIA-4.0` · `4.1` · `4.2` · `4.3` en `docs/evidencia/`; 4.3a `7d41d39`, 4.3b cerrada 21/10, 4.3c cerrada 22/10, gates en verde 22/10). **Siguiente subetapa: 4.3-bis** (eliminar/condonar). Pendiente de aprobación del usuario: promoción `staging → main` y despliegue de reglas a Producción; H-e sigue abierto.

## Roadmap

### Etapa 0 — Relevamiento + construcción del contexto interno

Objetivo: comprender completamente AppFinanciera y convertir ese conocimiento en un sistema de contexto persistente dentro del propio repo de AppFinanciera. No es solamente producir un mapa: debe dejar preparada la aplicación para que su propio OpenCode pueda trabajar autónomamente en futuras etapas.

Dos resultados:

- **Resultado A — Conocimiento:** descubrir cómo funciona realmente la aplicación.
- **Resultado B — Sistema de contexto:** convertir ese conocimiento en documentación y configuración persistente dentro del repo (`context/`, `AGENTS.md` actualizado, agentes especializados, `ROADMAP.md`).

Cadena conceptual: `Código existente → Relevamiento → Contexto técnico + funcional → AGENTS.md actualizado → Agentes especializados → OpenCode autónomo`.

### Etapa 1 — Base estructural

Con la evidencia de la Etapa 0: modelo de gastos; gastos compartidos; gastos fijos; balances; preparación para porcentajes configurables; relaciones usuarios/grupos; modelo de recuperaciones/reintegros; compatibilidad futura con tarjeta; otras decisiones estructurales necesarias. **No asumir soluciones antes del relevamiento.**

### Etapa 2 — Correcciones y limpieza

Solo aquello que la Etapa 0 justifique: código obsoleto; transferencias antiguas; código muerto; bugs; taxonomías; `Otros`; robustez; schemas/types; inconsistencias; otras mejoras concretas.

**Estado real (verificado en el repo `opencode-AppFinanciera`):** no se implementa como un bloque grande, sino en subetapas pequeñas, independientes y verificables, con el flujo Local → Staging → Producción → Verificación. Estructura aprobada en `opencode-AppFinanciera/docs/handoffs/HANDOFF-ETAPA-2.md`: 2.1 (taxonomía de fijos + `Otros`), 2.2 (totales del mes con gastos fijos), 2.3 (ids de bandas + sección `Otros` de ingresos), 2.4 (robustez de sesión/redirección), 2.5 (retirar flujo legacy de gastos fijos), 2.6 (limpieza de código muerto); además existen **2.7 (guard de integridad `groupId`) y 2.8 (header `Personal` / `Total registrado` en `/gastos-fijos`)**, surgidas de la validación runtime de 2.2, y **2.9 (totales del header acotados al período visible)**, surgida de una discrepancia detectada después de 2.8. Las transferencias quedan para la Etapa 3.

- **2.1 CERRADA (25/09/2026)**, commit de producción `b46b570`; sin cambios en Firestore.
- **2.2 CERRADA (30/09/2026)**, commit `119cc4a`. Regla aplicada: los totales de `/gastos` incluyen solo gastos fijos **efectivamente pagados** (`esPagado = !!paidByUid || (pagoHasta > periodo)`, no `estado`); *pagado* ≠ *saldado*, y liquidar un saldo no altera los totales. Gate histórico read-only PASS (34 entries, 0 inconsistentes); prueba runtime en sandbox 6/6 PASS con limpieza verificada. No tocó históricos ni estructura de datos.
- **2.3 CERRADA (30/09/2026)**, commit `7d71fb5`; gate read-only PASS (`idsLegacy` = 0), 8/8 en Local, Staging y Producción (solo lectura, 0 escrituras).
- **2.8 CERRADA (30/09/2026)**, commit `66ba009`; bloque `Personal` con `Personal` (cubierto) y `Total registrado`, verificado en Producción.
- **2.9 CERRADA (06/10/2026)**, commit `bfbdda4`: `totalPersonal` (`Total registrado`) y `totalPersonalCubierto` (`Personal`) solo suman entries reales del período visible (`esDelPeriodo = !!g.entry && g.entry.periodo === periodo`); el efecto 4 (`pagoHasta > periodo`) y `esPagado` quedaron intactos. Gate read-only PASS (P1–P6) y runtime 17/17. Verificada en Producción por el usuario.
- **2.7 CERRADA (08/10/2026)**, commit `96934c0`: guard en `registrarGasto` que lanza si `esCompartido && !grupo?.id`, `groupId` agregado al `updateDoc` de re-registro y `PagarModal` con `try/catch/finally` que muestra el error sin cerrar el modal. Gate Firestore PASS (41 entries, 0 corruptos) y harness 20/20. Verificada en Producción por el usuario. Promovida con push directo previo a la adopción del flujo permanente de ramas del proyecto.
- **2.4 CERRADA (10/10/2026)**, commit `1716a19`: robustez de sesión/redirección en `lib/AuthContext.jsx`; primer cierre con el flujo de ramas completo; verificada en Producción por el usuario.
- **2.5 CERRADA (11/10/2026)**, commit `3216095`: retiro del flujo legacy de gastos fijos (−705 líneas); bloque de Transferencias intacto; flujo completo Local → Staging → Producción; verificada en Producción por el usuario.
- **2.6 CERRADA (11/10/2026)**, commit `10ab576`: limpieza de código muerto (−330 líneas); transferencias excluida del alcance; conservados `gastosCalculations.js` (balances de transferencias), `origenCompra` y `Transferenciassections.jsx` como base para el diseño de la Etapa 3; verificada en Producción por el usuario.
- **Etapa 2 COMPLETAMENTE CERRADA (9/9 subetapas, 11/10/2026).**

### Etapa 3 — Nuevas funcionalidades financieras

Principalmente: dinero a recuperar; reintegros; adelantos; liquidación de saldos; personas externas; integración futura con tarjeta.

**Regla fundamental: reintegro/recuperación ≠ ingreso.**

### Etapa 4 — Evolución general del producto

Futuro: múltiples grupos; configuración por grupo; porcentajes configurables; configuración general; módulo de tarjeta; estadísticas; productos; UX; aplicación para terceros; otras funcionalidades de producto. Solo anticipar en etapas anteriores aquello que tenga una implicación estructural real.

**Nota de numeración (19/10/2026):** los documentos de trabajo de la Etapa 4 en curso (`HANDOFF-ETAPA-4.md`, `PROPUESTA-ETAPA-4.md`) corresponden a la **implementación de Reintegros** (ver «Estado del documento» y «Etapa 4 — decisiones de las Rondas 1 y 2»); este alcance de evolución general queda como trabajo futuro, no aprobado (backlog en el `ROADMAP.md` del repo).

## Decisiones funcionales ya cerradas

> No volver a plantear como preguntas pendientes. Si el código real no coincide, primero se documenta la inconsistencia; no se corrige automáticamente.

### `/gastos`

Conservar el comportamiento actual como referencia deseada:

`total mensual = gastos personales + parte del usuario de gastos compartidos diarios + 50% de gastos fijos compartidos + 100% de gastos fijos personales`

- `/gastos` = visualización general.
- `/gastos-fijos` = administrador/detalle de gastos fijos.
- Si el código real no coincide, el hallazgo se documenta como inconsistencia (no se "arregla").

### Gastos compartidos diarios

Compartidos a nivel de registro/visualización, pero **no generan deuda ni balance**. Intencional para el uso actual. **No convertir retroactivamente** esos gastos en deudas.

### Gastos fijos compartidos

Sí generan balance entre participantes. El balance puede acumularse y posteriormente liquidarse. Cuando se liquida, el balance vuelve a cero, pero **el historial permanece**. Diferencia conceptual que debe existir: **histórico de lo ocurrido** vs **balance actualmente pendiente**.

### Recuperaciones

Representan **dinero adelantado que está pendiente de recuperar**. Pueden involucrar: pareja; miembro del grupo; amigo; familiar; persona externa.

El dinero recibido para cancelar esa deuda: reduce/cancela el saldo; **no es ingreso real**.

### Tarjeta

Será un **módulo futuro propio** (no necesariamente con integración bancaria). El modelo actual de recuperaciones debería diseñarse de manera que pueda utilizarse posteriormente desde ese módulo.

### `Otros`

Debe seguir existiendo y funcionar. No es prioridad actual.

### Firestore

Se permite utilizar Firestore **exclusivamente en lectura** si posteriormente se demuestra que aporta evidencia necesaria. Por ahora, **no otorgar acceso adicional ni modificar datos**.

### Datos históricos

No eliminar, migrar, normalizar ni modificar datos durante la Etapa 0. Las decisiones sobre datos históricos se tomarán después de contar con evidencia.

## Registro de sesión (para el panel)

- **Estado del proyecto:** Activo.
- **Auditoría inicial:** completada (`REPORT-02.md`, read-only; previa al esquema 0–4).
- **Etapa 0 (Relevamiento + contexto):** completada (contexto y agentes commiteados, `d0c6fec`, con `REPORT-ETAPA-0.md`; pusheados, verificado 23/09). `opencode-AppFinanciera/docs/handoffs/HANDOFF-ETAPA-0-MAPA-CONTEXTO.md` aprobado y entregado (commiteado en `opencode-AppFinanciera`, 22–23/09).
- **Etapa 1 (Base estructural):** **CERRADA (25/09/2026)**, commit `78e1461`. Entregables: `opencode-AppFinanciera/docs/handoffs/HANDOFF-ETAPA-1-BASE-ESTRUCTURAL.md` y `opencode-AppFinanciera/docs/propuestas/PROPUESTA-ETAPA-1.md`.
- **Etapa 2 (Correcciones y limpieza):** **CERRADA (11/10/2026), 9/9 subetapas**. 2.1 CERRADA (25/09/2026, `b46b570`); **2.2, 2.3 y 2.8 CERRADAS (30/09/2026)** (`119cc4a` · `7d71fb5` · `66ba009`, Producción PASS con cuenta real); **2.9 CERRADA (06/10/2026, `bfbdda4`)** y **2.7 CERRADA (08/10/2026, `96934c0`)**; **2.4 CERRADA (10/10/2026, `1716a19`)**; **2.5 CERRADA (11/10/2026, `3216095`)** y **2.6 CERRADA (11/10/2026, `10ab576`)**, ambas verificadas en Producción. Ambientes alineados: `main` == `staging` == Producción == `10ab576` (11/10/2026).
- **Etapa 3 (diseño): CERRADA (15/10/2026).** `HANDOFF-ETAPA-3.md` entregado (`405a11c`) y `PROPUESTA-ETAPA-3.md` producida y commiteada (`e665e3d`, 14/10/2026), **aprobada por el usuario** en la conversación de cierre (15/10/2026): el diseño queda como base autorizada para planificar la Etapa 4. Decisiones PO-1…PO-8 y DC-1…DC-8 incorporadas. Los pendientes técnicos P-1…P-9 se abordan subetapa por subetapa durante la Etapa 4 (p. ej. P-2 en 4.0/D-6) y los vacíos de PO-4 (§12.6) quedaron resueltos en la propuesta (§11, 17/10). **Etapa 4:** **EN CURSO (implementación en `staging`)** — **Ronda 1–2 aprobadas (15/10/2026)**: estructura (orden 4.0→4.5, bis incluidas; herramientas solo propuesta; flujo de 6 pasos) + decisiones técnicas D-1…D-11, con **D-9 resuelto (opción B, 16/10)** y **D-11a/D-11b/PO-4 sin objeto (17/10: sin confirmación bilateral)**. `HANDOFF-ETAPA-4.md` **entregado** (`5ca4e35`, 15/10); `PROPUESTA-ETAPA-4.md` (**plan técnico, nombre ordenado por el usuario**) **aprobada 16/10** (`e57f6f0`) y **enmendada 17/10** (`0ed53ab`: 4.6 eliminada, secuencia hasta 4.5). **Implementación hasta ahora (rama `staging`):** 4.0 gate Firestore (`ff47291`·`63666f6`, suite 25/25), 4.1 modelo y servicios (`2404140`·`6519dda`), 4.2 alta de reintegros (`74b9203`·`632dd65`, aprobada 17/10, `EVIDENCIA-4.2`), lote de reglas (`5264d2e`·`41f8cb8`) y **4.3 acciones de pago/edición** (4.3a `7d41d39`; 4.3b 21/10; 4.3c 22/10; gates en verde 22/10, `EVIDENCIA-4.3`). **Sin promoción a `main` y sin deploy de reglas a Producción** (requieren aprobación explícita del usuario).
- **Acceso Firestore:** read-only aprobado por el usuario; sin escrituras, migraciones, índices ni cambios de reglas. La Etapa 2.1 no modificó Firestore.
- **Próxima acción:** **Etapa 4 — implementación (en curso, rama `staging`):** (a) subetapa **4.3-bis** (eliminar/condonar en `/reintegros`; 4.3 cerrada 22/10, `EVIDENCIA-4.3`); (b) resolver **H-e** (obligación impuesta a un tercero sin veto ni aviso) antes de abrir la app al público; (c) al cierre de la etapa, promoción `staging → main` y despliegue de reglas con la checklist de ventana y aprobación explícita del usuario; (d) detalles de estilo de `/reintegros` y del modal pendientes de que el usuario los detalle. Cada subetapa y todo despliegue **requieren aprobación explícita del usuario por separado**; ninguna aprobación parcial autoriza por sí sola código, Firestore, dependencias, commits, push ni despliegues.
- **Sesión de origen:** 21/09/2026 (redefinición de la Etapa 0, nuevo esquema de etapas 0–4 y decisiones funcionales cerradas).