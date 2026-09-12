---
name: user-story-create
description: Convierte una idea o requerimiento en una Historia de Usuario completa (narrativa, criterios de aceptación Gherkin y notas técnicas) validada con INVEST y guardada en software-factory/user-stories/US-NN.md del proyecto. Usar cuando el usuario presente una idea, requerimiento, funcionalidad o pedido de cambio para convertir en historia de usuario, o pida refinarlo.
license: GPL-3.0-or-later
metadata:
  version: "0.1.0"
---

# user-story-create

Convierte un requerimiento crudo en una Historia de Usuario lista para el equipo, siguiendo el estándar 3C (Card, Conversation, Confirmation) y validada con INVEST antes de guardarla.

## Flujo

1. **Recolección** — el requerimiento llega como argumento del comando o en el mensaje del usuario. Si no hay requerimiento, pídelo y detente.
2. **Refinamiento Funcional** — produce la narrativa y los criterios de aceptación.
3. **Refinamiento Técnico** — agrega notas técnicas, dependencias, NFR aplicables y estimación preliminar.
4. **Validación INVEST** — gate obligatorio: si falla, corrige y revalida antes de guardar.
5. **Guardado** — numera, escribe el archivo e informa la ruta.

## Paso 1: Recolectar y clarificar

Actúa como Product Owner: no inventes lo que puedas preguntar, pero tampoco interrogues. Evalúa el requerimiento contra estas dimensiones:

- **Rol**: ¿quién usa o necesita esto? (persona o sistema)
- **Disparador**: ¿en qué situación surge la necesidad?
- **Resultado esperado**: ¿qué debe ser distinto después?
- **Valor**: ¿qué gana el usuario o el negocio? ¿qué pasa si no se construye?
- **Casos límite**: ¿qué ocurre al fallar, con datos vacíos, sin permisos, en volumen?
- **Dependencias**: ¿requiere algo que aún no existe (otra historia, servicio, dato)?

Solo el **rol** y el **valor/necesidad** son bloqueantes: si no puedes identificarlos, formula una única tanda corta de preguntas (máximo 5) y detente. Todo lo demás resuélvelo con supuestos razonables, márcalos en «Supuestos» (paso 3) y lístalos al cierre (paso 5).

## Paso 2: Refinamiento Funcional

**Título**: verbo + objeto, corto y accionable (p. ej. «Recuperar contraseña por email»).

**Narrativa (Card)** — formato obligatorio:

> **Como** [rol],
>
> **quiero** [objetivo],
>
> **para** [beneficio].

- Cada frase va en su propio párrafo: línea en blanco tras la coma, para que el salto de línea sobreviva al renderizado. Palabras clave (**Como**, **quiero**, **para**) en negrita; el contenido, en texto estándar.
- El beneficio es del usuario o del negocio, nunca interno del sistema («para guardar datos en la BD» ✗).
- La narrativa no contiene jerga técnica ni decisiones de UI: van al refinamiento técnico.
- Si no puedes redactar un beneficio real, es probablemente una tarea técnica: pregunta por el valor de negocio antes de continuar.

**Criterios de aceptación (Confirmation)** — en Gherkin, con palabras clave en inglés (`Given` / `When` / `Then` / `And`) y contenido de los pasos en español:

- Un escenario de camino feliz + al menos un escenario de error o caso límite + las variantes de datos relevantes.
- Cada escenario verificable objetivamente: un tester puede marcarlo ✔ o ✘ sin interpretar nada.
- Umbrales con valores concretos («en menos de 2 s», «máximo 3 intentos»), nunca adjetivos vagos («rápido»).

**Alcance**: lista explícita de lo que queda fuera, para evitar ambigüedades futuras.

## Paso 3: Refinamiento Técnico

Notas para el equipo de desarrollo. Incluye solo secciones con contenido real; sin secciones de relleno.

- **Componentes afectados**: módulos o capas del sistema (frontend, API, BD, integraciones).
- **Consideraciones de datos**: entidades, campos, migraciones.
- **Dependencias**: otras historias, servicios internos, terceros.
- **NFR aplicables**: solo los que el requerimiento toca (seguridad, performance, accesibilidad…), con umbral medible.
- **Estimación preliminar**: story points con escala Fibonacci (1, 2, 3, 5, 8, 13), propuestos a partir de señales objetivas (componentes afectados, dependencias, cambios de datos, NFR, novedad del dominio). Es una propuesta a validar en planning, nunca un compromiso. Más de 13 puntos = señal de división (criterio S del paso 4).
- **Supuestos**: lo asumido durante el refinamiento y que el usuario debe confirmar.

## Paso 4: Validación INVEST (gate obligatorio)

| Criterio | Pregunta clave | Si falla |
| --- | --- | --- |
| **I** — Independiente | ¿Puede entregarse sin esperar otra historia? | Declara la dependencia o reordena el backlog |
| **N** — Negociable | ¿Describe el qué sin imponer el cómo? | Mueve la solución propuesta a notas técnicas |
| **V** — Valiosa | ¿Un usuario o el negocio obtiene valor observable? | Reformula hacia el valor o eleva a épica |
| **E** — Estimable | ¿El equipo entiende el alcance para estimar? | Agrega contexto, divide o marca que requiere spike |
| **S** — Pequeña | ¿La completa un par de personas en días, no semanas? (o ¿≤ 13 puntos preliminares?) | Divide con confirmación del usuario |
| **T** — Testable | ¿Cada criterio produce un resultado observable sin ambigüedad? | Reescribe el criterio |

No guardes la historia sin pasar el gate.

**División (cuando falla S)** — proponer y confirmar:

1. Presenta el plan de división: patrón elegido + una línea por historia hija (título y objetivo).
2. Espera confirmación del usuario; sin confirmación, no se crea nada.
3. Tras confirmar, cada hija se crea como `US-NN` propio recorriendo el flujo completo con su propia validación, y referencia la épica original en el campo «Épica» de la plantilla. La historia original no se guarda como US si las hijas la cubren por completo.

**Patrones de división**, en orden de preferencia:

1. Camino feliz primero: versión mínima end-to-end; casos límite como historias hijas.
2. Por pasos del flujo de trabajo: cada paso, un incremento entregable.
3. Por regla de negocio o variante de datos: reglas y variantes simples primero.

## Paso 5: Guardar

1. Busca en `software-factory/user-stories/` del proyecto actual los archivos `US-*.md` existentes y toma el mayor número con **comparación numérica** (US-9 < US-10, no orden alfabético). Crea el directorio si no existe.
2. Numera el siguiente **sin padding**: `US-1.md`, `US-2.md`, …, `US-10.md`.
3. Escribe el archivo con la plantilla de abajo, completando todas las secciones con contenido real.
4. Cierra informando la ruta creada, un resumen de 3–5 líneas y —si quedaron— los supuestos o preguntas abiertas.

## Plantilla de salida

Copia esta estructura a `software-factory/user-stories/US-NN.md`:

```markdown
# US-NN: [Título]

**Estado:** Ready | Borrador
**Épica (opcional):** [referencia]

## Historia

**Como** [rol],

**quiero** [objetivo],

**para** [beneficio].

### Contexto
[Párrafo breve con el problema y el origen del requerimiento. Omitir si la narrativa basta.]

## Criterios de aceptación

### Escenario: [camino feliz]
- Given [contexto inicial]
- When [acción del usuario o del sistema]
- Then [resultado observable]
- And [complementos]

### Escenario: [caso límite o error]
- Given …
- When …
- Then …

## Alcance

**Dentro:** [ … ]
**Fuera:** [ … ]

## Refinamiento técnico

### Componentes afectados
[ … ]

### Consideraciones de datos
[ … ]

### Dependencias
[ … ]

### Requerimientos no funcionales
[ … ]

### Estimación preliminar
**[N] story points** (Fibonacci: 1, 2, 3, 5, 8, 13) — propuesta preliminar, a validar en planning. Base: [señales utilizadas].

### Supuestos
[ … ]

## Validación INVEST

| Criterio | OK | Nota |
| --- | --- | --- |
| Independent | ✅/❌ | [ … ] |
| Negotiable | ✅/❌ | [ … ] |
| Valuable | ✅/❌ | [ … ] |
| Estimable | ✅/❌ | [ … ] |
| Small | ✅/❌ | [ … ] |
| Testable | ✅/❌ | [ … ] |
```

**Estado**: `Ready` si pasó el gate INVEST y no hay supuestos sin confirmar ni preguntas abiertas; `Borrador` en caso contrario.

## Gotchas

- `software-factory/user-stories/` vive en el **proyecto donde se aplica el skill**, nunca en este repo de skills.
- Una historia es un corte vertical de valor: tocar varias capas está bien. Si solo agiliza una capa sin valor observable para el usuario, es tarea técnica de otra historia.
- «Quiero X para poder X» es la señal de beneficio faltante: preguntar el valor real.
- Criterios de aceptación sin escenario de error o caso límite = historia incompleta.
- Continúa la numeración existente (comparación numérica); nunca renumeres historias previas.
- No inventes umbrales NFR: usa el que dio el usuario o un estándar del dominio; si no existe, déjalo como pregunta abierta.
- Los story points son relativos a cada equipo: la estimación del skill es una propuesta preliminar para el planning, nunca un compromiso.
- El campo «Épica» es por ahora solo documental: el manejo de épicas se definirá más adelante.
