# Contexto - Música

## Propósito

Área de organización musical: estudio técnico del instrumento, repertorio, clases, registros de práctica y estadísticas. Distingue los ejercicios de estudio (material técnico) de las partituras de repertorio (canciones), y registra qué se practica sin juzgar ni penalizar.

## Ubicación

Carpeta del Vault: `02-Musica`

Estructura:

```
02-Musica/
├── Estudio/
│   ├── Rutina de Estudio del Instrumento.md
│   └── Ejercicios.md
├── Repertorio/
├── Clases/
├── Registro/
│   └── <AAAA-MM-DD>.md
├── Estadisticas/
│   ├── Semanal/
│   │   └── 2026-S40.md
│   └── Mensual/
│       └── 2026-10.md
├── Partituras/
└── Toques/
```

## Frecuencia

Base: **3 sesiones de estudio por semana** (referencia del sistema y del Planner). Pueden ocurrir 4 o más naturalmente, pero 3 es el objetivo base.

## Rutina

Orden estable de la rutina de estudio:

1. Nota larga
2. Flex
3. Cromatismos
4. Escalas
5. Arpegios
6. Tema de estudio

El **tema de estudio** puede incluir: progresión armónica, melodía e improvisación.

El sistema registra cambios de ejercicios/modalidades pero **no decide por sí mismo** cuándo cambiar la rutina. Los cambios ocurren porque el ejercicio está procesado/dominado o porque el profesor lo indica.

## Cómo funciona

### Estudio / Ejercicios

- `Estudio/Rutina de Estudio del Instrumento.md` = nota base que describe la rutina en sí. El texto se actualiza cuando cambian los ejercicios.
- `Estudio/Ejercicios.md` = nota general con los ejercicios organizados por área (Nota larga, Flex, Cromatismos, Escalas, Arpegios, Tema de estudio), en tabla o estructura organizada.
- No existe una nota independiente por cada ejercicio.
- Columnas/estructura de `Ejercicios.md`: ejercicio, modalidad, objetivo, tempo, PDF (referencia cuando corresponda), estado, observaciones e historial de cambios.
- Los ejercicios van a crecer y evolucionar: cuando un ejercicio cambia, se registra el cambio y **se mantiene el anterior como histórico** (no se sobrescribe la historia). El registro de la fecha de cambio preserva qué modalidad era la vigente en cada momento.
- Los PDFs de ejercicios son **material técnico**; las partituras son **repertorio**. No mezclarlos.

### Repertorio

- Separado de la rutina de estudio.
- Relacionado con: ensayos, toques y futuros proyectos/grabaciones.
- Los temas actuales ya están aprendidos y memorizados.
- Los temas nuevos se registran y se relacionan con ensayo, toque y estado de aprendizaje.
- Estados mínimos: **En preparación** / **Aprendido**.
- No se construye todavía un sistema complejo de grabaciones.

### Clases

- Comienzan en octubre. No se crea una arquitectura compleja: funciona como **fuente de modificaciones/indicaciones** para la rutina (ejercicios, modalidades, objetivos, tempos, indicaciones).
- El sistema no aplica cambios automáticos; al comenzar las clases se integra esa información en el contexto.

### Registro de sesión

- Una nota independiente por cada sesión: `Registro/<AAAA-MM-DD>.md`.
- Formato:

```
# <AAAA-MM-DD>

## Sesión
- Duración total: <min>

## Rutina
- Nota larga: ✅ | <min> | <tempo>
- Flex: ✅ | <min> | <tempo>
- Cromatismos: ✅ | <min> | <tempo>
- Escalas: ✅ | <min> | <tempo>
- Arpegios: ✅ | <min> | <tempo>
- Tema de estudio: ✅ | <min> | <tempo>

## Nota
<opcional>
```

- Los ejercicios pueden indicarse junto a cada área de la rutina cuando se requiera precisión.
- El registro debe permitir identificar **qué ejercicio/modalidad se utilizó** en cada momento histórico, para que el histórico no quede ambiguo cuando cambien los ejercicios.

### Estadísticas

- Resumen semanal persistente: `Estadisticas/Semanal/<AÑO-S#>.md` (p. ej. `2026-S40.md`)
- Resumen mensual persistente: `Estadisticas/Mensual/<AAAA-MM>.md` (p. ej. `2026-10.md`)
- Pueden mostrar: cantidad de sesiones, días practicados, tiempo total, promedio por sesión, ejercicios realizados, cumplimiento de cada parte de la rutina, evolución de tempos, evolución del repertorio y cambios de ejercicios/modalidades del período.
- Sirven para **detectar tendencias y ajustar la práctica**, no para evaluar ni castigar.
- No inventar métricas que no puedan obtenerse de los registros.

### Toques y Calendario

- Los eventos de toques viven en `02-Musica/Toques` y su calendario en `09-Calendario/Toques.md`.
- Fiesta Ventolera (proyecto musical) es independiente de VentoleraApp (programación, `03-Programacion/Proyectos Personales`).

## Planner y Música

- El Planner solo necesita conocer: el **objetivo base de 3 sesiones**, ensayos, toques, compromisos musicales y acciones de repertorio necesarias para eventos (cuando un evento lo requiera).
- El Planner **NO necesita** conocer: detalle de cada ejercicio, tempos, duración individual por ejercicio ni historial técnico. Esa información permanece en Música.
- El Planner coordina **cuándo proteger la práctica**; Música registra **qué ocurrió** durante ella.

## Decisiones

- Frecuencia base: **3 sesiones por semana**.
- Separación conceptual: Estudio / Repertorio / Clases / Registro / Estadísticas / Partituras / Toques.
- No mezclar ejercicios de estudio con partituras de repertorio (aunque ambos puedan usar PDFs).
- Una única nota general de ejercicios (`Estudio/Ejercicios.md`).
- Una nota de registro por sesión (`Registro/<AAAA-MM-DD>.md`).
- Resúmenes semanales y mensuales persistentes en estadísticas.
- El sistema registra pero no decide el cambio de ejercicios/modalidades.

## Sin definir aún

- Detalles concretos de las clases (contenido, frecuencia, seguimiento) hasta que comiencen en octubre.
- Sistema de seguimiento concreto del repertorio más allá de los estados mínimos.
- Formato exacto de las estadísticas semanales/mensuales (se define al usarlas con datos reales, Fase 5).
- Estructura de ensayos/grabaciones futuras.

### Evolución futura (ideas abiertas, NO son decisiones)

- Posible sistema para registrar grabaciones/proyectos de producción de la banda (Fase 6 o posterior).
- No está aprobado implementarlo aún.