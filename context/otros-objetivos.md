# Contexto - Otros

## Propósito

Espacio abierto para asuntos personales temporales o concretos que requieren atención, seguimiento o resolución, pero que no encajan en las áreas principales del sistema.

## Ubicación

Carpeta del Vault: `05-Otros`

Estructura actual:

```
05-Otros/
├── Otros Objetivos/
│   ├── Licencia de Conducir.md
│   └── Arreglo del Pasillo.md
├── Rutina de Ejercicio/
│   ├── Rutina de Ejercicio.md
│   └── Registro/
└── NotasPsicologicas/
    ├── Diseño.md
    └── Registro/
```

La carpeta existe: `Otros Objetivos/` agrupa tareas u objetivos puntuales que no tienen otra categoría (no es una lista de espera: pueden estar en ejecución); `Rutina de Ejercicio/` y `NotasPsicologicas/` son subáreas de registro propio.

## Cómo funciona

- Es un área deliberadamente abierta y flexible, sin jerarquía fija.
- Agrupa asuntos personales que requieren atención puntual:
  - Seguimiento de familia y amigos: recordar y atender a alguien que está
    enfermo, atraviesa algo importante, o algo que quiero tener presente
    para acompañarlo.
  - Proyectos personales de la vida cotidiana (ejemplos: clases de manejo
    para sacar la libreta, construir un sistema para el teclado en el
    escritorio, mejorar la iluminación del living).
  - Otros asuntos concretos que aparezcan en la vida y quiera atender.

Los ejemplos anteriores no son una lista cerrada de categorías.

### Diferencia con 01-Objetivos

- 01-Objetivos guarda la jerarquía estructurada de objetivos (anual y
  semestral) de las áreas principales.
- 05-Otros es abierto, sin jerarquía, para asuntos temporales
  y puntuales que no pertenecen a otras áreas.

### Separación de Ideas

El espacio de Ideas vive ahora en `07-Ideas` (carpeta independiente en el
Vault) y su contexto está en `context/ideas.md`. No forma parte de esta área.

## Decisiones

- Área deliberadamente abierta y flexible; no se sobreestructura.
- Contiene asuntos personales abiertos que necesitan atención, seguimiento o resolución: puede incluir proyectos personales, tareas puntuales o seguimientos. No es una carpeta transversal `Proyectos`. Ver `context/arquitectura.md`.
- Se diferencia de 01-Objetivos: aquí no hay jerarquía de objetivos.
- Los seguimientos de personas se plantean como cosas a recordar y
  atender, sin convertirlos automáticamente en tareas recurrentes.
- Ideas no pertenece a esta área; ahora vive en `07-Ideas`.
- `NotasPsicologicas/` es un subárea de registro personal introspectivo (diseño en `NotasPsicologicas/Diseño.md`): una nota por fecha, texto libre, sin análisis. La frecuencia de escritura es personal (~1–2 semanas); la relectura mensual la recuerda el Planner antes del cierre de mes. No es un asunto puntual ni un objetivo.
- `Rutina de Ejercicio/Registro/` guarda una nota por sesión de ejercicio (`<AAAA-MM-DD>.md`) con los datos de la tabla del bloque `### Ejercicio` de la daily, transcrita al cierre del día (misma lógica que el registro de música).

## Sin definir aún

- Formato de registro de cada asunto (¿nota por asunto, otra forma?).
- Formato de registro de los seguimientos de personas.
- Si conviene crear subcarpetas cuando un asunto adquiera continuidad o
  si permanece todo en un solo nivel.
- Cómo se marcarán los asuntos como terminados o atendidos.