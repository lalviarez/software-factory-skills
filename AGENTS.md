# AGENTS.md

Colección de skills de OpenCode para el flujo de software factory: de la Historia de Usuario a producción. Repositorio solo de documentación: no hay build, lint, tests ni toolchain; la verificación es revisión de Markdown.

## Estructura

- Un skill = un directorio `skills/<skill-name>/` con su `SKILL.md`.
- Formato de `SKILL.md`: frontmatter YAML con `name` y `description`, seguido del cuerpo en Markdown (formato de skills de OpenCode).

## Convenciones

- Toda la documentación se escribe en español.
- Al agregar o modificar un skill, sincronizar:
  - la tabla en `README.md` (raíz), con el comando como `/skill-name`;
  - la tabla en `skills/README.md`, con descripción detallada (incluye la ruta de salida);
  - `CHANGELOG.md` (estilo Keep a Changelog).
- `LICENSE` contiene el texto canónico de la GPL-3.0 y no se modifica; la nota de copyright del autor vive en la sección Licencia del `README.md`. El código que se agregue en el futuro debe llevar cabeceras GPL por archivo.
- Las historias de usuario se numeran `US-NN` y se guardan en `software-factory/user-stories/US-NN.md` — ruta en el proyecto destino donde se aplica el skill, no en este repo.

## Estado actual

- Skill existente: `user-story-create` (fases de Refinamiento Funcional y Refinamiento Técnico); su `SKILL.md` es un placeholder vacío pendiente de contenido. El repo se distribuye bajo GPL-3.0-or-later (texto completo en `LICENSE`).