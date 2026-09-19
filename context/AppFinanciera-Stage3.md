# AppFinanciera — Stage 3 (Diseño) — Documento de coordinación

Documento de coordinación de `personal-system` para el proyecto AppFinanciera. Fuente única para retomar la Etapa 3 en una futura sesión, sin rehacer el análisis.

## Estado del documento

- **Etapa 2 (Auditoría): completada.** La auditoría fue read-only (`REPORT-02.md` en el repo de AppFinanciera) y no modificó código ni datos.
- **Etapa 3 (Diseño): EN REVISIÓN. NO APROBADO.**
  - El diseño incluye **solo propuesta** (sección 2). No es alcance implementado ni aprobado.
  - Faltan resolver las preguntas P1–P8 (sección 3) y la revisión del usuario.
- **Etapa 4 (Implementación): NO aprobada** y fuera de alcance hasta que el diseño esté revisado y aprobado.
- Regla de flujo: **LEER → ANALIZAR → DISEÑAR → PROPONER → USUARIO DECIDE → PLANIFICAR → USUARIO APRUEBA → EJECUTAR**.
- **`HANDOFF-03.md`: NO se ha generado.** Se generará solo después de que el diseño sea revisado y aprobado, como instrucciones para llevar el diseño al repo de AppFinanciera.
- Regla permanente de despliegue (para cuando haya implementación): **Local → Staging → Producción → Verificación**. Nunca asumir terminado solo porque funciona localmente; verificar tras producción; no modificar producción directamente.
- Relación con el Organizador: AppFinanciera es un proyecto separado. El Organizador coordina, prioriza, analiza, propone, registra decisiones y controla estado. AppFinanciera implementa, prueba, modifica código, trabaja sobre Firestore y genera sus propios reportes. El cierre de Finanzas del Organizador **no implica terminar AppFinanciera como producto**.

---

## 1. Memoria de la sesión — uso real y visión de AppFinanciera

Fuente: documento de contexto proporcionado por el usuario (sesión 19/09/2026). Es la **fuente de verdad sobre uso real y visión**. La auditoría describe el código; este documento describe la realidad.

### 1.1 Propósito de la sesión

- `REPORT-02` (auditoría de Stage 2) generado y revisado, read-only, sin cambios en código ni datos.
- Objetivo: dejar registrado el **contexto real de uso** y la **visión futura** de AppFinanciera, para que la próxima sesión arranque directamente con el **diseño de Stage 3**.
- **No implementar Stage 3 todavía.** Primero consolidar contexto, analizar el modelo actual y diseñar. La implementación solo comienza después de que el diseño sea revisado y aprobado.

### 1.2 Dos dimensiones de AppFinanciera (mantener separadas)

- **Uso actual (hoy):** herramienta financiera usada hoy → registrar ingresos, registrar gastos, manejar gastos fijos, manejar gastos compartidos, visualizar información financiera, llevar el balance de determinados gastos compartidos.
- **Visión futura (largo plazo):** aplicación general que otras personas puedan descargar → crear cuenta; crear grupos; compartir gastos; definir cómo se dividen determinados gastos; configurar gastos fijos; registrar productos; estadísticas por producto/categoría; manejar tarjetas; manejar préstamos/adelantos; manejar distintos tipos de gastos compartidos; configurar el comportamiento financiero del grupo.
- **La visión futura NO es alcance de Stage 3. No asumir que todo debe implementarse ahora.**

### 1.3 Uso real actual

- Dos personas usando la app, cada una con su cuenta.
- Áreas principales: ingresos, gastos, gastos fijos, gastos compartidos, visualización.
- **Ingresos existentes:** Sueldo (trabajo fijo mensual), Bandas (actuaciones), Freelance.
- Freelance se registra correctamente, pero tiene un **problema en la visualización** (bug). Ese problema es trabajo a revisar pero **no debe confundirse con el modelo conceptual de ingresos**.

### 1.4 Gastos fijos compartidos (SÍ generan balance real)

- Ejemplos: alquiler, electricidad, agua, suscripciones, otros recurrentes.
- Pueden ser **personales** o **compartidos**.
- Hoy los compartidos se manejan **50/50**.
- Cuando se registra una factura: se registra el gasto → se registra quién lo pagó → se determina cuánto corresponde a cada persona → se acumula el balance → la persona que debe ve a quién debe → al realizar el pago/ajuste el balance queda saldado.
- **Este mecanismo sí genera una deuda/balance real**, específico de los gastos fijos compartidos.
- **Cierre mensual:** en la práctica los balances se resuelven. La app debe **conservar el historial aunque el balance termine en cero**. No asumir que debe eliminarse el histórico al cerrar el mes.
- Diferencia conceptual que debe existir: **histórico de lo ocurrido** vs **balance actualmente pendiente**.

### 1.5 Configuración futura de porcentajes

- Hoy el uso es 50/50. Convendría que el **modelo interno no quede limitado a 50/50** (futuro: 50/50, 60/40, 70/30…).
- La interfaz actual puede seguir mostrando 50/50.
- Al diseñar Stage 3, analizar si la **estructura de datos ya es compatible** con el concepto.
- Regla: **modelo suficientemente flexible, interfaz sencilla.**

### 1.6 Gastos diarios compartidos (NO generan balance — especialmente importante)

- Un gasto diario puede ser:
  - **Personal** → solo pertenece al usuario que lo registra.
  - **Compartido** → visible para ambas personas (ej.: compra en supermercado con productos del hogar).
- El gasto compartido sirve como: registro, historial, información para ambos y dato para visualización. **NO genera deuda ni balance entre las personas.** Es **intencional**.
- No mostrar de forma constante "Debés $X" por cada gasto diario compartido ni generar sensación de deuda en el uso cotidiano.
- **En el grupo actual nunca se utilizará el balance para gastos diarios compartidos.**
- La estructura general puede contemplar que otros grupos/usuarios quieran usar balance → debe ser un **posible ajuste de configuración, no una obligación**.
- No convertir esto en deuda visible en el visualizador actual.

### 1.7 Gastos extraordinarios compartidos / dinero a recuperar (caso diferente)

- Ejemplos: compro un mueble para la casa y corresponde dividirlo 50/50; yo pago todo; mi pareja luego me devuelve su parte. O compro una entrada para un amigo que me devuelve posteriormente su parte.
- **No deben registrarse como "ingreso personal".** El dinero recibido posteriormente es una **recuperación de dinero adelantado / reintegro / settlement**, no un ingreso nuevo.
- Debe existir **conceptualmente una categoría o módulo diferente para "dinero a recuperar de otra persona"**, aplicable a: pareja, amigo, familiar u otra persona del grupo.
- Es diferente de: ingreso; gasto diario compartido sin balance; gasto fijo compartido.
- **Analizar durante Stage 3 cuál es la mejor forma de modelarlo. No asumir todavía el nombre técnico definitivo.**

### 1.8 Tarjeta de crédito

- Hoy **no está implementada como módulo específico**.
- Funcionamiento real actual: se utiliza la tarjeta → posteriormente se revisan los gastos → se determina qué parte corresponde a la otra persona → se realiza el ajuste manual.
- Debería evolucionar eventualmente hacia un **módulo propio de tarjeta** (no necesariamente con integración bancaria).
- Objetivo del módulo: representar correctamente gastos realizados con tarjeta, quién realizó el gasto, qué parte corresponde a otra persona, cuánto queda por recuperar y pagos/ajustes posteriores.
- **No tratar la devolución de la parte de la tarjeta como ingreso.** Debe formar parte del modelo de recuperaciones/settlements.

### 1.9 Transferencias actuales

- La colección/lógica de `transferencias` hallada en la auditoría corresponde a **un intento anterior** de implementar este concepto.
- **Actualmente no se utiliza.** No debe considerarse funcionalidad central del modelo financiero actual.
- Analizar si corresponde: marcarla como obsoleta; retirar progresivamente su uso; limpiar la lógica asociada; o mantenerla temporalmente por compatibilidad histórica.
- **No construir Stage 3 alrededor de esta funcionalidad.**

### 1.10 Configuración futura de la aplicación (idea de producto)

- Idea: una sección de configuración (posiblemente accesible con una "ruedita") donde el grupo/usuario configure cómo utilizar determinadas funcionalidades. Ejemplos: porcentaje de división de gastos compartidos (50/50, 60/40…); mostrar balance o no; activar/desactivar comportamientos; editar gastos fijos; configurar participantes; otras reglas financieras del grupo.
- Permite un modelo general flexible sin obligar a todos los usuarios a usar todas las funcionalidades.
- **Grupo actual (ejemplo conceptual):** gastos diarios compartidos sin balance; gastos fijos compartidos 50/50 + balance; recuperaciones activas; tarjeta futura.
- **Otro grupo (ejemplo hipotético):** 60/40; balances activos para compartidos; otros participantes; otra configuración.
- **Es visión de producto futura. No implementar toda esta configuración ahora.**

### 1.11 Visualizador

- Debe respetar las **diferencias semánticas entre los tipos de movimiento**.
- Interesa visualizar: gastos personales; gastos diarios compartidos; gastos fijos personales; gastos fijos compartidos; ingresos reales.
- **No** convertir automáticamente todos los movimientos compartidos en deuda. Especialmente: **gasto diario compartido ≠ deuda** y **reintegro/recuperación ≠ ingreso**.
- El diseño de Stage 3 debe tener estas diferencias conceptuales presentes.

### 1.12 Firestore y acceso read-only

- Puede ser útil que el trabajo tenga acceso de **solo lectura** a Firestore para: inspeccionar la estructura real de las colecciones; observar documentos reales; entender cómo están representados los grupos, usuarios y relaciones; detectar inconsistencias entre modelo teórico y datos reales; validar el diseño; comprender el impacto de los cambios.
- **Solo si aporta valor real** al diseño/análisis. **No dar acceso de escritura.** No modificar datos reales desde el agente.
- Si no aporta una diferencia significativa respecto de la información ya disponible, **no implementarlo solo por tenerlo**.

### 1.13 Datos reales (cuestiones a analizar)

Identificadas en la auditoría; deben analizarse con el uso real:
- Visualización incorrecta de Freelance.
- Diferencias entre modelos de gastos compartidos.
- Reintegros actualmente contabilizados como ingresos.
- Estructura de gastos fijos.
- Posibles duplicaciones.
- Lógica antigua de transferencias.
- Diferencias entre datos reales y modelo conceptual.

- **Priorizar la corrección semántica del modelo antes que agregar funcionalidades.** El objetivo no es una app más compleja; es que los datos representen correctamente lo que realmente sucede.

### 1.14 Principio de diseño

> La aplicación debe poder representar correctamente la realidad financiera sin obligar al usuario a utilizar toda la complejidad disponible.

- El modelo puede ser flexible; la configuración puede ser futura; el usuario actual puede utilizar solo una parte; el visualizador debe mostrar solo información útil; no generar deuda artificial; no convertir recuperaciones en ingresos; no construir funcionalidades solo porque técnicamente son posibles.

### 1.15 Alcance de Stage 3

- La próxima conversación debe comenzar por **DISEÑAR Stage 3** (no por modificar código). Secuencia:
  1. Leer `REPORT-02.md`.
  2. Leer el contexto actual del proyecto.
  3. Incorporar toda la información de este documento.
  4. Comparar la auditoría técnica con el uso real.
  5. Identificar diferencias entre: modelo actual / modelo deseado / funcionalidades futuras.
  6. Definir qué debe corregirse.
  7. Definir qué debe mantenerse.
  8. Definir qué debe quedar obsoleto.
  9. Definir qué debe posponerse.
  10. Diseñar el modelo conceptual de datos.
  11. Determinar qué cambios mínimos necesita la aplicación.
  12. Determinar si el acceso read-only a Firestore aporta valor.
  13. Presentar una propuesta de Stage 3 para aprobación.
- No implementar hasta que la propuesta sea aprobada.

### 1.16 Criterio para cerrar Stage 3

- No basta con código funcionando. Debe quedar claro: qué representa cada tipo de movimiento; qué genera balance; qué no; qué es ingreso; qué es gasto; qué es recuperación; cómo funcionan los gastos fijos; cómo funciona el histórico; cómo se representa una deuda real; qué parte es específica del grupo actual; qué parte es del modelo general de la aplicación.
- Meta: dejar una **base suficientemente correcta** para pasar a implementación y posteriormente usar datos reales con confianza.

### 1.17 Regla permanente de despliegue

- **Local → Staging → Producción → Verificación.** Nunca asumir que una modificación está terminada solo porque funciona localmente. Verificar que el comportamiento real es correcto después de producción. No modificar producción directamente.

### 1.18 Relación con el Organizador Personal

- AppFinanciera es un proyecto separado.

| Organizador (coordina, define prioridades, analiza, propone, registra, controla estado) | AppFinanciera (implementa, prueba, modifica código, trabaja sobre Firestore, genera sus reportes) |
|---|---|

- El cierre de Finanzas del Organizador **no implica terminar AppFinanciera como producto**. Alcanzado el mínimo necesario para que el Organizador use datos financieros confiables, la app puede continuar desarrollándose como producto independiente.

### 1.19 Próximo paso (acordado)

- **No empezar programando.** Arrancar por el diseño de Stage 3 con este contexto y `REPORT-02.md` como base.

---

## 2. Fase A — Propuesta de diseño de Stage 3 (BORRADOR, NO aprobado)

Producida por la sesión de coordinación del 19/09/2026. **Requiere respuesta a P1–P8 y aprobación del usuario.** La implementación queda fuera hasta que esto se apruebe.

### 2.1 Tabla de contraste `hallazgo → uso real → decisión`

| # | Hallazgo (REPORT-02) | Impacto real (contexto de sesión) | Decisión propuesta |
|---|---|---|---|
| H1 | Gastos de `gastos` compartidos nunca se dividen; "Tu parte" muestra lo pagado, no la parte. | Coincide con la realidad: el gasto diario compartido **no debe dividirse ni generar deuda** (intencional). Los **totales del mes** quedan distorsionados (el que paga carga el monto completo). | El modelo confirma la semántica "registro sin balance". **Pendiente de decisión (P1)**: qué mostrar como total del mes para gastos diarios compartidos. |
| H2 | Gastos fijos compartidos siempre **50/50 fijo**; `registrarPago` elige `members[0]`. | Coincide con la realidad: fijos compartidos = 50/50 **+ balance real**. El mecanismo es correcto; lo defectuoso es la rigidez. | Mantener balance para fijos compartidos; hacer el **modelo compatible con divisiones flexibles** (partes por participante) sin cambiar la interfaz 50/50. |
| H3 | Reintegros/transferencias recibidas **suman a ingresos** sin contra-partida. | Contradice la realidad: el dinero recibido de otro es **recuperación de dinero adelantado, NO ingreso**. La lógica de transferencias está en desuso. | Crear concepto **"recuperación / dinero a recuperar"** que no toque ingresos. Transferencias → tratamiento sección 2.5. |
| H4 | Bug freelance: se rotula por `subtipo` en vez de `tipo`; ids de banda inconsistentes; tipo `otros` sin sección. | Confirmado: "Freelance se registra correctamente, pero hay un problema de visualización". | **Corrección necesaria** (visualización, no modelo). Decisión (P2) sobre el tipo `otros`. |
| H5 | Doble taxonomía de gastos fijos; el catálogo activo perdió "otros". | La realidad usa categorías de fijos (alquiler, luz, agua, suscripciones). No queda claro qué productos reales existen. | Definir **catálogo único** en el diseño; decidir si "otros"/productos custom se mantienen. |
| H6 | Dos lógicas de "compartido" bajo la misma etiqueta. | No es inconsistencia: son **dos conceptos intencionalmente distintos** (diario sin balance vs fijo con balance). | **Formalizar la diferencia semántica** en el modelo. No unificar: documentar. |
| H7 | Doble conteo posible tarjeta (fijo "OCA") + transferencia concepto tarjeta. | Realidad: tarjeta se maneja manual (usar → revisar → parte del otro → ajuste). La devolución de la parte **no es ingreso**. | Diseñar la semántica de recuperación para que cubra la parte de tarjeta; **módulo de tarjeta propio = futuro**. Decisión de alcance (P5). |
| H8 | `gastosCalculations.js` código muerto e inconsistente. | Sin uso real. | Descartar/limpiar como corrección menor de implementación (no afecta diseño). |
| H9 | Anuales difieren entre `/gastos` (por periodo) y `/gastos-fijos` (por `pagoHasta`); entradas "pendiente_pago" suman igual al total. | No mencionado por el usuario. Conecta con "histórico vs balance pendiente". | Señalar hallazgo; **decidir (P3)** si existen suscripciones anuales en uso. |
| H10 | Loading infinito si falta índice compuesto; `subscribeIngresos` sin manejo de errores. | No percibido por el usuario. | Corrección técnica de robustez dentro de implementación. |
| H11 | Un solo grupo: `groups[0]`. | Realidad: 1 grupo de 2 personas. Es lo **específico del grupo actual**. | No diseñar multi-grupo completo en Stage 3; definir qué es **general** y qué **particular del grupo actual**. |
| H12 | Sin schemas ni tipos; entidades definidas al escribir. | La app funciona igual. | El diseño define un **modelo conceptual** y mapea a Firestore existente con **cambios mínimos**; no migrar todo. |
| H13 | Transferencias: UI deshabilitada pero lectura activa (enviadas=gasto, recibidas=ingreso). | Mismo origen que H3: concepto obsoleto distorsionando cálculos. | Ver sección 2.5. |

### 2.2 Contradicciones explícitas auditoría vs contexto (sin resolver)

1. **Reintegros (H3/H13):** la auditoría describe las transferencias recibidas como "ingreso" que infla el balance; el contexto de uso dice que **no son ingreso** y que la funcionalidad está en desuso.
2. **Gastos compartidos "nunca se dividen" (H1):** la auditoría lo marca como distorsión a corregir; el contexto dice que **no deben dividirse** (gasto diario compartido = registro). Lo único a decidir es cómo se muestran los **totales**.
3. **"Dos lógicas de compartido" (H6):** la auditoría lo ve como defecto; el contexto dice que son conceptos deliberadamente separados. No hay bug semántico; hay que **documentar la distinción**.
4. **Brecha (no contradicción):** la auditoría no encuentra "dinero a recuperar" porque no existe en el código; el contexto lo introduce como categoría. Es una **carencia a diseñar**.

### 2.3 Modelo conceptual de datos (nivel conceptual, sin schemas técnicos)

- **Grupo** — conjunto de participantes con configuración propia (hoy: 1 grupo, 2 miembros). Se mantiene el concepto aunque hoy haya un solo grupo.
- **Participante** — persona con cuenta/rol dentro del grupo.
- **Movimiento financiero** — clasificación semántica explícita (sección 2.4).
- **Gasto fijo (config)** — ítem recurrente (alquiler, luz, agua, suscripciones), personal o compartido, con **división por partes** (hoy 50/50; compatible a futuro con 60/40 etc.).
- **Entrada de gasto fijo (registro periódico)** — mes/periodo, monto, vencimiento, **pagado_por**, **participantes [{uid, corresponde, pagado}]**, estado. Base del balance real.
- **Balance / saldo** — dato **derivable** (no autorreferente): suma de "corresponde" sin pagar vs adelantos hechos por cada participante. Distinción: **histórico de entradas** (permanece) vs **saldo pendiente** (se salda).
- **Recuperación / dinero a recuperar** — deudor, acreedor, monto, origen (adelanto de gasto extraordinario, parte de tarjeta, etc.), estado (pendiente / saldada). Opcionalmente vinculada al gasto que la originó. **NO es ingreso.**
- **Tarjeta (futuro)** — módulo propio: gastos, pagador, partes, saldo a recuperar. En Stage 3, solo su lógica de recuperación se cubre con el concepto anterior.
- **Transferencias** — estatus a decidir (sección 2.5). No forma parte del modelo objetivo.

**Regla de diseño:** el balance surge de comparar **"quién pagó"** vs **"qué le corresponde"**; cada movimiento declara si participa del balance o no.

### 2.4 Definición explícita de cada movimiento y qué genera balance

| Movimiento | Representa | ¿Genera balance? |
|---|---|---|
| **Ingreso real** (sueldo / banda / freelance) | Dinero nuevo que le pertenece al usuario (trabajo, actuaciones, cobros propios). | No |
| **Gasto personal** | Gasto que solo afecta a quien lo registra. | No |
| **Gasto diario compartido** | Compras/registro visibles al grupo (ej. supermercado del hogar). Historial e información. | **No** (intencional; el grupo actual nunca lo usa con balance) |
| **Gasto fijo personal** | Recurrente individual. | No |
| **Gasto fijo compartido** | Recurrente del grupo con división por partes y quién pagó. | **Sí** — deuda/balance real entre participantes |
| **Recuperación / reintegro / dinero a recuperar** | Devolución de dinero adelantado por otro (mueble, entrada, parte de tarjeta). | **Sí** — genera saldo a recuperar pendiente; el pago lo salda (no es ingreso) |
| **Pago / ajuste de balance** | Salda una deuda o una recuperación. | No (reduce el saldo pendiente) |
| **Tarjeta de crédito (futuro)** | Gastos de tarjeta + parte que corresponde a otro + lo que queda por recuperar. | Vía recuperación (devolución ≠ ingreso) |
| **Transferencias** | Concepto obsoleto del código. | Fuera del cálculo (sección 2.5) |

**Histórico vs balance pendiente:** las entradas y movimientos **nunca se eliminan** aunque el saldo se salde; el "cierre mensual" solo deja el balance en cero conservando el historial.

### 2.5 Tratamiento de las transferencias obsoletas

Opciones evaluadas:
1. **Marcar obsoletas** y dejar el código tal cual → riesgo: los datos históricos se siguen computando como ingreso/gasto.
2. **Excluir de los cálculos** (dejan de sumar a ingresos/gastos) y verlas como histórico fuera de balance → elimina la distorsión sin tocar datos.
3. **Retirar/limpiar la lógica** de lectura y de layout → mantenimiento de código posterior.
4. **Migrar casos históricos** a recuperaciones o a histórico excluido → decisión de datos, con consentimiento del usuario.

**Recomendación (borrador):** opción **2 como mínimo en el diseño** (los cálculos deben ignorar transferencias) y la **3 como limpieza de código** durante la implementación. La decisión sobre los datos históricos existentes (1 vs 4) la toma el usuario (nada se elimina). **No se construye Stage 3 alrededor de esta funcionalidad.**

### 2.6 Configuración flexible por grupo (visión futura)

- **Preparar ahora en el modelo:** la división de fijos compartidos como **lista de partes por participante** (no un 50/50 hardcodeado; el esquema `participantes[]` ya casi lo soporta) y la **clasificación semántica** de movimientos (permite futuro "mostrar balance o no" a nivel grupo sin migración).
- **Posponer:** la UI de configuración ("ruedita"), múltiples grupos activos, tarjeta, estadísticas por producto/categoría, productos custom con merge, cuenta pública.

### 2.7 Separación en 5 categorías

**A. Correcciones necesarias (Stage 4, tras aprobar diseño)**
1. Rotulado de ingresos freelance (por `tipo`, no `subtipo`) y arreglo de ids de banda.
2. Sección/total correctos para el tipo "otros" (según decisión P2).
3. Robustez de suscripciones de ingresos (errores, índices compuestos, fin de loading infinito).
4. Definir **catálogo único de gastos fijos** (resolver doble taxonomía y el "otros" perdido).
5. Quitar del cálculo la lectura de transferencias (env. = gasto / rec. = ingreso).
6. Eliminar código muerto (`gastosCalculations.js`, flujo legado de `fixed_expense_entries`).

**B. Cambios estructurales (núcleo del diseño)**
1. Clasificación semántica de movimientos (los 9 de la sección 2.4) y mapeo a Firestore existente.
2. Concepto **recuperación / dinero a recuperar** (con estado y origen).
3. Gasto fijo compartido con **partes de división no hardcodeadas** (compatible 50/50 → 60/40…).
4. Balance **derivable** (histórico + saldo pendiente), sin autoeliminación.
5. Visualizador alineado a la semántica: sin deuda artificial en diarios compartidos; recuperaciones separadas de ingresos.

**C. Funcionalidades nuevas (explícitas)**
1. Módulo mínimo de **recuperaciones/reintegros** (alta, estado pendiente/saldada, vista de "a quién debo / quién me debe").
2. (Si el usuario lo decide) normalización/visualización de la parte de tarjeta como recuperación.

**D. Mejoras futuras (posponer)**
1. Módulo propio de tarjeta.
2. UI de configuración del grupo/porcentajes.
3. Estadísticas por producto/categoría; productos custom con merge.
4. Historial anual con `pagoHasta` correcto (según decisión P3).

**E. Ideas de producto (visión, no proyectos)**
1. App descargable con cuentas/grupos públicos.
2. Participantes fuera del grupo (amigos, familiares) para recuperaciones.

### 2.8 Cambios mínimos de la aplicación (sin implementar)

1. Tipificar la semántica de movimientos (mínima: un campo/clasificación en `gastos`/`ingresos` + documentación del mapeo).
2. Nueva colección/concepto **recuperaciones** con estado.
3. Ajustar `fixed_expense_entries` a **participantes por partes** (lo existente ya lo soporta casi sin cambio).
4. Visualizador: separar **ingresos** de **recuperaciones**; totales del mes respetando la semántica (según decisión P1).
5. Excluir `transferencias` de todos los cálculos.
6. Robustecimiento de suscripciones (errores/índices).

### 2.9 Evaluación concreta: acceso read-only a Firestore

**Aporta valor: sí, moderado-alto**, específico para el diseño. El `REPORT-02` cubre el código; Firestore agrega la **evidencia real** para decidir puntos abiertos:
- Contenido real de `ingresos` (¿freelance/otros existen? formato histórico) → define la corrección C1 y totales.
- Forma real de `groups`/`users` y si `members[0]` es estable → valida el modelo multi-participante.
- Datos históricos de `transferencias` → decide las opciones de la sección 2.5.
- Huérfanos en `fixed_expenses` y estados reales de entradas → define limpieza y el caso "histórico vs pendiente".

**Condiciones (según contexto):** solo lectura, alcance mínimo, no modificar datos; si el costo es alto o no agrega diferencia, se omite. El coordinador **no solicita el acceso por sí mismo**: es una decisión del usuario otorgar credenciales de solo lectura (P7).

---

## 3. Preguntas pendientes de decisión del usuario (P1–P8)

Antes de poder **diseñar definitivamente** Stage 3:

1. **P1 — Totales del mes (H1):** para gastos diarios compartidos, ¿el mes debe mostrar lo que cada uno **pagó** (caja) o su **parte** correspondiente? (Con la regla de que no generan balance ni deuda.)
2. **P2 — Tipo "otros"** en ingresos: ¿se usa de verdad? ¿mantenerlo con sección o quitarlo?
3. **P3 — Suscripciones anuales (H9):** ¿existe alguna en uso? ¿cómo debe comportarse el histórico anual?
4. **P4 — Transferencias históricas existentes:** ¿migrar a recuperaciones, dejarlas como histórico excluido, o ignorarlas? (Nada se elimina.)
5. **P5 — Tarjeta:** ¿se diseña la semántica de recuperación para cubrirla ya en Stage 3, o se relega el módulo a futuro?
6. **P6 — Recuperaciones:** ¿solo entre miembros del grupo (hoy: pareja) o también con personas externas (amigos, familiares)?
7. **P7 — Firestore read-only:** ¿se aprueba incorporar acceso de solo lectura para el ciclo (y cómo se otorga)?
8. **P8 — Datos existentes:** ¿los gastos diarios compartidos ya cargados quedan como están (registro sin balance), sin normalizar nada?

---

## 4. Registro de sesión (para el panel)

- **Estado del proyecto:** Activo.
- **Etapa 2 (Auditoría):** completada (`REPORT-02.md`, read-only).
- **Etapa 3 (Diseño):** en revisión. Borrador producido en `context/AppFinanciera-Stage3.md`. NO aprobado.
- **Próxima acción:** responder P1–P8 y revisar el borrador de diseño (sección 2).
- **Después de la aprobación:** redactar `HANDOFF-03.md` para el repo de AppFinanciera.
- **Sesión de origen:** 19/09/2026 (cierre de sesión con respaldo para retomar sin perder contexto).