# Apuntes · Puesta en producción segura

Apuntes de la asignatura Puesta en producción segura del curso de especialización en ciberseguridad en entornos de las tecnologías de la información. Se publicarán en
<https://victor-educ.github.io/apuntes-PPS/>.

## Editar

Los apuntes son ficheros Markdown en `docs/`. Cada unidad de trabajo está en `docs/ut/`.
El sitio se genera con [MkDocs Material](https://squidfunk.github.io/mkdocs-material/).

```bash
pip install -r requirements.txt
mkdocs serve        # vista previa en http://127.0.0.1:8000
```

Cada push a `main` lanza el workflow de `.github/workflows/deploy.yml`, que construye el sitio
y lo publica en GitHub Pages.

## Autoría

Los apuntes los ha escrito Víctor Sellés apoyándose en Claude, el asistente de IA de Anthropic, para redactar, ampliar y revisar el material a partir del material de la asignatura en cursos anteriores y de la planificación del curso. El contenido está revisado por el autor.

## Material de terceros

El sitio no reproduce los apuntes de otros autores: los enlaza y los cita en la página Material de partida. Las imágenes de terceros llevan su atribución al pie.

## Licencia

Texto e imágenes propias: [CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/deed.es).
