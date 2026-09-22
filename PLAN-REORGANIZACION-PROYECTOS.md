# Plan de continuidad — Reorganización de proyectos

## Propósito

Este documento sirve como instrucción de continuidad para retomar desde otra PC la reorganización de la estructura de `Proyectos Personales`.

Debe utilizarse como guía de relevamiento y ejecución controlada.

**No ejecutar cambios automáticamente.**

Primero realizar el relevamiento READ-ONLY, informar el estado actual y proponer un plan. Cualquier modificación requiere aprobación explícita del usuario.

---

# 1. Objetivo de estructura

La estructura física deseada de `Proyectos Personales` es:

```text
Proyectos Personales/
├── personal-system/
│   └── .git/
│
└── opencode-AppFinanciera/
    ├── .git/
    ├── AGENTS.md
    ├── ROADMAP.md
    ├── opencode.json
    ├── .opencode/
    ├── context/
    └── AppFinanciera/
        ├── .git/
        ├── app/
        ├── lib/
        ├── public/
        ├── package.json
        └── ...
```

La intención es mantener tres repositorios independientes:

* `personal-system`
* `opencode-AppFinanciera`
* `AppFinanciera`

No existe un monorepo.

No utilizar Git submodules.

Los `.git` de cada repositorio deben permanecer independientes.

---

# 2. Rol de este documento

Este documento no representa una tarea permanente ni una nueva arquitectura.

Es una instrucción temporal para:

* verificar la estructura desde otra PC;
* detectar diferencias entre máquinas;
* comprobar el estado de Git;
* detectar referencias antiguas;
* continuar la reorganización si fuera necesario;
* dejar preparada la estructura para posteriormente implementar un verificador centralizado desde `personal-system`.

Cuando la reorganización esté completamente validada en ambas PCs, este documento puede conservarse como histórico o eliminarse posteriormente con aprobación del usuario.

---

# 3. Primera etapa — detectar la ubicación de trabajo

Antes de modificar cualquier cosa:

1. Identificar la carpeta raíz de `Proyectos Personales`.
2. Identificar la ubicación del repositorio `personal-system`.
3. Identificar `opencode-AppFinanciera`.
4. Identificar `AppFinanciera`.
5. Confirmar que `AppFinanciera` está físicamente dentro de `opencode-AppFinanciera`.

No asumir rutas absolutas específicas de una PC.

Si existe una ruta documentada que pertenece a otra máquina, tratarla como referencia histórica o específica de máquina y no reemplazarla ciegamente.

---

# 4. Segunda etapa — paneo general de Proyectos Personales

Antes de inspeccionar cada repositorio individualmente, realizar un paneo READ-ONLY de toda la carpeta:

```text
Proyectos Personales/
```

El objetivo es verificar que la estructura general de la PC sea coherente con la estructura esperada.

Mostrar como mínimo:

* carpetas principales;
* repositorios detectados;
* carpetas `.git` detectadas;
* ubicación relativa de cada repositorio;
* repositorios anidados;
* carpetas inesperadas relevantes;
* posibles duplicados de proyectos.

No es necesario mostrar todos los archivos internos de cada proyecto.

El paneo debe permitir detectar rápidamente diferencias como:

```text
PC A

Proyectos Personales/
├── personal-system/
└── opencode-AppFinanciera/
    └── AppFinanciera/
```

frente a:

```text
PC B

Proyectos Personales/
├── personal-system/
├── AppFinanciera/
└── opencode-AppFinanciera/
```

Si la estructura general difiere entre máquinas, informar la diferencia antes de modificarla.

---

# 5. Tercera etapa — identificar repositorios Git

Para cada repositorio detectado, verificar READ-ONLY:

```bash
git status
git branch
git remote -v
git log --oneline -5
```

Como mínimo verificar:

### `personal-system`

Debe ser un repositorio Git independiente.

### `opencode-AppFinanciera`

Debe ser el repositorio que contiene:

* configuración de OpenCode;
* documentación;
* contexto;
* agentes;
* handoffs;
* roadmap;
* demás archivos propios del cerebro/contexto de AppFinanciera.

### `AppFinanciera`

Debe ser un repositorio Git independiente de la aplicación Next.js.

Debe permanecer anidado dentro de:

```text
opencode-AppFinanciera/AppFinanciera/
```

---

# 6. Verificar independencia de los repositorios

Confirmar que:

```text
personal-system/.git/
opencode-AppFinanciera/.git/
opencode-AppFinanciera/AppFinanciera/.git/
```

sean repositorios independientes.

No:

* mover `.git`;
* convertirlos en submodules;
* fusionar historiales;
* crear un monorepo;
* eliminar un `.git`.

---

# 7. Verificar `.gitignore`

El repositorio:

```text
opencode-AppFinanciera/
```

debe ignorar:

```text
AppFinanciera/
```

La aplicación anidada no debe aparecer como contenido trackeado del repositorio padre.

Verificar también que el repositorio `AppFinanciera` siga funcionando normalmente como repositorio independiente.

---

# 8. Verificar nombres

Los nombres físicos esperados son:

```text
personal-system
opencode-AppFinanciera
AppFinanciera
```

Si aparecen nombres o referencias antiguas como:

```text
organizador-app
appFinancieraOpenCode
```

no asumir automáticamente que deben cambiarse.

No tratar `AppFinanciera` como nombre antiguo: es el nombre nuevo y correcto del repositorio de la aplicación anidada.

Distinguir entre:

* nombre físico de carpeta;
* nombre del repositorio;
* nombre del remote;
* nombre histórico;
* referencia documental;
* referencia conceptual;
* ruta absoluta de una máquina.

---

# 9. Referencias antiguas

Buscar referencias relacionadas con la reorganización, especialmente:

```text
Proyectos Personales\AppFinanciera
organizador-app
appFinancieraOpenCode
```

y rutas relacionadas.

Para cada referencia encontrada indicar:

| Referencia            | Ubicación     | Tipo             | Acción  |
| --------------------- | ------------- | ---------------- | ------- |
| ruta antigua          | archivo       | ruta local       | evaluar |
| organizador-app       | documentación | nombre histórico | evaluar |
| appFinancieraOpenCode | Git           | remote           | evaluar |

No realizar reemplazos globales ciegos.

Las referencias históricas pueden mantenerse si tienen sentido.

---

# 10. Verificar remotes

La intención final de nombres en GitHub es:

```text
Caskito1/personal-system
Caskito1/opencode-AppFinanciera
Caskito1/AppFinanciera
```

Pero el nombre actual de un remote no implica que GitHub haya sido renombrado.

Por lo tanto:

* informar los remotes actuales;
* no asumir que GitHub fue renombrado;
* no inventar un cambio;
* no modificar remotes sin aprobación.

Si todavía aparecen:

```text
appFinancieraOpenCode.git
organizador-app.git
```

informarlo como posible normalización pendiente.

---

# 11. Verificar sincronización con GitHub

Para cada repositorio verificar:

* branch actual;
* working tree limpio o modificado;
* commits locales pendientes de push;
* commits remotos pendientes de pull;
* divergencia entre local y remote, si existe.

No hacer `commit`, `push`, `pull`, `merge` ni `reset` como parte de este relevamiento sin aprobación.

---

# 12. Comparación entre PCs

Este procedimiento se ejecutará en más de una PC.

Por lo tanto, el resultado debe permitir comparar fácilmente:

### Estructura general

```text
Proyectos Personales/
├── personal-system/
└── opencode-AppFinanciera/
    └── AppFinanciera/
```

### Estado de repositorios

```text
personal-system          → branch / commit / status
opencode-AppFinanciera   → branch / commit / status
AppFinanciera            → branch / commit / status
```

### Remotes

```text
personal-system          → remote
opencode-AppFinanciera   → remote
AppFinanciera            → remote
```

Si las dos PCs tienen diferencias, señalar exactamente cuáles.

El objetivo no es que ambas PCs tengan necesariamente archivos temporales idénticos, sino que compartan:

* la misma estructura de proyectos;
* los mismos repositorios;
* los mismos nombres;
* la misma referencia de GitHub;
* el estado sincronizado cuando corresponda.

---

# 13. Reglas de seguridad

Durante este procedimiento:

* NO borrar archivos.
* NO borrar carpetas.
* NO borrar repositorios.
* NO modificar el Vault de Obsidian.
* NO modificar objetivos personales.
* NO modificar código de AppFinanciera.
* NO modificar configuración de OpenCode salvo que sea estrictamente necesaria para corregir una referencia de la reorganización.
* NO hacer commits.
* NO hacer push.
* NO cambiar remotes.
* NO ejecutar comandos destructivos.
* NO hacer reemplazos globales sin revisar cada caso.

Primero:

```text
LEER → ANALIZAR → INFORMAR → PROPONER
```

Después de la aprobación:

```text
EJECUTAR → VERIFICAR → INFORMAR
```

---

# 14. Si todavía hay que ejecutar la reorganización

Si el relevamiento detecta que la PC todavía no tiene la estructura esperada, preparar un plan específico.

El plan debe contemplar, cuando corresponda:

```text
AppFinanciera/
    ↓
opencode-AppFinanciera/

organizador-app/
    ↓
AppFinanciera/
```

manteniendo los `.git` correspondientes en cada repositorio.

No ejecutar esos cambios hasta recibir aprobación.

---

# 15. Resultado esperado del relevamiento

La respuesta de OpenCode debe terminar con:

## Paneo general

Mostrar la estructura relevante de:

```text
Proyectos Personales/
```

## Repositorios

Mostrar:

```text
personal-system
opencode-AppFinanciera
AppFinanciera
```

y el estado Git de cada uno.

## Diferencias detectadas

Indicar cualquier diferencia respecto de la estructura esperada.

## Referencias antiguas

Indicar referencias encontradas y si requieren actualización.

## GitHub

Mostrar remotes y posibles diferencias.

## Plan

Si hay cambios necesarios, presentar el plan exacto.

**No ejecutar modificaciones todavía.**

Esperar aprobación explícita del usuario.

---

# 16. Objetivo posterior

Una vez que esta reorganización esté estable y validada en ambas PCs, el siguiente paso será diseñar un verificador centralizado dentro de `personal-system`.

Ese futuro verificador tendrá otro objetivo:

> Centralizar el aviso del estado de los proyectos, pero no centralizar el trabajo de los proyectos.

Ejemplo conceptual:

```text
VERIFICACIÓN DE SESIÓN

personal-system          ✓
opencode-AppFinanciera  ✓
AppFinanciera            ⚠ cambios locales

RESULTADO:
✗ SESIÓN NO CERRADA

Acción:
Entrar a opencode-AppFinanciera para resolver el problema.
```

El verificador futuro deberá ser independiente de este documento.

Su función será detectar el estado general de los repositorios, no administrar el contexto interno de cada proyecto.