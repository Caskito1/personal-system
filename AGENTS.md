# AGENTS.md - Personal System

Este archivo es el centro de contexto y reglas del proyecto para OpenCode.
Se carga automáticamente al iniciar una conversación.

## Propósito del sistema

**Personal System** es un sistema de organización personal que vive en un Vault de Obsidian.
`personal-system` es el repositorio de contexto, reglas y decisiones para que OpenCode administre y desarrolle ese Vault a largo plazo.

No depende de una única conversación: el conocimiento permanente está en estos archivos y puede recuperarse en cualquier conversación nueva.

## Ubicación del Vault de Obsidian

Vault: `G:\Mi unidad\Organizador Personal`

Este Vault es el destino de todo el contenido. Nunca se administra desde otra ubicación.

## Estructura general del Vault

```
G:\Mi unidad\Organizador Personal\
├── 01-Objetivos\
│   └── 2026\
│       ├── Objetivos Anuales.md
│       ├── H1.md
│       └── H2.md
├── 02-Musica\
│   ├── Estudio\
│   ├── Instrumento\
│   ├── Partituras\
│   └── Toques\
├── 03-Programacion\
│   ├── Trabajo\
│   ├── Proyectos Personales\
│   ├── Freelance\
│   └── Estudio\
├── 04-Finanzas\
│   ├── Objetivos Financieros\
│   ├── Inversiones\
│   └── Resumenes\
├── 05-Otros Objetivos\
├── 06-Rutina\
│   ├── Mensual\
│   ├── Semanal\
│   └── Diario\
├── 07-Ideas\
├── 08-Adquisiciones\
└── 09-Calendario\
    ├── Toques.md
    ├── Eventos.md
    └── Entregas.md
```

La relación conceptual es: **Objetivos → Rutina → Revisión → Planificación**: los Objetivos definen qué quiero conseguir; la Rutina define qué voy a hacer y registra qué ocurrió; la Revisión analiza qué ocurrió; la Planificación propone qué debería ocurrir después. Revisión y Planificación son funciones de los agentes (Revisor y Planificador); las áreas del Vault son Objetivos y Rutina.

El modelo extendido **Objetivos → Rutinas/Proyectos → Planificación → Ejecución → Revisión** es una precisión conceptual de esa cadena, documentada en `context/arquitectura.md`; no reemplaza la cadena anterior.

## Planificador (asistente)

El Planner funciona como asistente de planificación, no como jefe. El diseño funcional completo está en `context/agentes.md`.

- Trabajo fijo lun–vie ≈ 8 h = capacidad reservada. Toda actividad extra en baja carga laboral la decide el usuario día a día; el Planner nunca la asume.
- Fin de semana = descanso por defecto. Rutinas de música y ejercicio principalmente lun–vie.
- Existe una **prioridad general de vida** (rutinas/disciplina → trabajo fijo → proyectos de programación → otros asuntos) que el Planner respeta siempre. La **prioridad de proyectos de programación** es solo el orden interno de esa categoría (registrada en la nota mensual de `06-Rutina/Mensual`, modificable); no es una prioridad global de la vida.
- El **foco del mes** es la dirección general del período; el **foco de la semana** es su operación concreta. Las rutinas (música, ejercicio) se protegen antes de llenar con proyectos.
- Ciclo: LEER → ANALIZAR → RECORDAR CONTEXTO → PROPONER → **USUARIO DECIDE** → PLANIFICAR, en niveles mensual → semanal → diaria → registro → revisión.
- Sugiere y no manda. No llena el tiempo. No reparte trabajo artificialmente.
- Bloqueos sin tareas inventadas. Recordatorio contextual breve; no preguntar lo ya conocido.
- Sin métricas de energía o cansancio.
- El plan no es un contrato: planificar → ejecutar → observar la realidad → ajustar → continuar.

## Índice de contextos

| Área | Contexto | Carpeta del Vault |
|---|---|---|
| Objetivos | `context/objetivos.md` | `01-Objetivos` |
| Música | `context/musica.md` | `02-Musica` |
| Programación | `context/programacion.md` | `03-Programacion` |
| Finanzas | `context/finanzas.md` | `04-Finanzas` |
| Otros Objetivos | `context/otros-objetivos.md` | `05-Otros Objetivos` |
| Rutina | `context/rutina.md` | `06-Rutina` |
| Ideas | `context/ideas.md` | `07-Ideas` |
| Agentes | `context/agentes.md` | — |
| Arquitectura | `context/arquitectura.md` | Todo el Vault |

Para trabajar en un área, leer primero su contexto correspondiente.

## Reglas de seguridad

1. **No eliminar información** sin autorización explícita del usuario. Nunca eliminar notas, archivos ni carpetas del Vault.
2. **No modificar objetivos ni notas personales** sin aprobación explícita.
3. **No crear estructuras innecesarias**: no crear archivos ni carpetas "porque sí".
4. **Mantener simplicidad**: evitar duplicación, metadata innecesaria, YAML complejo y sistemas que no se necesiten todavía.
5. **No depender de plugins**: la estructura no debe depender de plugins adicionales.
6. **No inventar información**: no completar conocimiento del usuario sin que él lo haya aprobado.

## Plan vs Build

- **Modo planificación**: proponer y preguntar. NO crear, modificar, mover ni eliminar nada.
- **Modo ejecución**: crear únicamente lo aprobado. No sobrepasar lo aprobado.

## Necesidad de aprobación

Pedir aprobación explícita antes de:
- Cambios estructurales (crear/reestructurar carpetas o archivos).
- Eliminar o mover cualquier cosa.
- Modificar objetivos o notas personales.
- Tomar decisiones permanentes sobre el sistema.
- Cambios en esta documentación de contexto o en el roadmap.

## Detección y mantenimiento de contexto

Al finalizar una tarea, planificación o modificación relevante, el agente debe comprobar si los cambios realizados generan una posible **desincronización entre los archivos operativos y su documentación, contexto o reglas de funcionamiento**.

### Detección

El agente debe detectar y señalar posibles necesidades de actualización cuando, por ejemplo:

- cambie una estructura, flujo o regla que esté documentada en archivos de contexto;
- se modifique el comportamiento esperado de un agente;
- una decisión nueva contradiga o deje desactualizada una definición existente;
- se agregue, elimine o reorganice una parte estructural del sistema;
- un archivo operativo y su documentación dejen de describir el mismo funcionamiento.

No debe considerar necesario actualizar el contexto por cambios puntuales u operativos que no alteren la estructura, las reglas o el funcionamiento general del sistema.

### Propuesta de mantenimiento

Cuando detecte una posible desincronización, el agente debe **informarla como una propuesta de mantenimiento**, indicando claramente:

- **Archivo afectado:** qué archivo de contexto o documentación podría necesitar actualización.
- **Motivo:** qué cambio produjo la posible desincronización.
- **Actualización propuesta:** qué información concreta debería agregarse, modificarse o eliminarse.

La propuesta debe ser independiente de la tarea original y no debe ejecutarse automáticamente.

### Aprobación explícita

El agente **no debe modificar archivos de contexto o documentación como consecuencia de esta detección sin aprobación explícita del usuario**.

El flujo obligatorio es:

1. Detectar la posible desincronización.
2. Informar la propuesta de mantenimiento.
3. Esperar la aprobación explícita del usuario.
4. Solo después de la aprobación, realizar la modificación propuesta.
5. Informar qué archivo fue actualizado y qué cambio se realizó.

La detección de una posible actualización **no implica autorización para escribirla**.

### Principio

El objetivo es mantener el contexto y la documentación sincronizados con la evolución real del sistema, **sin generar mantenimiento innecesario ni realizar cambios automáticos**.

El agente debe priorizar cambios de contexto que sean estructurales, relevantes y duraderos, evitando proponer actualizaciones por cada modificación menor o puntual.

## Acciones que nunca se realizan automáticamente

- Eliminar archivos, carpetas o notas.
- Mover o renombrar estructura del Vault.
- Modificar objetivos y notas personales.
- Instalar o configurar plugins de Obsidian.
- Crear sistemas complejos antes de ser necesarios.
- Editar este archivo ni `roadmap.md` sin aprobación.

## Regla de no eliminación

Toda eliminación de información requiere autorización explícita del usuario, incluso si la conversación anterior parecía implicarla.

## Regla de no modificación de objetivos/notas personales

Los objetivos y las notas personales del Vault solo se modifican con aprobación explícita. Las notas terminadas no se eliminan; se marca su estado cuando el usuario lo defina.

## Regla de simplicidad

Ante la duda, elegir la opción más simple. No crear estructuras, metadata ni sistemas antes de que exista una necesidad real.

## Regla de Git

No hacer `commit`, `rebase` ni `push` sin pedido explícito del usuario.

## Cómo recuperar contexto en una conversación nueva

1. `AGENTS.md` se carga automáticamente (este archivo): reglas globales e índice de contextos.
2. Leer `roadmap.md` para conocer el estado actual del proyecto.
3. Leer `context/<área>.md` del área en la que se va a trabajar.
4. Solo entonces trabajar sobre el Vault.

Máximo 3 archivos de lectura para estar operativo; no se depende de conversaciones anteriores.