# Roadmap - Personal System

Estado del proyecto de `personal-system`: la infraestructura de contexto y reglas para que OpenCode administre el Vault de Obsidian.

## Fases del proyecto

| Fase | Descripción | Estado |
|---|---|---|
| 1. Estructura del Vault | Crear y aprobar la estructura inicial de carpetas del Vault de Obsidian | ✅ Completada |
| 2. Contexto | Crear AGENTS.md, roadmap y contextos por área | ✅ Completada |
| 3. Agentes | Diseñar asistentes especializados por área | 🚧 En curso |
| 4. Sistemas | Diseñar cada área en profundidad | ✅ Completada |
| 5. Datos reales | Llenar el sistema con datos reales | ⏳ Pendiente |
| 6. Automatización | Calendario / app / Drive / etc. | ⏳ Pendiente |

## Estado actual

**Fase 3 en curso**: agentes del sistema. **Fase 3.3 implementada**: agente **PLANIFICADOR** READ-ONLY (especificación en `context/agentes.md`, registro técnico en `.opencode/agent/planificador.md`). **Fase 3.4 realizada y cerrada**: prueba real del PLANIFICADOR en la Semana 38 (14–20/09/2026), veredicto A (10/10 criterios, READ-ONLY verificado sin cambios en el Vault). Sin modificaciones de diseño; las dos observaciones menores optativas quedaron **descartadas por decisión del usuario** en 3.5. **Fase 3.5 completada**: escritura de notas de Rutina habilitada (creación, traslados, cierres, resúmenes), bajo aprobación explícita por escritura y limitada a `06-Rutina/**`; prueba real completada con el cierre de la Semana 38 y la apertura de la Semana 39. **Fase 3.6 (REVISOR): EN CURSO.** El REVISOR se especifica en `context/agentes.md` (herramienta de cierre y retrospectiva, niveles semanal y mensual, regla temporal para períodos abiertos, clasificación de acciones y persistencia de hallazgos en la nota del período siguiente) con registro técnico en `.opencode/agent/revisor.md`. Tras la prueba real (Semana 38 retrospectiva + Semana 39 en curso) se rediseñó la integración REVISOR↔PLANIFICADOR; queda pendiente el veredicto del usuario.

**Fase 4 completada**: diseño de sistemas en profundidad. **Planner V2 persistido** (frecuencia base de música en 3 sesiones; prioridad general de vida separada de la prioridad interna de proyectos). **Finanzas, Programación y Música especificadas** en `context/finanzas.md`, `context/programacion.md` y `context/musica.md` (arquitectura de notas, registro, estadísticas y relación con el Planner). Ajuste de nombres de proyectos (AppFinanciera, VentoleraApp, Organizador Personal, Portfolio en pausa/en definición) alineado en `context/agentes.md`, con prioridad actualizada (1. Organizador · 2. AppFinanciera · 3. VentoleraApp · 4. Portfolio). **Programación con ciclo de proyectos opencode** (HANDOFF → REPORT, panel en `Indice de Proyectos.md`) y **Finanzas enfocada al mínimo funcional de AppFinanciera** (etapas 2–4): el cierre de Finanzas no equivale al cierre de la aplicación.

**Siguiente**: Fase 5 — Datos reales: crear las notas reales del Vault con datos del usuario, comenzar el uso real y luego observar/ajustar. Sin automatizaciones.

## Notas

- Fase 1: Vault creado con estructura inicial aprobada en `G:\Mi unidad\Organizador Personal`. Se eliminó `Bienvenido.md` (nota predeterminada de Obsidian). Se agregó `07-Ideas` como carpeta independiente (separada de `05-Otros Objetivos`).
- Fase 2: creados AGENTS.md, roadmap.md y los 7 contextos de área, todos con conocimiento real definido y aprobado por el usuario durante la Fase 2.1.
- Fase 3: diseño conceptual (3.1, 2 agentes: Planificador y Revisor) y especificación (3.2) completados. Fase 3.3: PLANIFICADOR READ-ONLY implementado. Fase 3.4: prueba real en la Semana 38, veredicto A (READ-ONLY verificado por snapshot MD5 del Vault: 0 cambios); observaciones menores optativas descartadas por decisión del usuario. Fase 3.5 (completada): escritura de notas de Rutina (creación, traslados, cierres, resúmenes) con aprobación explícita por escritura y alcance `06-Rutina/**`; prueba real completada con el cierre de la Semana 38 y la apertura de la Semana 39. Fase 3.6 (en curso): REVISOR — agente read-only dedicado (herramienta de cierre y retrospectiva), especificado en `context/agentes.md` y con registro técnico en `.opencode/agent/revisor.md`. Diseño ajustado tras la prueba real (S38 retrospectiva + S39 en curso): integración REVISOR↔PLANIFICADOR, regla temporal (período abierto ≠ pendiente/deserción), clasificación de acciones (completada, en curso, pendiente real, trasladada, descartada, fantasma), niveles semanal/mensual, cierre como acción visible del período y persistencia de hallazgos en la nota del período siguiente. Pendiente veredicto del usuario.
- Fase 4: especificados Finanzas, Programación y Música. Finanzas: principio "pensar, decidir, proyectar y revisar" sin duplicar la operación; estructura `Estrategia Financiera.md`, `Resumenes/`, `Inversiones/Historial de Inversiones.md`, `Objetivos Financieros/Objetivos 2026.md`, `Revisión Anual`. Programación: 4 proyectos (AppFinanciera, VentoleraApp, Organizador Personal, Portfolio en pausa/en definición), conceptos proyecto/objetivo/etapa/próxima acción/tarea, prioridad interna separada de la de vida, ciclo de proyectos con opencode y foco en el mínimo funcional de AppFinanciera para cerrar Finanzas. Música: base 3 sesiones, rutina 6 pasos, `Estudio/Ejercicios.md`, registro por sesión `Registro/<AAAA-MM-DD>.md`, estadísticas semanales/mensuales, repertorio separado, clases como fuente de indicaciones. No se crearon notas reales del Vault en esta fase.
- Fase 5: crear las notas reales por área con datos del usuario, comenzar el uso real, luego observar y ajustar. No implementada.
- Fase 6: automatización (Calendario → Drive → AppFinanciera vía endpoint). Posterior.