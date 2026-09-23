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
├── Partituras/
│   ├── Ejercicios/
│   └── Repertorio/
│       └── Ventolera/
├── Toques/
├── Registro/
│   ├── Plantilla de Sesion.md
│   └── <AAAA-MM-DD>.md
├── Clases/
└── Estadisticas/
    ├── Semanal/
    └── Mensual/
```

`Clases/` y `Estadisticas/` (Semanal/Mensual) existen como estructuras preparadas, sin contenido aún.

## Frecuencia

Base: **3 sesiones de estudio por semana** (referencia del sistema y del Planner). Pueden ocurrir 4 o más naturalmente, pero 3 es el objetivo base.

## Rutina

`Estudio/Rutina de Estudio del Instrumento.md` define cómo está estructurada una sesión: qué bloques la componen y en qué orden. `Estudio/Ejercicios.md` define los ejercicios concretos de cada bloque.

Orden estable de la rutina de estudio:

1. Nota larga
2. Registro Bajo
3. Flexibilidad
4. Cromáticos
5. Escalas
6. Arpegios
7. Progresiones armónicas
8. Tema de improvisación

El **tema de improvisación** se trabaja en tres pasadas: **Pasada 1 — Acordes**, **Pasada 2 — Melodía**, **Pasada 3 — Improvisación**.

Estado actual de los ejercicios: Escalas y Arpegios en **Mayores 7**; Progresiones armónicas en II-V-I (sin ejercicios cargados todavía).

El sistema registra cambios de ejercicios/modalidades pero **no decide por sí mismo** cuándo cambiar la rutina. Los cambios ocurren porque el ejercicio está procesado/dominado o porque el profesor lo indica.

## Cómo funciona

### Estudio / Ejercicios

- `Estudio/Rutina de Estudio del Instrumento.md` = nota base que describe la rutina en sí. El texto se actualiza cuando cambian los ejercicios.
- `Estudio/Ejercicios.md` = nota general con los ejercicios organizados por área (Nota larga, Registro Bajo, Flexibilidad, Cromáticos, Escalas, Arpegios, Progresiones armónicas, Tema de improvisación), en tabla o estructura organizada.
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

### Partituras

- `Partituras/Ejercicios/` y `Partituras/Repertorio/Ventolera/` están separadas: ejercicios (material técnico) vs. repertorio del proyecto Ventolera.

### Clases

- La carpeta `Clases/` está creada como estructura preparada, sin contenido aún.
- Comienzan en octubre. No se crea una arquitectura compleja: funciona como **fuente de modificaciones/indicaciones** para la rutina (ejercicios, modalidades, objetivos, tempos, indicaciones).
- El sistema no aplica cambios automáticos; al comenzar las clases se integra esa información en el contexto.

### Registro de sesión

- Una nota independiente por cada sesión: `Registro/<AAAA-MM-DD>.md`.
- La plantilla única de la sesión es `Registro/Plantilla de Sesion.md`: sigue el orden de la rutina (los 8 bloques, con ejercicio, variación, tempo, duración, resultado y observación por bloque), incluye el **Tema de improvisación** en sus 3 pasadas, las secciones de **Repertorio** y **Nota** (Observaciones generales) y un **Resumen de la sesión** (síntesis narrativa breve y opcional de cómo fue la sesión en conjunto; no reemplaza las observaciones puntuales). Estructura final: `## Sesión` → `## Rutina` → `## Repertorio` → `## Nota` → `## Resumen de la sesión`.
- El registro debe permitir identificar **qué ejercicio/modalidad se utilizó** en cada momento histórico, para que el histórico no quede ambiguo cuando cambien los ejercicios.
- La nota diaria de `06-Rutina/Diario/<día>.md` incluye el bloque `## Música` con una tabla como captura temporal de la sesión; los datos se transcriben luego a `Registro/<AAAA-MM-DD>.md`. El bloque diario incluye `### Repertorio`, `### Observaciones` y `### Resumen de la sesión`, y el resumen se transcribe al registro permanente junto con el resto de la sesión. La diaria es captura temporal; `Registro/` es el registro permanente.

### Estadísticas

- Resumen semanal persistente: `Estadisticas/Semanal/<AÑO-S#>.md` (p. ej. `2026-S40.md`)
- Resumen mensual persistente: `Estadisticas/Mensual/<AAAA-MM>.md` (p. ej. `2026-10.md`)
- Las carpetas `Estadisticas/Semanal/` y `Estadisticas/Mensual/` están creadas como estructura preparada; los resúmenes se generan con datos reales al usarlas.
- Pueden mostrar: cantidad de sesiones, días practicados, tiempo total, promedio por sesión, ejercicios realizados, cumplimiento de cada parte de la rutina, evolución de tempos, evolución del repertorio y cambios de ejercicios/modalidades del período.
- Sirven para **detectar tendencias y ajustar la práctica**, no para evaluar ni castigar.
- No inventar métricas que no puedan obtenerse de los registros.

### Toques y Calendario

- `Toques/` aloja únicamente los toques que requieren preparación musical / repertorio definido; su calendario vive en `09-Calendario/Toques.md`.
- El repertorio por toque se registra dentro de la nota del toque, solamente cuando corresponda, dividido en **Repaso** y **Nuevo**.
- Fiesta Ventolera (proyecto musical) es independiente de VentoleraApp (programación, `03-Programacion/Proyectos Personales`).

### Ensayos

- Ensayo semanal con Ventolera: **jueves de 19:30 a 22:00**, salvo cancelación (lo avisa el usuario).
- Es **independiente** de la rutina de 3 sesiones de estudio semanales (estudio = técnica, improvisación y repertorio).
- El **repertorio** es lo único que influye en los toques; el estudio de repertorio y el ensayo **van de la mano** (lo que se estudia de repertorio se ve en el ensayo).
- Si un ensayo requiere estudiar repertorio específico, el usuario lo comunica.

## Planner y Música

- El Planner solo necesita conocer: el **objetivo base de 3 sesiones**, ensayos, toques, compromisos musicales y acciones de repertorio necesarias para eventos (cuando un evento lo requiera).
- El Planner **NO necesita** conocer: detalle de cada ejercicio, tempos, duración individual por ejercicio ni historial técnico. Esa información permanece en Música.
- El Planner coordina **cuándo proteger la práctica**; Música registra **qué ocurrió** durante ella.
- Al abrir una semana nueva, el Planner pregunta por los ensayos (cancelaciones o cambios). El ensayo del jueves se incluye en la planificación semanal y en la daily del jueves.

## Decisiones

- Frecuencia base: **3 sesiones por semana**.
- Separación conceptual: Estudio / Partituras / Toques / Registro / Clases / Estadísticas.
- No mezclar ejercicios de estudio con partituras de repertorio (aunque ambos puedan usar PDFs).
- Una única nota general de ejercicios (`Estudio/Ejercicios.md`).
- Una nota de registro por sesión (`Registro/<AAAA-MM-DD>.md`).
- Resúmenes semanales y mensuales persistentes en estadísticas.
- El sistema registra pero no decide el cambio de ejercicios/modalidades.
- Ensayo de Ventolera: jueves 19:30–22:00, aparte de las 3 sesiones de estudio. Solo el repertorio incide en los toques; ensayo y estudio de repertorio van de la mano.

## Sin definir aún

- Detalles concretos de las clases (contenido, frecuencia, seguimiento) hasta que comiencen en octubre.
- Sistema de seguimiento concreto del repertorio más allá de los estados mínimos.
- Formato exacto de las estadísticas semanales/mensuales (se define al usarlas con datos reales, Fase 5).
- Estructura de ensayos/grabaciones futuras.

### Evolución futura (ideas abiertas, NO son decisiones)

- Posible sistema para registrar grabaciones/proyectos de producción de la banda (Fase 6 o posterior).
- No está aprobado implementarlo aún.