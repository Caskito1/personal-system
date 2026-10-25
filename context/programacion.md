# Contexto - Programación

## Propósito

Área de organización de mi actividad como programador: trabajo profesional, proyectos personales, aprendizaje y freelance. Cada proyecto mantiene su propio contexto, objetivos y próximos pasos; no existe una lista global de tareas de programación.

## Ubicación

Carpeta del Vault: `03-Programacion`

Estructura:

```
03-Programacion/
├── Trabajo/
├── Proyectos Personales/
│   ├── Indice de Proyectos.md
│   ├── AppFinanciera.md
│   ├── VentoleraApp.md
│   ├── Organizador Personal.md
│   ├── Portfolio.md
│   └── Armador de Componentes B2B.md
├── Freelance/
└── Estudio/
```

## Conceptos

- **Proyecto** = iniciativa con resultado concreto que puede cerrarse.
- **Objetivo** = resultado buscado del proyecto.
- **Etapa / bloque** = parte secuencial del proyecto.
- **Próxima acción** = siguiente acción concreta de la etapa actual, registrada en la nota del proyecto.
- **Tarea** = acción concreta que entra en el plan semanal/diario del Planner.

Cada proyecto mantiene su propio contexto; no se mezclan los proyectos en una única lista de tareas.

## Cómo funciona

### Trabajo

- Trabajo profesional fijo (≈8 horas diarias) = **capacidad reservada** (lun–vie).
- Toda actividad extra en baja carga laboral la decide el usuario día a día; el Planner nunca la asume.
- Rol: Frontend. Stack principal: Next.js, Tailwind.
- Trabajo sobre varias páginas/proyectos.
- **Catálogo de componentes B2B**: análisis de una copia local del proyecto Next.js de TLW para producir un catálogo de componentes (IDs canónicos, dos vistas, contrato exportable). Repo propio: `opencode-CatalogoB2B` (GitHub privado, rama `main`). Fuente de decisión/estado: Vault `03-Programacion/Trabajo/Catalogo/Catálogo de componentes.md`; fuente técnica: el repo. Estado: Fases 0-1.6 del piloto completadas; punto de pausa (25/10/2026) pendiente de revisión visual y aprobación del usuario; etapa de variantes e inventario global no autorizados. Relacionado: **Armador de Componentes B2B** (Proyectos Personales; en definición).

### Proyectos Personales

#### AppFinanciera

Aplicación de finanzas (Next.js + Firebase). Es la **fuente operacional** de información financiera; no confundir con el área 04-Finanzas.

Objetivo actual: alcanzar el **mínimo funcional** para que Finanzas del Organizador pueda operar con datos reales (etapas 2–4 del roadmap financiero en `context/finanzas.md`). **El cierre de Finanzas no equivale al cierre de AppFinanciera:** las funcionalidades futuras propias quedan como backlog de la aplicación y se deciden posteriormente; el endpoint/API es parte de la automatización futura (Fase 6), no de estas etapas.

**Mínimo 2026 (alcance funcional aprobado, a documentar; no implementado en este BUILD):**

- Diseño aprobado del modelo de **recuperaciones / settlements** para representar gastos propios, gastos de terceros, adelantos y reintegros, **sin** refactor innecesario.
- **Corrección semántica:** los reintegros no son ingresos.
- Modelo de **dinero a recuperar** y su relación con gastos de terceros y adelantos.
- **Liquidación de saldos** que preserva el historial (no borra el pasado para cuadrar el presente).
- **Gastos con tarjeta** representados dentro del modelo de recuperaciones/settlements: la tarjeta es medio de pago y monto recuperable, **no un módulo propio de tarjeta** (fuera de alcance en 2026).
- **Cierre de los 11 puntos semánticos** del modelo (reglas semánticas del dominio de la aplicación; fuente canónica en `opencode-AppFinanciera/context/dominio.md`, secciones 2, 5, 6, 7, 10 y 11). Este BUILD documenta el alcance; no implementa el modelo.
- **Extracción manual** de datos: el uso de datos puede ser inicialmente manual; no requiere endpoint ni automatización.

Este BUILD **solo documenta** este alcance en los contextos. No implementa código ni modifica el repo `opencode-AppFinanciera`.

Estado: **Activo** — Etapa 0 (Relevamiento + construcción del contexto interno) **completada** vía el OpenCode del repo de AppFinanciera (contexto y agentes commiteados y pusheados en `opencode-AppFinanciera`, `d0c6fec`; verificado 23/09). Etapa 1 (Base estructural) **CERRADA (25/09/2026)**, commit `78e1461` en el repo. Etapa 2 (Correcciones y limpieza) **CERRADA (11/10/2026, 9/9 subetapas)**: 2.1 (taxonomía de gastos fijos + `Otros`) **CERRADA el 25/09/2026** con commit de producción `b46b570`; **2.2 (totales del mes con gastos fijos), 2.3 (ingresos: labels de bandas + sección `Otros`) y 2.8 (header `Personal` / `Total registrado`) CERRADAS el 30/09/2026** (`119cc4a` · `7d71fb5` · `66ba009`; Producción PASS con cuenta real); **2.9 (totales del header acotados al período) CERRADA el 06/10/2026** (`bfbdda4`) y **2.7 (guard `groupId`) CERRADA el 08/10/2026** (`96934c0`), ambas verificadas en Producción; **2.4 (robustez de sesión/redirección) CERRADA el 10/10/2026** (`1716a19`), verificada en Producción; **2.5 (retiro del flujo legacy de gastos fijos) y 2.6 (limpieza de código muerto) CERRADAS el 11/10/2026** (`3216095` · `10ab576`), ambas verificadas en Producción. El `HANDOFF-ETAPA-3.md` (diseño de Reintegros) está commiteado en el repo (`405a11c`), y `PROPUESTA-ETAPA-3.md` (diseño de Reintegros) está producida, commiteada (`e665e3d`, 14/10/2026) y **aprobada por el usuario (15/10/2026)**: **Etapa 3 CERRADA**; el diseño quedó como base de la **Etapa 4 (implementación de Reintegros), EN CURSO desde el 16/10/2026**: `HANDOFF-ETAPA-4.md` entregado (`5ca4e35`, 15/10) y `PROPUESTA-ETAPA-4.md` (plan técnico; nombre ordenado por el usuario) **aprobada 16/10** (`e57f6f0`) y **enmendada 17/10** (`0ed53ab`, secuencia hasta 4.5, sin confirmación bilateral); subetapas **4.0–4.3 implementadas** en `staging` con sus EVIDENCIA (4.3 cerrada 21–22/10; sigue **4.3-bis**); pendientes técnicos P-1…P-9 abordados subetapa por subetapa; cada subetapa y su promoción a Producción requieren aprobación explícita por separado. Acceso a Firestore read-only aprobado, sin escrituras ni migraciones. La auditoría inicial está completada en el repo (`REPORT-02.md`). El roadmap (etapas 0–4), las decisiones funcionales cerradas y el estado viven en `context/AppFinanciera.md`; los HANDOFF y PROPUESTAS aprobados viven en el repo del proyecto (`opencode-AppFinanciera/HANDOFF-ETAPA-0-MAPA-CONTEXTO.md`, `opencode-AppFinanciera/HANDOFF-ETAPA-1-BASE-ESTRUCTURAL.md`, `opencode-AppFinanciera/PROPUESTA-ETAPA-1.md`, `opencode-AppFinanciera/HANDOFF-ETAPA-2.md`, `opencode-AppFinanciera/PROPUESTA-ETAPA-3.md`, `opencode-AppFinanciera/HANDOFF-ETAPA-4.md`, `opencode-AppFinanciera/PROPUESTA-ETAPA-4.md`); el respaldo del contexto de sesión original está en `CONTEXTO-ETAPA3.md` del repo. Ver también `03-Programacion/Proyectos Personales/Indice de Proyectos.md` y `03-Programacion/Proyectos Personales/AppFinanciera.md`.

#### VentoleraApp

Web de la banda La Ventolera (Next.js, Tailwind). Dashboard con login (Firebase) que incluye sistemas de partituras y recibos de sueldo. No confundir con **Fiesta Ventolera** (`02-Musica`, proyecto musical independiente).

Estado: **En pausa** (detrás de AppFinanciera). Entrará al ciclo de proyectos con opencode (onboarding) cuando termine la parte de AppFinanciera.

Etapas previstas:

- armador de landings dentro del Dashboard;
- sistema de audios por canción dentro del Dashboard, en la sección de partituras.

No agregar más funcionalidades por ahora.

#### Organizador Personal

El sistema de organización personal que se construye con OpenCode (este sistema y el Vault de Obsidian). Proyecto principal actual.

**Definición de 2026 (objetivo anual):** el Organizador es la capa de **objetivos, prioridades, alcance, secuencia, handoffs, reportes y coordinación** que hace posible que los proyectos funcionen y se reporten. Su resultado esperado en 2026 es el **uso real del circuito de rutina y planificación (hasta el nivel mensual)** y que los proyectos reporten avances por el circuito, no el cierre técnico del sistema.

**Límite con la capa técnica:** el OpenCode de cada repositorio de proyecto (**OpenCode de proyecto**) conserva y utiliza el conocimiento técnico necesario para ejecutar las planificaciones aprobadas. El Organizador **no** duplica ese conocimiento ni sustituye al OpenCode de proyecto en la auditoría técnica, el plan técnico, la ejecución del código o la verificación. Ver `context/arquitectura.md`.

**Fuera de alcance en 2026:** Calendar (automatización de calendario), la FASE 6 de automatizaciones/integraciones y el cierre técnico completo del sistema. Calendar es una idea futura, no parte del objetivo anual 2026.

Flujo previsto:

1. Agentes
2. Diseño profundo de sistemas por área (Fase 4)
3. Datos reales (Fase 5)
4. Automatización (Fase 6): Calendario → Drive → AppFinanciera (mediante el endpoint de AppFinanciera).

#### VentoleraApp

Estado 2026: **Etapa 0 de recuperación y preparación.** En 2026 no se desarrolla funcionalidad nueva del dashboard; el trabajo es reapropiarse del proyecto y dejarlo preparado.

Mínimo 2026 (resultado esperado):

- **Etapa 0 ejecutada:** repo y OpenCode de proyecto preparados, auditoría inicial y plan derivados de ella.
- **Dossier / landing** editable y mantenida por el usuario.
- **Audio por partitura:** estructura del sistema de audios por canción en la sección de partituras, definida y con carga inicial.
- Cierre de la etapa con informe y **pendientes explícitamente asignados a 2027**.

Además de este mínimo, las etapas previstas (armador de landings dentro del Dashboard y demás funcionalidades) quedan para 2027 o posterior. No agregar más funcionalidades por ahora.

#### Portfolio

Portfolio profesional personal. Estado: **en pausa / en definición**. No se elimina. Dos pilares: (1) CV, carta de presentación y preparación para entrevistas (mantener actualizado con LinkedIn); (2) sección **Tools** con herramientas para optimizar procesos de trabajo (backlog inicial: optimizador/formateador de imágenes, armador de newsletter que toma datos de un PDF y los pasa a HTML). Antes de entrar al ciclo opencode se define el alcance de cada pilar.

**Mínimo 2026 (resultado esperado):** **Etapa 0** (repo y OpenCode de proyecto preparados, auditoría inicial y plan derivados de ella), resolver las inconsistencias necesarias para que la base quede coherente, **CV 2027** actualizado y **Tools** queda como backlog. Carta de presentación y entrevistas quedan como camino 2027; no se implementan en 2026.

### Ciclo de proyectos con opencode

- Principio de arquitectura: **el Organizador planifica y coordina; el OpenCode de cada proyecto conserva y utiliza el conocimiento técnico necesario para ejecutar autónomamente esas planificaciones**. Ver `context/arquitectura.md`.
- Cada proyecto personal puede tener su propio ciclo de trabajo con opencode, ejecutado en otra instancia de opencode dentro del repo del proyecto.
- Componentes por repo: `AGENTS.md` (reglas, incl. la definición canónica de tipos de documento), `ROADMAP.md` (roadmap propio), `opencode.json` (config mínima), `.opencode/agent/` (subagentes) y documentos de trabajo en `docs/` (HANDOFF, PROPUESTA, EVIDENCIA, REPORT — tipos y rutas canónicos en el `AGENTS.md` del repo).
- Estructura de conocimiento estándar dentro del repo del proyecto (confirmada en la Etapa 0 de AppFinanciera; documentación de trabajo en `docs/` desde la reorganización del 22/10/2026):

```
<repo>/
├── AGENTS.md                  (delgado: cómo trabajar + qué leer antes de trabajar)
├── ROADMAP.md
├── context/
│   ├── MAPA-<PROYECTO>.md     (puerta de entrada: qué es, estructura, dónde está cada cosa, referencias)
│   ├── arquitectura.md        (cómo funciona técnicamente)
│   └── dominio.md             (cómo debe comportarse el sistema, separado de la implementación)
├── .opencode/agent/           (agentes que el relevamiento justifique)
└── docs/
    ├── handoffs/              HANDOFF-*.md
    ├── propuestas/            PROPUESTA-*.md
    ├── reportes/              REPORT-*.md (+ docs históricos de contexto)
    └── evidencia/             EVIDENCIA-*.md (si el proyecto genera evidencia por subetapa)
```

- Regla de ubicación: los documentos de trabajo viven en `docs/` del repo del proyecto; si el código está en un repo anidado, la evidencia de cierre vive igual en `docs/evidencia/` del repo padre (commiteada en la misma sesión que el código, citando su hash).

- Regla de contexto: el conocimiento técnico vive en el repo del proyecto (no en `personal-system`). El Organizador conserva en sus contextos: objetivos, prioridades, decisiones, roadmap, estado, qué debe hacerse, resultado esperado, y restricciones/criterios.
- El Vault es el **panel de control y registro permanente**: `Indice de Proyectos.md` + nota por proyecto guardan estado, etapa, próxima acción y decisiones.
- `personal-system` actúa como **coordinador**: redacta los HANDOFF, evalúa las PROPUESTAS y los cierres (EVIDENCIA) y actualiza el panel tras cada decisión del usuario.
- Estados: proyecto → En definición / Activo / En pausa / Bloqueado; etapa → Pendiente / En curso / En revisión / Aprobada / Ajustes.
- Ciclo por etapa: HANDOFF → PROPUESTA → aprobación del usuario → ejecución → EVIDENCIA por subetapa → evaluación/cierre de etapa → actualización del Vault. REPORT: solo auditorías read-only. Definición canónica de tipos y rutas: `AGENTS.md` del repo del proyecto.

#### Onboarding de un proyecto

1. Pull/clonar el repo del proyecto.
2. Instalar/abrir opencode en la carpeta del repo.
3. Crear `AGENTS.md`, `ROADMAP.md` y `opencode.json` (+ subagentes si corresponden).
4. Primera intervención: redactar el `HANDOFF` de la etapa inicial (auditoría).
5. Registrar estado y próxima acción en la nota del Vault y en `Indice de Proyectos.md`.

### Freelance

Área para proyectos freelance que puedan aparecer. Actualmente no existe ningún proyecto freelance. SemanaNegra (cuando exista registro) vive aquí con su estado y bloqueos.

### Estudio

Aprendizaje en programación mediante cursos y proyectos personales. Estado: sin sistema concreto de seguimiento definido.

## Planner y Programación

- La **prioridad interna de proyectos** pertenece a Programación (orden dentro de `03-Programacion/Proyectos Personales`). Actualmente: **1. Organizador Personal · 2. AppFinanciera · 3. VentoleraApp · 4. Portfolio**. AppFinanciera va antes que VentoleraApp porque se necesita su mínimo funcional para cerrar Finanzas del Organizador; después de eso se vuelve al Organizador y luego se avanza con los demás.
- Esta prioridad NO reemplaza la prioridad general de vida del Planner (rutinas/disciplina → trabajo fijo → proyectos de programación → otros asuntos).
- Un proyecto fuera de foco en el período no genera tareas automáticamente.
- Un proyecto bloqueado no genera tareas: solo se señala el bloqueo y el Planner espera el checkpoint.
- La **próxima acción** de la nota del proyecto puede convertirse en una acción planificable del Planner.
- El estado de cada proyecto vive en su propia nota; los avances se registran allí y el Planner los lee para proponer.

## Decisiones

- Estructura de 4 carpetas (Trabajo, Proyectos Personales, Freelance, Estudio) aprobada.
- Los proyectos viven dentro del área correspondiente; los proyectos de programación viven en `03-Programacion/Proyectos Personales`. Ver modelo general en `context/arquitectura.md`.
- Proyectos vigentes: AppFinanciera, VentoleraApp, Organizador Personal, Portfolio (en pausa/en definición), Armador de Componentes B2B (en definición; depende del Catálogo B2B de Trabajo). El Catálogo B2B es un proyecto de Trabajo con repo propio (`opencode-CatalogoB2B`); no entra en la prioridad interna de Proyectos Personales.
- No confundir AppFinanciera con el área 04-Finanzas; no confundir VentoleraApp con Fiesta Ventolera (02-Musica).
- Prioridad interna de proyectos = orden dentro de Programación; independiente de la prioridad general de vida.

## Sin definir aún

- Organización concreta de Estudio (cursos, seguimiento, registro).
- Cómo se refleja el trabajo profesional aquí (¿algo más allá del contexto del área?).
- Qué pasa cuando aparezca un proyecto freelance concreto.

### Evolución futura (ideas abiertas, NO son decisiones)

- Incorporar IA en el flujo de trabajo profesional. No está implementado ni decidido.
- Agregar más funcionalidades a AppFinanciera (análisis de balances, seguimiento de inversiones, etc.).
- Agregar más funcionalidades al dashboard de VentoleraApp.
- Agregar herramientas al Portfolio.
- Automatización con Obsidian vía endpoint de AppFinanciera (Fase 6).
- Estas ideas no están aprobadas para implementarse aún.