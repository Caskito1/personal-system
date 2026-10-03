# Contexto - Finanzas

## Propósito

Área de organización financiera personal. Principio: **OBSIDIAN FINANZAS = pensar, decidir, proyectar y revisar**. No se convierte en una segunda aplicación financiera: es un sistema estratégico y de seguimiento.

## Fuentes y responsabilidades

- **AppFinanciera** → registro operativo diario (ingresos, gastos, gastos compartidos, gastos fijos, tarjeta, préstamos, etc.).
- **Gletir** → ejecución y custodia de inversiones.
- **Excel** → detalle auxiliar mientras AppFinanciera no integre todas las funcionalidades.
- **Obsidian (04-Finanzas)** → estrategia, objetivos, resumen mensual, evolución y decisiones.
- **Planner** → transforma acciones financieras relevantes en acciones planificables.

## No duplicar en Obsidian

Obsidian NO registra:

- movimientos individuales;
- gastos detallados;
- operaciones diarias;
- saldos en tiempo real.

Los resúmenes mensuales utilizan datos provenientes de AppFinanciera/Excel, pero Obsidian no los duplica: registra la fotografía mensual y las decisiones.

## Ubicación

Carpeta del Vault: `04-Finanzas`

Estructura:

```
04-Finanzas/
├── Estrategia Financiera.md
├── Resumenes/
│   └── Resumen <Mes> <Año>.md
├── Inversiones/
│   └── Historial de Inversiones.md
├── Objetivos Financieros/
│   └── Objetivos 2026.md
└── Revisión Anual <Año>.md
```

## Cómo funciona

### Estrategia Financiera

- Decisiones vigentes de estrategia y su regla general: los excedentes se destinan a inversiones según la estrategia.
- Estrategia 2026: excedente mensual → normalmente fondo local; diciembre → aporte al ETF/VOO.
- Los aportes mensuales son **variables, no una obligación rígida**: dependen del excedente disponible, ingresos extraordinarios y gastos excepcionales.
- La estrategia se revisa una vez al año (no mes a mes), excepto cambios explícitos del usuario.

### Resúmenes mensuales

- Registro manual una vez por mes, con datos de AppFinanciera/Excel.
- Contenido: ingresos totales, egresos totales, inversión realizada, estado de las inversiones en Gletir (fondo local y ETF VOO), estado de préstamos (si existen), estado de tarjeta (si corresponde) y avance contra objetivos.
- Objetivo: una fotografía mensual comparable con los objetivos anuales.

### Inversiones

- **Definición canónica 2026** (documentada en `04-Finanzas/Objetivos Financieros/Objetivos 2026.md`, y no repetida aquí):
  - **Fondo local:** saldo **equivalente a USD 5.000** al cierre de diciembre de 2026, convertido desde UYU con la **cotización de diciembre**. No es una meta fija en pesos ni una obligación de aportes mensuales: depende del excedente disponible.
  - **VOO:** **+USD 1.500 adicionales** durante diciembre de 2026, sobre la posición ya existente. El **rendimiento no forma parte del aporte** y **no se fija un saldo final** para VOO.
- El historial de inversiones vive en `Inversiones/Historial de Inversiones.md`.
- No se registran montos, porcentajes ni asignación de cartera en tiempo real; eso lo custodia Gletir.

### Objetivos Financieros

- Objetivos patrimoniales y de inversión, con su estrategia de ahorro correspondiente.
- Las compras grandes/patrimoniales viven aquí; las adquisiciones corrientes viven en `08-Adquisiciones`.
- **Objetivo 2026 registrado**: ver la definición canónica en `Objetivos Financieros/Objetivos 2026.md` (fondo local ≈ USD 5.000 equivalente al cierre de diciembre convertido a la cotización de diciembre, y +USD 1.500 a VOO durante diciembre). Esta sección resume; no redefine las metas.
- Posible objetivo futuro (aún no decidido): crecimiento del fondo local hacia aproximadamente USD 7.000–8.000 para utilizar eventualmente parte como entrada para un vehículo. Los ETFs se mantienen como inversión de largo plazo.

### Revisión anual

- Revisión de metas vs realidad, evaluación de la estrategia del año.
- Evaluación de diversificación, otros ETFs, alternativas en USD, etc.
- Decide y actualiza `Estrategia Financiera.md` para el año siguiente.
- **Relación con el cierre global del año:** esta revisión financiera es una **revisión propia del área**, y su resultado alimenta el cierre anual global del sistema (`01-Objetivos/<Año>/Objetivos Anuales.md`, REVISOR ANUAL). El REVISOR ANUAL **no la reemplaza ni la recalcula**: la toma como insumo para evaluar la línea de finanzas del año. Ver `context/agentes.md` (REVISOR) y `context/rutina.md` (circuito de revisión acumulativo).

### Relación con el Planner

- El Planner recibe acciones financieras relevantes y planificables (p. ej. actualizar el resumen mensual, revisar excedente e invertir, realizar el aporte a VOO en diciembre, preparar la revisión anual).
- El Planner lee estrategia y resúmenes como contexto para decisiones, respeta el carácter variable de los aportes y **no inventa montos ni operaciones**.

## Decisiones

- Principio vigente: Obsidian Finanzas = estrategia, objetivos, resumen mensual, evolución y decisiones; no duplica la operación diaria.
- Estructura de 3 carpetas (Inversiones, Objetivos Financieros, Resumenes) aprobada, con las notas definidas en la arquitectura de esta sección.
- El Vault no duplica el registro diario de movimientos: AppFinanciera es la fuente principal; Obsidian se usa para resúmenes, análisis, objetivos y planificación.
- Fuente para el seguimiento del objetivo financiero: el **Excel** como detalle auxiliar; la aplicación financiera queda para los movimientos/datos operativos.
- Estrategia de inversión actual (ETF + fondo local Gletir en pesos) vigente hasta fin de año; es revisable y no es una regla permanente.
- Inversión mensual variable según excedente; no es obligación rígida.

## Roadmap financiero

Dirección de trabajo del sistema financiero. **Regla: el roadmap es dirección de trabajo, no autorización de ejecución.** Flujo: Analizar → Proponer → Usuario decide → Planificar → Usuario aprueba → Ejecutar. No es una lista rígida de tareas.

1. **Inversiones** — cargar y estructurar los datos reales históricos de Gletir. *(Ejecutada: `Inversiones/Historial de Inversiones.md` con datos 2026.)*
2. **Auditoría inicial de AppFinanciera** — revisar cómo registra hoy gastos, tarjeta, ingresos, totales y balances. *(Ejecutada: `REPORT-02.md` en el repo, read-only.)*
3. **Diseño gastos de terceros/reintegros** — proponer el cambio mínimo para representar gastos propios, gastos de terceros/adelantos, reintegros y dinero a recuperar, sin refactorizar innecesariamente. Se apoya en la evidencia de la Etapa 0 de AppFinanciera. **Condición de bloqueo, verificada el 30/09/2026:** el diseño estaba bloqueado hasta el cierre de la **subetapa 2.2** (totales del mes con gastos fijos), cerrada ese día. **No es necesario cerrar la Etapa 2 completa** para desbloquearlo: 2.4, 2.5 y 2.6 siguen sin empezar y 2.7 requiere aprobación propia, pero ninguna de ellas es condición del diseño. El diseño del modelo financiero es esta etapa 3; su implementación (etapa 4) **requiere aprobación explícita y separada** y no está autorizada.
4. **Implementación AppFinanciera** — solo después de aprobar el diseño.
5. **Datos reales financieros** — incorporar ingresos (desde ~jun 2026), gastos, inversiones y evolución con las fuentes ordenadas.
6. **Resúmenes financieros** — resúmenes mensuales en Obsidian con datos reales (evolución y cumplimiento de objetivos).
7. **Automatización** — endpoint/API de AppFinanciera e integración con Obsidian/Planner cuando las fuentes estén estables.

- **Estado actual:** etapa 1 completada (historial de inversiones 2026 cargado). Etapa 2 (Auditoría inicial de AppFinanciera) completada (`REPORT-02.md`, read-only). Del lado de la aplicación, AppFinanciera está en su **Etapa 2 en curso**: **2.1, 2.2, 2.3 y 2.8 cerradas** (25/09/2026 y 30/09/2026; `b46b570` · `119cc4a` · `7d71fb5` · `66ba009`), 2.4 · 2.5 · 2.6 sin empezar y **2.7 sin implementar** (detalle en `context/AppFinanciera.md`).
- **Próximo paso:** las etapas 3 y 4 (diseño e implementación de gastos de terceros/reintegros) se alimentan de la **Etapa 0 de AppFinanciera** (Relevamiento + contexto interno, completada; ver `context/AppFinanciera.md` y `opencode-AppFinanciera/HANDOFF-ETAPA-0-MAPA-CONTEXTO.md`) y del cierre de la **subetapa 2.2**, cerrada el 30/09/2026. Esa subetapa era la condición de bloqueo real del diseño; **cerrar la Etapa 2 completa no es requisito** para diseñarlo.
- Las etapas 2–4 requieren trabajo sobre AppFinanciera: primero se releva/audita y se diseña, y solo después se implementa. La Etapa 0 de AppFinanciera (nuevo esquema de etapas 0–4 de la aplicación) es el relevamiento que sostiene este diseño.
- No priorizar mejoras del Excel ni convertirlo en fuente de verdad; no crear estructuras nuevas en Obsidian sin aprobación.

### Objetivo de las etapas 2–4 y cierre de Finanzas

- Las etapas 2–4 tienen como objetivo llevar AppFinanciera al **mínimo funcional necesario** para que Finanzas pueda operar con datos reales y alimentar el análisis del Organizador (LEER → ANALIZAR → PROPONER); no para terminar la aplicación.
- **El cierre de Finanzas no equivale al cierre de AppFinanciera.** Alcanzado y validado el mínimo funcional, Finanzas puede considerarse cerrada aunque la aplicación conserve funcionalidades futuras por desarrollar (estadísticas, visualizaciones, mejoras de UX u otros módulos; ejemplos conceptuales que quedan como backlog de la aplicación y se deciden posteriormente).
- El endpoint y la automatización no son el "final" de AppFinanciera: son una posible etapa posterior del sistema de integración/automatización.

### Alcance funcional aprobado para 2026 (AppFinanciera)

Documentado en `context/programacion.md`. Estos casos deben quedar resueltos para que Finanzas pueda operar; **no se implementan en este BUILD**:

1. **Modelo de recuperaciones / settlements** para gastos propios, gastos de terceros, adelantos y reintegros, sin refactor innecesario.
2. **Corrección semántica:** el reintegro **no** es ingreso.
3. **Dinero a recuperar**, vinculado a gastos de terceros y adelantos.
4. **Liquidación de saldos** que preserva el historial.
5. **Gastos con tarjeta** dentro del modelo de recuperaciones (medio de pago y monto recuperable); **módulo propio de tarjeta fuera de alcance**.
6. **Extracción de datos manual**: suficiente; no requiere endpoint ni automatización.

### Criterio de cierre de Finanzas

Finanzas se considera suficientemente cerrada cuando:

1. El modelo financiero necesario está definido.
2. AppFinanciera registra correctamente la información que se necesita.
3. Están resueltos los casos relevantes de gastos propios, gastos de terceros/adelantos, reintegros y dinero a recuperar.
4. AppFinanciera permite obtener los datos financieros necesarios para el Organizador.
5. Esos datos permiten que el Organizador pueda: **LEER** la situación financiera; **ANALIZAR** evolución y cumplimiento; **PROPONER** acciones o decisiones.
6. Se trabaja con datos reales durante un período y se generan los resúmenes financieros de Obsidian.
7. Se puede revisar posteriormente si los datos, cálculos y el modelo funcionan correctamente.

No es requisito para cerrar Finanzas: terminar todas las funcionalidades futuras de AppFinanciera, tener endpoint, automatizar la transferencia de datos al Organizador, integrar automáticamente Obsidian/Planner, ni resolver ahora la etapa 7. La obtención de datos puede ser inicialmente manual; lo importante es que existan, sean confiables y puedan ser utilizados por el Organizador.

### Después del mínimo funcional

1. Dejar Finanzas en **observación** durante un período real (~1 mes).
2. Acumular datos reales y generar resumen financiero en Obsidian.
3. Revisar/analizar y comprobar que el modelo y los datos sirven.
4. Corregir únicamente si aparece un problema real.
5. Después de esa validación, decidir si se continúa con AppFinanciera o se avanza con otra parte del Organizador/proyectos.

## Sin definir aún

- Estrategia de inversión posterior a fin de año (se revisa en la revisión anual).
- Fechas y montos exactos de los objetivos patrimoniales futuros (auto, casa).
- Cómo se obtendrán los datos de las fuentes (AppFinanciera, Gletir, Excel) hacia los resúmenes (automatización futura, Fase 6).

### Evolución futura (ideas abiertas, NO son decisiones)

- Diversificar la cartera en la revisión de fin de año (otros ETFs, alternativas en USD, etc.).
- Interés de largo plazo de que las inversiones generen rendimientos/ingresos que contribuyan a la situación financiera.
- Estas ideas no están aprobadas para implementarse aún.