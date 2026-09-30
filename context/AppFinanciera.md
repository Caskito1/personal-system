# AppFinanciera — Documento de coordinación

Documento de coordinación de `personal-system` para el proyecto AppFinanciera: qué conoce y cómo coordina el Organizador. Contiene principios, roadmap, decisiones funcionales cerradas, estado y próximas acciones. **No es el lugar del conocimiento técnico de la aplicación**: ese vive en el repo de AppFinanciera (ver `opencode-AppFinanciera/HANDOFF-ETAPA-0-MAPA-CONTEXTO.md`).

## Principio arquitectónico

> **El Organizador planifica y coordina. El OpenCode de cada proyecto conserva y utiliza el conocimiento técnico necesario para ejecutar autónomamente esas planificaciones.**

`personal-system` no debe convertirse en el repositorio del conocimiento técnico de AppFinanciera.

**El Organizador conoce:** objetivos; prioridades; decisiones; roadmap; estado de cada proyecto; qué debe hacerse; qué resultado se espera; restricciones y criterios importantes.

**El repo de AppFinanciera conserva:** conocimiento técnico; arquitectura; funcionamiento real; modelo de dominio; estructura de datos; convenciones; agentes; reglas de trabajo; contexto específico de la aplicación; decisiones técnicas relevantes.

La intención es poder enviar a futuro HANDOFFs relativamente concisos al OpenCode de AppFinanciera y que este trabaje sin que vuelvan a explicarle toda la aplicación (resultado que construye la **Etapa 0**).

## Estado del documento

- **Auditoría inicial: completada** (previa al esquema de etapas 0–4). Read-only, `REPORT-02.md` en el repo de AppFinanciera. Base de partida, no verdad absoluta.
- **Etapa 0 (Relevamiento + construcción del contexto interno): COMPLETADA.** Contexto y agentes de Etapa 0 commiteados en `opencode-AppFinanciera` (commit `d0c6fec`), con `REPORT-ETAPA-0.md` incluido (no se copia a `personal-system`); commits commiteados y pusheados (verificado 23/09).
  - `opencode-AppFinanciera/HANDOFF-ETAPA-0-MAPA-CONTEXTO.md` aprobado y entregado: commiteado en el repo `opencode-AppFinanciera`.
  - Etapa 0 cerrada.
- **Etapa 1 (Base estructural): CERRADA (25/09/2026).** Commit `78e1461` en el repo `opencode-AppFinanciera`. Entregables: `opencode-AppFinanciera/HANDOFF-ETAPA-1-BASE-ESTRUCTURAL.md` y `opencode-AppFinanciera/PROPUESTA-ETAPA-1.md`. Etapa de diseño/estructura (NO implementa funcionalidades).
- **Etapa 2 (Correcciones y limpieza): EN CURSO.** Estructura de subetapas aprobada en `opencode-AppFinanciera/HANDOFF-ETAPA-2.md`:
  - **2.1 — Taxonomía de gastos fijos unificada + `Otros`: CERRADA (25/09/2026).** Commit de producción `b46b570`; validada en Local (build + 27 invariantes), Staging y Producción. Sin cambios en Firestore.
  - **2.2 — Totales del mes con gastos fijos: CERRADA (30/09/2026).** Commit `119cc4a`; Local (build + fixtures 24/24) y Producción PASS (cuenta real).
  - **2.3 — Ingresos (labels de bandas + sección `Otros`): CERRADA (30/09/2026).** Commit `7d71fb5`; gate read-only PASS, Local 8/8, Staging PASS y Producción PASS (cuenta real, solo lectura, 0 escrituras).
  - **2.8 — Header `Personal` / `Total registrado` en `/gastos-fijos`: CERRADA (30/09/2026).** Commit `66ba009`; verificada en Producción.
  - **2.4 · 2.5 · 2.6: sin empezar.**
  - **2.7 — Guard de integridad `groupId` en el alta de compartidos: NO implementada, requiere aprobación propia** (surgió de la validación runtime de 2.2).
- **Etapas 3–4: NO iniciadas.** Solo se definen aquí su alcance (sección Roadmap).
- Regla de flujo: **LEER → ANALIZAR → PROPONER → USUARIO DECIDE → PLANIFICAR → USUARIO APRUEBA → EJECUTAR**.
- Regla permanente de despliegue (cuando haya implementación): **Local → Staging → Producción → Verificación**. Nunca asumir terminado solo porque funciona localmente; verificar tras producción; no modificar producción directamente.
- Relación con el Organizador: AppFinanciera es un proyecto separado. El Organizador coordina, prioriza, analiza, propone, registra decisiones y controla estado. El OpenCode de AppFinanciera ejecuta y trabaja sobre su repo. El cierre de Finanzas del Organizador **no implica terminar AppFinanciera como producto**.

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

**Estado real (verificado en el repo `opencode-AppFinanciera`):** no se implementa como un bloque grande, sino en subetapas pequeñas, independientes y verificables, con el flujo Local → Staging → Producción → Verificación. Estructura aprobada en `opencode-AppFinanciera/HANDOFF-ETAPA-2.md`: 2.1 (taxonomía de fijos + `Otros`), 2.2 (totales del mes con gastos fijos), 2.3 (ids de bandas + sección `Otros` de ingresos), 2.4 (robustez de sesión/redirección), 2.5 (retirar flujo legacy de gastos fijos), 2.6 (limpieza de código muerto); además existen **2.7 (guard de integridad `groupId`) y 2.8 (header `Personal` / `Total registrado` en `/gastos-fijos`)**, surgidas de la validación runtime de 2.2. Las transferencias quedan para la Etapa 3.

- **2.1 CERRADA (25/09/2026)**, commit de producción `b46b570`; sin cambios en Firestore.
- **2.2 CERRADA (30/09/2026)**, commit `119cc4a`. Regla aplicada: los totales de `/gastos` incluyen solo gastos fijos **efectivamente pagados** (`esPagado = !!paidByUid || (pagoHasta > periodo)`, no `estado`); *pagado* ≠ *saldado*, y liquidar un saldo no altera los totales. Gate histórico read-only PASS (34 entries, 0 inconsistentes); prueba runtime en sandbox 6/6 PASS con limpieza verificada. No tocó históricos ni estructura de datos.
- **2.3 CERRADA (30/09/2026)**, commit `7d71fb5`; gate read-only PASS (`idsLegacy` = 0), 8/8 en Local, Staging y Producción (solo lectura, 0 escrituras).
- **2.8 CERRADA (30/09/2026)**, commit `66ba009`; bloque `Personal` con `Personal` (cubierto) y `Total registrado`, verificado en Producción.
- **2.4 · 2.5 · 2.6 sin empezar.** **2.7 (guard `groupId`) NO implementada**, requiere aprobación propia.

### Etapa 3 — Nuevas funcionalidades financieras

Principalmente: dinero a recuperar; reintegros; adelantos; liquidación de saldos; personas externas; integración futura con tarjeta.

**Regla fundamental: reintegro/recuperación ≠ ingreso.**

### Etapa 4 — Evolución general del producto

Futuro: múltiples grupos; configuración por grupo; porcentajes configurables; configuración general; módulo de tarjeta; estadísticas; productos; UX; aplicación para terceros; otras funcionalidades de producto. Solo anticipar en etapas anteriores aquello que tenga una implicación estructural real.

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
- **Etapa 0 (Relevamiento + contexto):** completada (contexto y agentes commiteados, `d0c6fec`, con `REPORT-ETAPA-0.md`; pusheados, verificado 23/09). `opencode-AppFinanciera/HANDOFF-ETAPA-0-MAPA-CONTEXTO.md` aprobado y entregado (commiteado en `opencode-AppFinanciera`, 22–23/09).
- **Etapa 1 (Base estructural):** **CERRADA (25/09/2026)**, commit `78e1461`. Entregables: `opencode-AppFinanciera/HANDOFF-ETAPA-1-BASE-ESTRUCTURAL.md` y `opencode-AppFinanciera/PROPUESTA-ETAPA-1.md`.
- **Etapa 2 (Correcciones y limpieza):** **en curso**. 2.1 CERRADA (25/09/2026, `b46b570`); **2.2, 2.3 y 2.8 CERRADAS (30/09/2026)** (`119cc4a` · `7d71fb5` · `66ba009`, Producción PASS con cuenta real); 2.4 · 2.5 · 2.6 sin empezar; **2.7 (guard `groupId`) NO implementada, requiere aprobación propia**. Ambientes alineados en el repo (rama `master`).
- **Etapas 3–4:** no iniciadas.
- **Acceso Firestore:** read-only aprobado por el usuario; sin escrituras, migraciones, índices ni cambios de reglas. La Etapa 2.1 no modificó Firestore.
- **Próxima acción:** planificar la siguiente subetapa disponible de la Etapa 2 (2.4 robustez de sesión/redirección, 2.5 retirar flujo legacy, 2.6 limpieza de código muerto, o 2.7 guard `groupId`), cada una con su propia planificación y aprobación antes de implementar.
- **Sesión de origen:** 21/09/2026 (redefinición de la Etapa 0, nuevo esquema de etapas 0–4 y decisiones funcionales cerradas).