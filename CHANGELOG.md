# Changelog

Todos los cambios notables de este proyecto se documentan en este archivo.

El formato sigue la guía [Keep a Changelog](https://keepachangelog.com/es/1.1.0/).

## [No publicado]

## [0.1.0] - 2026-09-12

### Añadido

- Licencia [GPL-3.0-or-later](https://www.gnu.org/licenses/gpl-3.0.html) para el repositorio, con copyright de Leonardo Javier Alviarez Hernández.
- Contenido del skill [`user-story-create`](skills/user-story-create/SKILL.md): flujo de cinco pasos que convierte una idea o requerimiento en una Historia de Usuario — refinamiento funcional (estándar 3C, criterios de aceptación Gherkin) y técnico (estimación preliminar en story points), con validación INVEST como gate obligatorio y plantilla de salida en `software-factory/user-stories/US-NN.md` del proyecto.
- Advertencia de fase de desarrollo (inestable, uso bajo propio riesgo) para `user-story-create` en las tablas de `README.md` y `skills/README.md`.
- Sección «Instalación» en `README.md` con badge de [skills.sh](https://skills.sh/lalviarez/software-factory-skills): método principal `npx skills add lalviarez/software-factory-skills` e instalación manual (global y por proyecto), incluida la instalación de skills individuales.
- Nota de instalación individual y pendientes de publicación (awesome-opencode, Ecosystem de opencode.ai) en `skills/README.md`.
- Workflow de GitHub Actions (`.github/workflows/release.yml`) que, al hacer push/merge a `main`, crea el tag y la GitHub Release de la versión declarada en este archivo que aún no tenga tag, con notas extraídas de su sección y validación de consistencia contra `metadata.version` de cada skill.
- Actualización de `AGENTS.md`: estado real del skill (ya no placeholder), reglas de versionado y release automáticas, y pendientes de publicación; la nota de pendientes se mueve a `AGENTS.md` y se elimina de `skills/README.md`.

### Cambiado

- La narrativa de `user-story-create` («Como / quiero / para») exige ahora un salto de línea tras cada coma (cada frase en párrafo separado), con las palabras clave en negrita y el contenido en texto estándar.
