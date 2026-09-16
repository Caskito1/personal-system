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

Próximos pasos:

- usar OpenCode dentro del proyecto;
- corregir visualización de ingresos freelance;
- agregar sistema de items pendientes;
- agregar balance y estadísticas de productividad;
- crear endpoint/API para futura automatización (el Organizador Personal podrá consultar información de AppFinanciera mediante ese endpoint).

La automatización con Obsidian NO se implementa todavía (Fase 6).

#### VentoleraApp

Web de la banda La Ventolera (Next.js, Tailwind). Dashboard con login (Firebase) que incluye sistemas de partituras y recibos de sueldo. No confundir con **Fiesta Ventolera** (`02-Musica`, proyecto musical independiente).

Próximos pasos:

- incorporar OpenCode al proyecto;
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

Portfolio profesional personal con una sección de herramientas ("Tools") para el trabajo diario. Estado actual: **en pausa**. No se elimina.

### Freelance

Área para proyectos freelance que puedan aparecer. Actualmente no existe ningún proyecto freelance. SemanaNegra (cuando exista registro) vive aquí con su estado y bloqueos.

### Estudio

Aprendizaje en programación mediante cursos y proyectos personales. Estado: sin sistema concreto de seguimiento definido.

## Planner y Programación

- La **prioridad interna de proyectos** pertenece a Programación (orden dentro de `03-Programacion/Proyectos Personales`). Actualmente: 1. Organizador Personal · 2. VentoleraApp · 3. AppFinanciera.
- Esta prioridad NO reemplaza la prioridad general de vida del Planner (rutinas/disciplina → trabajo fijo → proyectos de programación → otros asuntos).
- Un proyecto fuera de foco en el período no genera tareas automáticamente.
- Un proyecto bloqueado no genera tareas: solo se señala el bloqueo y el Planner espera el checkpoint.
- La **próxima acción** de la nota del proyecto puede convertirse en una acción planificable del Planner.
- El estado de cada proyecto vive en su propia nota; los avances se registran allí y el Planner los lee para proponer.

## Decisiones

- Estructura de 4 carpetas (Trabajo, Proyectos Personales, Freelance, Estudio) aprobada.
- Los proyectos viven dentro del área correspondiente; los proyectos de programación viven en `03-Programacion/Proyectos Personales`. Ver modelo general en `context/arquitectura.md`.
- Proyectos vigentes: AppFinanciera, VentoleraApp, Organizador Personal, Portfolio (en pausa).
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