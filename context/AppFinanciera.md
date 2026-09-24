# AppFinanciera — Documento de coordinación

Documento de coordinación de `personal-system` para el proyecto AppFinanciera: qué conoce y cómo coordina el Organizador. Contiene principios, roadmap, decisiones funcionales cerradas, estado y próximas acciones. **No es el lugar del conocimiento técnico de la aplicación**: ese vive en el repo de AppFinanciera (ver `HANDOFF-ETAPA-0-MAPA-CONTEXTO.md`).

## Principio arquitectónico

> **El Organizador planifica y coordina. El OpenCode de cada proyecto conserva y utiliza el conocimiento técnico necesario para ejecutar autónomamente esas planificaciones.**

`personal-system` no debe convertirse en el repositorio del conocimiento técnico de AppFinanciera.

**El Organizador conoce:** objetivos; prioridades; decisiones; roadmap; estado de cada proyecto; qué debe hacerse; qué resultado se espera; restricciones y criterios importantes.

**El repo de AppFinanciera conserva:** conocimiento técnico; arquitectura; funcionamiento real; modelo de dominio; estructura de datos; convenciones; agentes; reglas de trabajo; contexto específico de la aplicación; decisiones técnicas relevantes.

La intención es poder enviar a futuro HANDOFFs relativamente concisos al OpenCode de AppFinanciera y que este trabaje sin que vuelvan a explicarle toda la aplicación (resultado que construye la **Etapa 0**).

## Estado del documento

- **Etapa 2 (Auditoría): completada.** Read-only, `REPORT-02.md` en el repo de AppFinanciera. Base de partida, no verdad absoluta.
- **Etapa 0 (Relevamiento + construcción del contexto interno): COMPLETADA.** Contexto y agentes de Etapa 0 commiteados en `opencode-AppFinanciera` (commit `d0c6fec`), con `REPORT-ETAPA-0.md` incluido (no se copia a `personal-system`); commits commiteados y pusheados (verificado 23/09).
  - `HANDOFF-ETAPA-0-MAPA-CONTEXTO.md` aprobado y entregado: commiteado en el repo `opencode-AppFinanciera`.
  - Etapa 0 cerrada; no avanzar a la Etapa 1 sin decisión.
- **Etapas 1–4: NO iniciadas.** Solo se definen aquí su alcance (sección Roadmap).
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
- **Etapa 2 (Auditoría):** completada (`REPORT-02.md`, read-only).
- **Etapa 0 (Relevamiento + contexto):** completada (contexto y agentes commiteados, `d0c6fec`, con `REPORT-ETAPA-0.md`; pusheados, verificado 23/09). `HANDOFF-ETAPA-0-MAPA-CONTEXTO.md` aprobado y entregado (commiteado en `opencode-AppFinanciera`, 22–23/09).
- **Etapas 1–4:** no iniciadas.
- **Próxima acción:** Etapa 1 (Base estructural) — pendiente de decisión; no iniciar.
- **Sesión de origen:** 21/09/2026 (redefinición de la Etapa 0, nuevo esquema de etapas 0–4 y decisiones funcionales cerradas).