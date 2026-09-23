# Contexto - Arquitectura

## Propósito

Referencia de la arquitectura conceptual del Organizador Personal: áreas vs tipos, modelo general del sistema, capas transversales y definiciones. Los contextos de área referencian este archivo; aquí no se duplica contenido de área.

## Estructura del Vault

```
Organizador Personal
│
├── 01-Objetivos
│
├── 02-Musica
│   ├── Estudio
│   ├── Instrumento
│   ├── Partituras
│   └── Toques
│
├── 03-Programacion
│   ├── Trabajo
│   ├── Proyectos Personales
│   ├── Freelance
│   └── Estudio
│
├── 04-Finanzas
│   ├── Objetivos Financieros
│   ├── Inversiones
│   └── Resumenes
│
├── 05-Otros
│
├── 06-Rutina
│   ├── Mensual
│   ├── Semanal
│   └── Diario
│
├── 07-Ideas
│
├── 08-Adquisiciones
│
└── 09-Calendario
    ├── Toques
    ├── Eventos
    ├── Entregas
    └── Recordatorios.md
```

## Áreas vs tipos

- Las carpetas principales representan **áreas de vida**: Objetivos, Música, Programación, Finanzas, Otros, Rutina, Ideas.
- Las categorías/tipos representan otra dimensión conceptual: Objetivos, Rutinas, Proyectos, Adquisiciones, Eventos, Ideas, Planificación, Ejecución, Revisión.
- No existe una carpeta transversal `Proyectos` ni una carpeta transversal `Tareas`.
- Los proyectos viven dentro del área correspondiente.
- Las acciones concretas correspondientes se gestionan desde `06-Rutina`.

## Modelo general

```
OBJETIVOS
    ↓
RUTINAS / PROYECTOS
    ↓
PLANIFICACIÓN
  ├─ MENSUAL
  ├─ SEMANAL
  └─ DIARIA
    ↓
EJECUCIÓN
    ↓
REVISIÓN
    ↺
```

La cadena **Objetivos → Rutina → Revisión → Planificación** es una decisión existente del sistema; el modelo extendido es una precisión conceptual de esa cadena, no una implementación nueva.

Dos capas transversales alimentan la planificación:

```
ADQUISICIONES ─────┐
                   ├──→ PLANIFICACIÓN
CALENDARIO ────────┘
```

### Capacidad y carga

- Trabajo fijo lun–vie ≈ 8 h = capacidad reservada. La baja carga laboral se decide día a día por el usuario; el Planner nunca la asume disponible.
- Fin de semana = descanso por defecto. Solo se usa para compromisos, actuaciones, grabaciones, eventos o necesidad concreta.
- Espacio principal para proyectos personales: lun–vie, fuera del trabajo fijo.

### Jerarquía de prioridades

La "prioridad de proyectos" NO es una jerarquía general de la vida del usuario. Son conceptos distintos:

**Prioridad general de vida** (estable, no cambia por período):

```
1. Rutinas y disciplina personal
   ├── Música (estudio del instrumento)
   └── Ejercicio
2. Trabajo fijo (lun–vie, 8 h)
3. Proyectos personales de programación
4. Otros asuntos (según contexto, fechas y necesidad)
```

**Foco del mes**: dirección general de un período. Puede abarcar varias áreas (música, actuación, examen, programación, etc.). No equivale a prioridad de proyectos; vive en la nota mensual de `06-Rutina/Mensual`.

**Prioridad de proyectos de programación**: solo el orden interno dentro de `03-Programacion/Proyectos Personales`. Preferencia del período, no permanente, modificable por el usuario. Se activa únicamente cuando existe capacidad para programación personal.

**Foco de la semana**: dirección operativa de la semana. Deriva del foco mensual + calendario + ejecución previa.

El objetivo de H2 no es desarrollar muchos proyectos de programación: es construir disciplina (música y ejercicio), mantener trabajo y mejorar profesionalmente. Los proyectos no desplazan automáticamente las rutinas.

### Criterio de capacidad

El Planner asigna capacidad en este orden conceptual:

```
1. Compromisos fijos (eventos, clases, toques, ensayos)
2. Trabajo fijo (8 h, lun–vie)
3. Rutinas fundamentales (música, ejercicio)
4. Proyectos personales de programación
5. Otros asuntos
```

No todos los niveles deben llenarse siempre. Una semana puede ser `Compromisos + Trabajo + Rutinas` y no tener proyecto personal; es un resultado correcto. El Planner se pregunta primero "¿qué es importante proteger esta semana?" antes de "¿qué proyecto puedo meter?".

Sobre todo el proceso opera el **Planner como asistente de planificación** (Diseño Funcional V2):

```
LEER → ANALIZAR → RECORDAR CONTEXTO → PROPONER → USUARIO DECIDE → PLANIFICAR
```

Ciclo de planificación: **mensual → semanal → diaria → ejecución/registro → revisión ↺**. La operación del ciclo —cierre del período → revisión (REVISOR) → persistencia de hallazgos → propuesta (PLANIFICADOR) → decisión → apertura— está definida en `context/agentes.md` (sección **Ciclo del sistema**).

- El Planner sugiere y no manda; la decisión final siempre es del usuario.
- Las rutinas de música y ejercicio son comportamiento estable, no proyectos que compiten por prioridad: se protegen antes de llenar espacios con proyectos.
- La prioridad de proyectos de programación solo aplica dentro de esa categoría. El Planner nunca interpreta "Organizador es prioridad 1" como "hay que darle más tiempo que a música".
- No reparte trabajo artificialmente entre todos los proyectos. Se prefiere concentración.
- No llena el tiempo disponible: busca una carga razonable y sostenible.
- Con poco tiempo disponible, reduce o elimina el bloque de programación; mantiene rutinas. Eso no significa que el proyecto perdió prioridad.
- Bloqueos sin tareas inventadas. Recordatorio contextual breve; no preguntar lo ya conocido.
- Sin métricas de energía o cansancio.
- El plan no es un contrato: planificar → ejecutar → observar la realidad → ajustar → continuar.

## Coordinación con OpenCode por proyecto

Principio de arquitectura del trabajo con opencode en los proyectos personales:

> **El Organizador planifica y coordina. El OpenCode de cada proyecto conserva y utiliza el conocimiento técnico necesario para ejecutar autónomamente esas planificaciones.**

`personal-system` no es el repositorio del conocimiento técnico de cada proyecto.

- **El Organizador conoce:** objetivos; prioridades; decisiones; roadmap; estado de cada proyecto; qué debe hacerse; qué resultado se espera; restricciones y criterios importantes.
- **El repo del proyecto conserva:** conocimiento técnico; arquitectura; funcionamiento real; modelo de dominio; estructura de datos; convenciones; agentes; reglas de trabajo; contexto específico de la aplicación; decisiones técnicas relevantes.

Aplicado a proyectos, el ciclo es: el Organizador redacta un HANDOFF relativamente conciso; el OpenCode del proyecto lo ejecuta respetando su propio contexto (estructura `context/` estándar, ver `context/programacion.md`); el proyecto devuelve un REPORT; el Organizador evalúa y actualiza el panel del Vault.

**Relación conceptual dentro del modelo general:** la planificación que alimenta `PLANIFICACIÓN → EJECUCIÓN → REVISIÓN` es del Organizador; la ejecución técnica que la materializa vive en el repo de cada proyecto, organizada por su propio opencode.

## Definiciones

### Objetivos

Indican qué se quiere conseguir y determinan prioridades. Viven en `01-Objetivos`.

### Rutinas

Actividades recurrentes que no tienen un cierre definitivo. Ejemplos: estudio de instrumento, estudio de programación, trabajo fijo, ejercicio, rutina financiera.

- La **definición** de cada rutina vive en su área natural (Música → `02-Musica/Estudio`; ejercicio → `05-Otros`).
- La **ejecución** vive en `06-Rutina` (notas mensual/semanal/diaria), que enlaza a la definición sin copiarla.

### Proyectos

Tienen un resultado concreto y eventualmente se cierran. Ejemplos: proyecto personal de programación, repertorio para una presentación, obtener la libreta, resolver una mejora concreta del hogar.

### Adquisiciones

Categoría transversal con ciclo propio:

```
idea → investigar → decidir → comprar → adquirido
```

No generan automáticamente tareas. Viven en `08-Adquisiciones`. Las compras grandes/patrimoniales (p. ej. un auto) siguen viviendo en `04-Finanzas/Objetivos Financieros`.

Criterio de clasificación: **objeto que se quiere comprar** → `08-Adquisiciones`; **trabajo/instalación/reparación** → `05-Otros`. Los materiales de una reparación no se registran como adquisición separada.

### Calendario

Capa transversal en `09-Calendario`: representa restricciones y contexto temporal (toques, ensayos, eventos, entregas, grabaciones, recordatorios). No reemplaza el lugar donde vive la información original: sus notas son índices/contexto temporal que enlazan al contenido real. Los toques continúan viviendo en `02-Musica/Toques`; los eventos generales sin área natural pueden vivir en `09-Calendario/Eventos.md`. Ensayos, grabaciones y otros eventos musicales sin lugar preciso todavía viven su dato temporal en `Eventos.md` y luego se enlazan desde su ámbito natural cuando exista.

Dentro de `09-Calendario`, los **recordatorios** viven separados de los eventos, en `09-Calendario/Recordatorios.md`. Diferencia conceptual entre ambas entidades:

- **Evento**: algo que ocurre en el calendario (ensayo, toque, cumpleaños, partido, clase, reunión, compromiso con fecha/hora).
- **Recordatorio**: algo que se quiere tener presente. Puede estar asociado a una fecha/hora, pero no representa necesariamente un evento de calendario (p. ej. "Terapia Rebeca — 21:00", "Resultado de la resonancia de mi madre — 12:00").

No se mezclan ambas entidades conceptualmente: los eventos salen de los archivos de evento (`Eventos.md`, `Toques.md`, `Entregas.md`) y los recordatorios de `09-Calendario/Recordatorios.md`.

Las clases de conducir tienen su fuente original en el proyecto [[Licencia de Conducir]] (`05-Otros`); el calendario solo indexa la fecha.

### Contexto dinámico semanal

Compromisos variables que se definen semana a semana (visita a familiares, partidos de Peñarol, toques/ensayos de la semana, compromisos puntuales). No se convierten automáticamente en eventos permanentes del calendario; se registran de forma ligera en la nota semanal de `06-Rutina` para que la Revisión entienda los desvíos.

**Recordatorio contextual de lunes**: al inicio de la semana, el Planner puede ofrecer un breve resumen del contexto relevante (compromisos conocidos, prioridad vigente, bloqueos). Es un recordatorio conciso, no un interrogatorio. Si la información ya está disponible, no se repite.

### Ideas

Son posibilidades, no obligaciones. Viven en `07-Ideas`.

### Planificación

Utilizará objetivos, rutinas, proyectos, calendario, bloqueos y contexto para decidir qué es razonable hacer durante un período. Se define en niveles:

- **Mensual**: define el enfoque y las prioridades del mes. El foco mensual vive en `06-Rutina/Mensual`; no existe una entidad separada para el "foco mensual".
- **Semanal**: organiza y distribuye el trabajo según la realidad, considerando calendario, bloqueos, rutinas, proyectos activos y lo ocurrido la semana previa. El contexto dinámico se registra de forma ligera en la nota semanal.
- **Diaria**: bajada liviana del plan semanal a días concretos; no es una tercera sesión compleja de planificación.

**No implementada aún.**

### Ejecución

Representará lo que realmente ocurrió, con registro diario liviano (Hecho / No hecho / Extra / Nota). Las secciones vacías se omiten; no es un formulario. **No implementada aún.**

### Revisión

La ejecuta el **REVISOR** (agente read-only, Fase 3.6 en curso) entre el cierre del período y la propuesta del siguiente (Ciclo del sistema, `context/agentes.md`). Compara lo planificado con lo ejecutado sobre el período **cerrado**, clasifica las acciones y responde: qué se planeó, qué ocurrió, qué quedó pendiente, qué apareció sin estar previsto, qué se traslada, qué se descarta, qué se prioriza después. Los hallazgos relevantes se persisten en la nota del período siguiente (sección `## Hallazgos de la revisión de <período>`) y los consume el **PLANIFICADOR** como contexto de la próxima propuesta. La operación completa está definida en `context/agentes.md` (sección **REVISOR**).

### Aclaraciones de proyectos

- **Ventolera (web)** = proyecto de programación (`03-Programacion/Proyectos Personales`): web de la banda La Ventolera, dashboard, Next.js/Tailwind.
- **Fiesta Ventolera** = proyecto musical (`02-Musica`): evento/gala de la banda. Proyecto independiente del de programación.
- **La Ventolera (categoría del Daily)** = categoría de presentación de `## Acciones` en la nota diaria (ver `context/rutina.md`): tareas que realizo para la banda que no son actividad musical ni desarrollo del proyecto web (producción, organización, diseño de afiches, comunicación, contenido/publicación/gestión del sitio). No es área física ni proyecto: no existe carpeta, nota ni estructura propia; solo clasifica tareas en el Daily. "Web" por sí sola no determina la categoría: desarrollo/funcionalidad → Ventolera (web); contenido/publicación/gestión → La Ventolera.

### Fuente financiera para seguimiento de objetivos

- **Excel** = fuente para el seguimiento del objetivo financiero (ingresos mensuales, cuentas, evolución, acumulado).
- **Aplicación financiera** = fuente de movimientos/datos operativos (registro diario de ingresos/egresos).
- No se modifica la estrategia de inversión ni el área 04-Finanzas.

## Fases funcionales del sistema

Eje de funcionalidad del sistema (no confundir con las fases de desarrollo del proyecto, que viven en `roadmap.md`):

1. **Núcleo de organización**: objetivos, proyectos, rutinas, calendario, adquisiciones, planificación mensual/semanal/diaria, ejecución y revisión, con capacidad de profundizar y ajustar cualquier elemento en cualquier momento.
2. **Planner conversacional**: analiza objetivos, proyectos, rutinas y calendario; detecta bloqueos y fechas; revisa el progreso real; sugiere prioridades; pregunta por cambios; ayuda a organizar el mes y la semana. Asistente, no jefe.
3. **Contexto semanal dinámico**: preguntas/contexto variables semana a semana (toques, visitas, partidos, compromisos puntuales), con persistencia ligera en la nota semanal.

La evolución conceptual: **Objetivos → Proyectos/Rutinas → Planificación mensual → semanal → diaria → Ejecución → Revisión**, con el Planner como capa de inteligencia: contexto + estado real + calendario + prioridades → preguntas → propuesta → decisión del usuario → plan.

## Reglas vigentes

1. No duplicar información.
2. Cada nota tiene un único lugar físico.
3. Las vistas o índices transversales utilizan enlaces.
4. No crear carpetas transversales `Proyectos` ni `Tareas`.
5. El foco mensual vive en `06-Rutina/Mensual`; no se crean entidades nuevas para representarlo.
6. Aún no se introducen: YAML/metadatos, nuevos estados de proyectos, automatizaciones, integración real con Google Calendar/Outlook, escritura automática del Planificador, Planner conversacional, ni contexto semanal dinámico automatizado.