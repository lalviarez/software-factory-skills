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

## Versionado y releases

- `CHANGELOG.md` es la fuente de verdad de versiones. Para liberar, en el propio PR: renombrar `## [No publicado]` → `## [X.Y.Z] - fecha`, dejar un `## [No publicado]` vacío y subir `metadata.version` de cada `skills/*/SKILL.md` a la misma versión.
- `.github/workflows/release.yml` automatiza el resto: al hacer push/merge a `main`, si la versión declarada no tiene tag, valida la consistencia CHANGELOG ↔ `metadata.version` de las skills, extrae las notas de esa sección y crea el tag `vX.Y.Z` y la GitHub Release. Es idempotente: merges sin versión nueva no generan releases.

## Estado actual

- Skill existente: `user-story-create` — `SKILL.md` completo (`metadata.version` 0.1.0): flujo de cinco pasos que convierte una idea o requerimiento en una Historia de Usuario (refinamiento funcional 3C con criterios Gherkin, refinamiento técnico con estimación preliminar en story points, validación INVEST como gate obligatorio), guardada en `software-factory/user-stories/US-NN.md` del proyecto destino. Figura «En desarrollo» en las tablas de los README.
- Repo público en GitHub (`lalviarez/software-factory-skills`) con sección «Instalación» en `README.md` (`npx skills add` + manual) y badge de skills.sh.
- Distribuido bajo GPL-3.0-or-later (texto completo en `LICENSE`).

## Pendiente de publicación

Cuando una skill salga de «En desarrollo», enviar el paquete a:

- [awesome-opencode](https://github.com/awesome-opencode/awesome-opencode) (PR)
- Página [Ecosystem](https://opencode.ai/docs/ecosystem/) de opencode.ai (PR)