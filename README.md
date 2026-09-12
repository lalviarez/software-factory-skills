<p align="center">
  <h1 align="center">Skills para desarrollo de software</h1>
  <p align="center">Desde la Historia de Usuario hasta su puesta en producción</p>
  <p align="center">
    <a href="https://skills.sh/lalviarez/software-factory-skills">
      <img src="https://skills.sh/b/lalviarez/software-factory-skills" alt="skills.sh" />
    </a>
  </p>
</p>


## Skills

| Skill | Descripción | Argumento | Estado |
| --- | --- | --- | --- |
| `/user-story-create` | Crea una historia de usuario en base a una idea o requerimiento | idea o requerimiento | En desarrollo — inestable, uso bajo propio riesgo |

---


## Instalación

Requisitos: [OpenCode](https://opencode.ai/docs/) y npx (incluido con Node.js).

**Opción recomendada** — instala el paquete completo o solo las skills que elijas:

```bash
npx skills add lalviarez/software-factory-skills
```

El CLI detecta OpenCode entre tus agentes y coloca las skills en el directorio correcto; con más de una skill en el paquete, te permite seleccionar cuáles instalar. El CLI recolecta telemetría anónima de instalaciones; puede desactivarse con `DISABLE_TELEMETRY=1`.

**Alternativa manual** — clona el repositorio y copia la skill a cualquiera de los directorios donde OpenCode descubre skills ([documentación](https://opencode.ai/docs/skills/)):

```bash
git clone https://github.com/lalviarez/software-factory-skills.git
# Global (disponible en todos los proyectos):
cp -r software-factory-skills/skills/user-story-create ~/.config/opencode/skills/
# Por proyecto:
cp -r software-factory-skills/skills/user-story-create <proyecto>/.opencode/skills/
```

Para instalar una **skill individual**, copia únicamente su subdirectorio (`skills/<skill-name>/`). También se admiten los directorios compatibles `.agents/skills/` y `.claude/skills/`, en sus variantes global y por proyecto.

Verifica la instalación abriendo OpenCode en tu proyecto: al teclear `/` debe aparecer `/user-story-create`.

---


## Licencia

Copyright (c) 2026 Leonardo Javier Alviarez Hernández.

[GPL-3.0-or-later](https://www.gnu.org/licenses/gpl-3.0.html): uso libre para cualquier fin (comercial o no); toda distribución de copias o modificaciones debe realizarse bajo esta misma licencia; el uso particular o interno no distribuido no genera obligaciones.
