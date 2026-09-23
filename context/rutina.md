# Contexto - Rutina

## Propósito

Define las acciones y la organización temporal para avanzar hacia los objetivos. Es el segundo eslabón de la cadena **Objetivos → Rutina → Revisión → Planificación**: toma el "qué quiero conseguir" (01-Objetivos), lo convierte en "qué voy a hacer" en distintos períodos y registra qué ocurrió.

## Ubicación

Carpeta del Vault: `06-Rutina`

Estructura actual:

```
06-Rutina/
├── Mensual/
├── Semanal/
└── Diario/
```

Las tres carpetas están en uso (Mensual, Semanal y Diario).

## Cómo funciona

- Se organiza por períodos en tres niveles: Mensual, Semanal y Diario.
- Las notas se nombran **por período**, con nombres en lenguaje natural: mensual `Septiembre 2026.md` en `Mensual/`, semanal `Semana 36.md` en `Semanal/`, diaria `9 de Septiembre.md` en `Diario/`.
- Los niveles Mensual, Semanal y Diario de la jerarquía general (Anual → Semestral → Mensual → Semanal → Diario) viven aquí, no en Objetivos.
- NO se duplican los objetivos dentro de Rutina: las notas de rutina pueden enlazar a los objetivos correspondientes mediante enlaces internos de Obsidian.
- Conceptualmente, esta área será el lugar donde se materializan las acciones concretas derivadas de objetivos, rutinas y proyectos (planificación, ejecución y revisión). El modelo general está en `context/arquitectura.md`; esa lógica no se implementa todavía.
- Estado actual: el sistema de rutina está en uso (nota mensual en curso, notas semanales y diarias creadas).

## Decisiones

- Las notas mensuales viven en `06-Rutina\Mensual\` y se nombran por período: `Septiembre 2026.md`.
- Las notas semanales viven en `06-Rutina\Semanal\` y se nombran por período: `Semana 36.md`.
- Las notas diarias viven en `06-Rutina\Diario\` y se nombran por período: `9 de Septiembre.md`.
- La nota mensual enlaza al objetivo semestral correspondiente (`[[H1]]` / `[[H2]]`); las acciones individuales pueden enlazar además al objetivo concreto (`- [ ] Practicar improvisación sobre progresiones II-V-I ([[H2]])`).
- No duplicar objetivos dentro de Rutina; la relación se hace con enlaces internos hacia 01-Objetivos.
- Los niveles Mensual, Semanal y Diario pertenecen a Rutina dentro de la jerarquía temporal.
- No sobreestructurar: mantener el sistema simple hasta que exista una necesidad concreta por nivel.

### Estructura de las notas de Rutina (Fase 3.5, aprobada)

- **Escritura bajo protocolo de aprobación**: el agente propone y solo escribe tras aprobación explícita y puntual de cada escritura ("Aprobado. Escribí X con este contenido").
- **Formato de estado en texto plano, sin YAML**: `Estado: Abierta` al crear; `Estado: Cerrada` al cerrar.
- **Nota mensual** (`Mensual/<Mes Año>.md`): `Estado`, vínculo a `[[H1]]`/`[[H2]]`, `## Foco del mes`, `## Rutinas (protegidas)`, `## Prioridad de proyectos`, `## Otros asuntos`, `## Finanzas`.
- **Nota semanal** (`Semanal/Semana NN.md`): `Estado`, `## Foco de la semana`, `## Calendario`, `## Rutinas`, `## Acciones` (checkboxes, con enlace al objetivo cuando corresponda), `## Registro` (Hecho / No hecho / Extra / Nota; las secciones vacías se omiten).
- **Nota diaria** (`Diario/<día>.md`): estructura aprobada (template de referencia en `Diario/Plantilla de Daily.md`):
  - `## Recordatorios`: solo los de HOY. Fuente: `09-Calendario/Recordatorios/*` y avisos del usuario del día.
  - `## Próximos Eventos`: solo eventos de HOY. Fuente: `09-Calendario/*` (Eventos.md, Toques.md, Entregas.md).
  - `## Acciones`: acciones del día agrupadas por categoría únicamente para presentación/lectura — `### B2B LATAM`, `### Música`, `### La Ventolera` (tareas para la banda que no son musicales ni de desarrollo del proyecto web; "web" por sí sola no determina la categoría: desarrollo/funcionalidad/mantenimiento técnico → VentoleraApp, contenido/publicación/gestión del sitio → La Ventolera), `### Programación` (→ `#### Proyectos personales` con `##### AppFinanciera`, `##### Organizador Personal`, `##### VentoleraApp (webventolera)`, `##### Portfolio` y `#### Freelancer`), `### Finanzas` (solo Finanzas del Organizador; NO AppFinanciera), `### Ejercicio`, `### Otros`.
  - `## Notas del día`: bandeja de captura rápida durante el día (texto libre, sin checkboxes ni estructura adicional); no implica automáticamente una tarea. Al cierre del día cada nota se revisa individualmente y el usuario decide: convertirla en tarea/acción (→ `## Acciones`), en objetivo o idea futura (→ lugar correspondiente), trasladarla al lugar adecuado, o descartarla. Una vez resuelta, trasladada o descartada, la nota temporal se elimina de la daily cerrada. No es un registro histórico independiente ni requiere carpeta, YAML ni estructura nueva. No es responsabilidad automática del PLANIFICADOR: la decisión es del usuario durante el cierre. Si una nota se transforma en "ver esto mañana", se usa el mecanismo existente de recordatorio de la daily siguiente.
  - `## Registro`: cierre/registro del día.
  - `## Panorama de la semana` (al final): `### Recordatorios` (semana), `### Eventos` (semana), `### Objetivos semanales` (desde la nota Semanal). NO es una lista de acciones; no duplica la lista diaria.
  - **Secciones condicionales**: cada sección/subsección solo aparece si tiene contenido ese día; no se generan encabezados ni tablas vacías.
  - **Categorías no rígidas**: son una forma de presentar las acciones; no se crean entidades, carpetas ni sistemas de tareas para soportar esta presentación. Ante una acción ambigua no se inventa ni modifica categoría ni se fuerza en `Otros`: se consulta al usuario dónde colocarla.
- **Bloque de música en notas diarias**: en días con sesión de música, la nota diaria incluye `### Música (N.ª sesión de la semana)` que captura los datos de la sesión: tabla en blanco con filas por bloque (Nota larga, Registro Bajo, Flexibilidad, Cromáticos, Escalas, Arpegios, Progresiones armónicas, Tema de improvisación) y columnas `Bloque | Ej | Variación | Tempo | Min | Resultado`; más subsecciones `### Repertorio`, `### Observaciones` y `### Resumen de la sesión` (síntesis narrativa breve y opcional de cómo fue la sesión en conjunto: qué trabajé, cómo me sentí técnicamente, qué salió bien, qué costó, qué tener presente; no reemplaza `### Observaciones`, que sigue siendo para anotaciones puntuales), y el checkbox `- [ ] Cargar en [[Registro/<AAAA-MM-DD>]]`. El checkbox se tilda cuando la sesión quedó cargada en `02-Musica/Registro/<AAAA-MM-DD>.md`; el resumen se transcribe junto con el resto de la información musical al registro permanente. Mantiene la lógica existente de sesión semanal.
- **Bloque de ejercicio en notas diarias**: en días con sesión de ejercicio, la nota diaria incluye `### Ejercicio (N.ª sesión de la semana)` con la tabla `| Ejercicio | Series | Repeticiones | Observaciones |`, siguiendo la lógica de sesión semanal equivalente a Música. La sesión se transcribe al cierre del día a `05-Otros/Rutina de Ejercicio/Registro/<AAAA-MM-DD>.md` y se tilda el checkbox `- [ ] Cargar en [[Rutina de Ejercicio/Registro/<AAAA-MM-DD>]]` (misma lógica que la carga de música).
- **Bloque de nota psicológica en notas diarias**: la tarea de escribir nota psicológica va en `### Otros` (no se crea una categoría propia). Cuando la tarea está presente, la nota diaria incluye `### Nota Psicológica de hoy` como espacio de escritura libre (cómo me siento en el presente, qué me está pasando), con el checkbox `- [ ] Cargar en [[NotasPsicologicas/Registro/<AAAA-MM-DD>]]`. Al cierre del día el contenido se transcribe a `05-Otros/NotasPsicologicas/Registro/<AAAA-MM-DD>.md` (misma lógica que la carga de música). Frecuencia de escritura personal (~1–2 semanas); relectura mensual recordada por el Planner antes del cierre de mes.
- **Cierre de período**: se cambia `Estado: Abierta` por `Estado: Cerrada` y se agrega `## Resumen` al final (plan vs realidad y pendientes, para notas mensuales y semanales). Requiere aprobación explícita. Las notas cerradas son inmutables; cualquier corrección requiere aprobación explícita.
- **Traslados**: en el origen `→ trasladada a [[<Período>]]`; en el destino `(de [[<Período>]])`.

## Sin definir aún

- Vínculo superior de las notas semanales y diarias (qué nota u objetivo de nivel superior referencian a nivel de nota, si lo hacen).
- Uso futuro de plugins (Calendar, Tasks) para automatizar o enlazar las notas de rutina. Se menciona solo como posibilidad futura; no está aprobado su uso.