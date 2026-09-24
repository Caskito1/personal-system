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
│   └── Portfolio.md
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

### Proyectos Personales

#### AppFinanciera

Aplicación de finanzas (Next.js + Firebase). Es la **fuente operacional** de información financiera; no confundir con el área 04-Finanzas.

Objetivo actual: alcanzar el **mínimo funcional** para que Finanzas del Organizador pueda operar con datos reales (etapas 2–4 del roadmap financiero en `context/finanzas.md`). **El cierre de Finanzas no equivale al cierre de AppFinanciera:** las funcionalidades futuras propias quedan como backlog de la aplicación y se deciden posteriormente; el endpoint/API es parte de la automatización futura (Fase 6), no de estas etapas.

Estado: **Activo** — Etapa 0 (Relevamiento + construcción del contexto interno) **completada** vía el OpenCode del repo de AppFinanciera (contexto y agentes commiteados y pusheados en `opencode-AppFinanciera`, `d0c6fec`; verificado 23/09). Etapa 1 (Base estructural) con HANDOFF entregado (24/09, `context/HANDOFF-ETAPA-1-BASE-ESTRUCTURAL.md`), pendiente de decisión/inicio; acceso a Firestore read-only aprobado para el relevamiento. La auditoría (Etapa 2) está completada en el repo (`REPORT-02.md`). El roadmap (etapas 0–4), las decisiones funcionales cerradas y el estado viven en `context/AppFinanciera.md`; el HANDOFF aprobado y entregado está en `context/HANDOFF-ETAPA-0-MAPA-CONTEXTO.md` (fuente) y commiteado en el repo destino (`opencode-AppFinanciera`); el respaldo del contexto de sesión original está en `CONTEXTO-ETAPA3.md` del repo. Ver también `Indice de Proyectos.md` y `03-Programacion/Proyectos Personales/AppFinanciera.md`.

#### VentoleraApp

Web de la banda La Ventolera (Next.js, Tailwind). Dashboard con login (Firebase) que incluye sistemas de partituras y recibos de sueldo. No confundir con **Fiesta Ventolera** (`02-Musica`, proyecto musical independiente).

Estado: **En pausa** (detrás de AppFinanciera). Entrará al ciclo de proyectos con opencode (onboarding) cuando termine la parte de AppFinanciera.

Etapas previstas:

- armador de landings dentro del Dashboard;
- sistema de audios por canción dentro del Dashboard, en la sección de partituras.

No agregar más funcionalidades por ahora.

#### Organizador Personal

El sistema de organización personal que se construye con OpenCode (este sistema y el Vault de Obsidian). Proyecto principal actual.

Flujo previsto:

1. Agentes
2. Diseño profundo de sistemas por área (Fase 4)
3. Datos reales (Fase 5)
4. Automatización (Fase 6): Calendario → Drive → AppFinanciera (mediante el endpoint de AppFinanciera).

#### Portfolio

Portfolio profesional personal. Estado: **en pausa / en definición**. No se elimina. Dos pilares: (1) CV, carta de presentación y preparación para entrevistas (mantener actualizado con LinkedIn); (2) sección **Tools** con herramientas para optimizar procesos de trabajo (backlog inicial: optimizador/formateador de imágenes, armador de newsletter que toma datos de un PDF y los pasa a HTML). Antes de entrar al ciclo opencode se define el alcance de cada pilar.

### Ciclo de proyectos con opencode

- Principio de arquitectura: **el Organizador planifica y coordina; el OpenCode de cada proyecto conserva y utiliza el conocimiento técnico necesario para ejecutar autónomamente esas planificaciones**. Ver `context/arquitectura.md`.
- Cada proyecto personal puede tener su propio ciclo de trabajo con opencode, ejecutado en otra instancia de opencode dentro del repo del proyecto.
- Componentes por repo: `AGENTS.md` (reglas), `ROADMAP.md` (roadmap propio), `HANDOFF-<etapa>.md` (orden de trabajo), `opencode.json` (config mínima), `.opencode/agent/` (subagentes) y `REPORT-<etapa>.md` (entregable de vuelta).
- Estructura de conocimiento estándar dentro del repo del proyecto (a confirmar/ajustar por relevamiento en cada etapa correspondiente):

```
<repo>/
├── AGENTS.md                  (delgado: cómo trabajar + qué leer antes de trabajar)
├── ROADMAP.md
├── context/
│   ├── MAPA-<PROYECTO>.md     (puerta de entrada: qué es, estructura, dónde está cada cosa, referencias)
│   ├── arquitectura.md        (cómo funciona técnicamente)
│   └── dominio.md             (cómo debe comportarse el sistema, separado de la implementación)
├── .opencode/agent/           (agentes que el relevamiento justifique)
├── HANDOFF-*.md
└── REPORT-*.md
```

- Regla de contexto: el conocimiento técnico vive en el repo del proyecto (no en `personal-system`). El Organizador conserva en sus contextos: objetivos, prioridades, decisiones, roadmap, estado, qué debe hacerse, resultado esperado, y restricciones/criterios.
- El Vault es el **panel de control y registro permanente**: `Indice de Proyectos.md` + nota por proyecto guardan estado, etapa, próxima acción y decisiones.
- `personal-system` actúa como **coordinador**: redacta los HANDOFF, evalúa los REPORT y actualiza el panel tras cada decisión del usuario.
- Estados: proyecto → En definición / Activo / En pausa / Bloqueado; etapa → Pendiente / En curso / En revisión / Aprobada / Ajustes.
- Ciclo por etapa: HANDOFF → ejecución (en el repo) → REPORT → evaluación → decisión → actualización del Vault.

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
- Proyectos vigentes: AppFinanciera, VentoleraApp, Organizador Personal, Portfolio (en pausa/en definición).
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