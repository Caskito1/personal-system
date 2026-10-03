# Contexto - Adquisiciones

## Propósito

Espacio donde viven las cosas que quiero comprar, o investigar para comprar. Una adquisición no implica compromiso de compra ni se convierte automáticamente en una tarea: `Lista de Compras.md` es el inbox de ideas activas, que se revisa por períodos.

## Ubicación

Carpeta del Vault: `08-Adquisiciones`

Estructura actual:

```
08-Adquisiciones/
├── Lista de Compras.md
├── Auriculares.md
├── Bandeja para Teclado.md
├── Cafetera.md
├── Celular.md
├── Championes.md
├── Juguete para el Gato.md
└── Luz para Plantas.md
```

- `Lista de Compras.md` es la **fuente única operativa**: ahí viven los estados y los datos operativos.
- Las notas individuales de `08-Adquisiciones` solo aportan detalle adicional y se enlazan con `[[...]]` cuando tienen información útil.
- La integración con los períodos está definida en `context/rutina.md` (estructura de las notas) y `context/agentes.md` (comportamiento del PLANIFICADOR).

## Cómo funciona

Ciclo: **Idea → inclusión mensual → investigación en una Semana X → ejecución mediante Dailys → decisión → compra / descartada / espera / nueva investigación.**

- **Idea**: está en la lista y no tiene trabajo asignado. No genera tareas.
- **Inclusión mensual**: al revisar el mes se lee el listado completo de ideas activas y el usuario decide cuáles quiere desarrollar, cuáles dejar en espera y cuáles descartar. La inclusión es siempre decisión explícita del usuario. Una idea que aparece durante el mes también puede entrar, pero solo si él lo indica.
- **Investigación**: al desarrollar una adquisición se le asigna una **semana concreta** (ej. Celular → Semana 41). La unidad de planificación es la semana, no las horas ni las sesiones. Esa investigación entra en la nota semanal y luego se traduce en acciones concretas en los Dailys.
- **Investigación completa**: significa que ya hay información suficiente para **decidir**. No significa que haya que comprar ni genera tareas por sí sola. Si la información no alcanza, la adquisición vuelve a la planificación semanal con una nueva semana: **nada se arrastra automáticamente**.
- **Decisión**: al terminar la investigación el usuario decide entre comprar, descartar, esperar o seguir investigando.
- **Listo para comprar**: la decisión de compra está tomada y falta ejecutarla. Tiene **seguimiento semanal** hasta que se compre, se postergue o se descarte. La fecha de compra puede ser concreta o tentativa. Si se posterga, el ítem vuelve a `Estado: En desarrollo`.
- **Esperar**: el ítem queda en `Estado: En desarrollo` **sin** semana de investigación asignada. La espera no crea un estado ni una etapa nueva: simplemente no tiene trabajo semanal y reaparece en la revisión mensual.
- **Descartada**: pasa a la sección `## Descartadas` conservando su registro. No se elimina nada.

### Dónde vive cada cosa

| Nivel | Dónde | Qué hace |
|---|---|---|
| Inventario | `Lista de Compras.md` | Estado oficial y datos operativos |
| Mensual | Revisión del listado en la conversación de planificación | El usuario decide qué desarrollar, qué esperar y qué descartar |
| Semanal | `06-Rutina/Semanal/Semana NN.md` → bloque de Adquisiciones | Semana de investigación asignada y seguimiento de `Listo para comprar` |
| Daily | `06-Rutina/Diario/<día>.md` → `### Adquisiciones` | Solo acciones concretas del día |
| Calendario | `09-Calendario/Recordatorios.md` | Solo el recordatorio concreto de compra |

La nota mensual **no lleva una sección propia** de Adquisiciones: cada resultado posible ya tiene destino. Desarrollar se escribe en la semana siguiente; descartar se escribe en la lista; esperar no requiere escritura, porque la ausencia de semana asignada *es* la espera.

## La puerta de compra

- Solo `Listo para comprar` genera acción o recordatorio de compra.
- `Idea` no genera acción de compra.
- `En desarrollo` con fecha tentativa es contexto orientativo, no compromiso automático.
- `Comprado` es registro, no acción.
- El recordatorio concreto de compra vive en `09-Calendario/Recordatorios.md`; el estado **no** se duplica en el calendario.
- Leer la lista no convierte las adquisiciones en tareas.

## Límite con Finanzas

Adquisiciones registra **qué quiero comprar**. Finanzas registra **cuánta plata tengo y a dónde va**. Ejecutar la compra es una acción de Adquisiciones; su impacto en el dinero es un asunto de Finanzas.

## Decisiones

- `Lista de Compras.md` es la fuente única operativa de Adquisiciones.
- Los estados son cuatro y no se agregan más: `Idea` (considerada, todavía sin desarrollo suficiente), `En desarrollo` (investigación, comparación, preparación o adquisición desarrollada que queda en espera), `Listo para comprar` (decisión de compra tomada, falta ejecutar) y `Comprado` (compra realizada).
- La etapa de investigación **no es un campo**: es un concepto del flujo, no un dato persistente. El ciclo queda representado por el Estado más la planificación mensual y semanal.
- La espera no es un estado ni una etapa/campo: un ítem en espera está en `En desarrollo` y sin semana de investigación asignada.
- La unidad de planificación de la investigación es la **semana**, no las horas ni las sesiones.
- La investigación no se arrastra automáticamente entre semanas.
- El Daily no muestra el inventario de adquisiciones: solo acciones concretas.
- No hay tope de adquisiciones en el Daily.
- Los descartes se conservan; no se elimina información.
- El detalle de la integración con los períodos y el comportamiento de los agentes están en `context/rutina.md` y `context/agentes.md`.

## Sin definir aún

- Si la lista de ideas activas crece mucho: cómo ajustar la revisión mensual (cambiar su cadencia, acotarla o subcontractarla).
- Automatización o integración con Calendar/Tasks (fase posterior, no aprobada).
