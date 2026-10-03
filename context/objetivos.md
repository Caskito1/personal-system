# Contexto - Objetivos

## Propósito

Representa qué quiero conseguir y hacia dónde voy. Es el primer eslabón de la cadena **Objetivos → Rutina → Revisión → Planificación**: define el destino, mientras que 06-Rutina define y registra las acciones para llegar.

## Ubicación

Carpeta del Vault: `01-Objetivos`

Estructura actual:

```
01-Objetivos/
└── 2026/
    ├── Objetivos Anuales.md
    ├── H1.md
    └── H2.md
```

## Cómo funciona

- Jerarquía conceptual: Anual → Semestral → Mensual → Semanal → Diario.
- Los niveles Mensual, Semanal y Diario NO se duplican aquí: viven principalmente en 06-Rutina y se vinculan mediante enlaces internos.
- Una carpeta por año (2026, 2027, …). Cada año nuevo, crear su carpeta.
- Dentro de cada año: una nota anual (`Objetivos Anuales.md`) y una nota por semestre (`H1.md` = primer semestre, `H2.md` = segundo semestre).
- **La nota anual es a la vez el objetivo del año y el lugar donde queda escrita su evaluación y sus decisiones.** Al cerrarse el año, esta nota suma la evaluación por línea, las decisiones del cierre y la proyección al año siguiente.
- **El nivel anual forma parte de la cadena de revisión** Daily → Semana → Mes → Año → siguiente año (ver `context/rutina.md` y `context/agentes.md`).
- Estado actual: `H2.md` tiene contenido real; `Objetivos Anuales.md` tiene el objetivo anual 2026 y aloja la evaluación de cierre; `H1.md` es un registro explícito de que el primer semestre no se utilizó y no tiene objetivos.

## Decisiones

- Incluir inicialmente solo la carpeta `2026` (2027+ se crean cuando corresponda).
- `H1` = primer semestre; `H2` = segundo semestre.
- No duplicar la jerarquía Mensual/Semanal/Diario dentro de Objetivos; ese nivel corresponde a Rutina.
- La relación entre Rutina y Objetivos se hará con enlaces internos de Obsidian, sin duplicar el contenido de los objetivos.
- El modelo general del sistema está documentado en `context/arquitectura.md`: la cadena **Objetivos → Rutinas/Proyectos → Planificación → Ejecución → Revisión** es una precisión conceptual de la cadena existente, no una implementación nueva.
- La nota mensual de Rutina enlaza al objetivo semestral correspondiente (`[[H1]]` / `[[H2]]`); las acciones individuales pueden enlazar al objetivo concreto que corresponda.

## Estado de los objetivos

- Cada objetivo se marca como **Cumplido**, **Parcial** o **No cumplido**.
- El estado **nunca va solo**: cada objetivo lleva **motivo**, **aprendizaje o hallazgo relevante** y **decisión para 2027**.
- Un objetivo **no alcanzado no desaparece ni se copia automáticamente** al año siguiente. La decisión de trasladarlo, modificarlo, abandonarlo o reemplazarlo surge de la conversación de cierre del año y queda registrada en la nota anual.
- Los objetivos no alcanzados se registran en su propia tabla dentro de la nota anual del año cerrado.

## Sin definir aún

- Si las notas semanales y diarias de Rutina llevan vínculo propio a un objetivo a nivel de nota (la mensual ya enlaza al semestral; las acciones ya pueden enlazar al objetivo concreto).