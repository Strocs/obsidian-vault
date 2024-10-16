---
id: 1727878089-datos-fondos-de-cultura
aliases:
  - Datos Fondos de Cultura
tags:
  - projects
  - personal
  - typescript
  - nextjs
  - tailwind
  - vercel
  - python
---

# Datos Fondos de Cultura

**Desarrollo del proyecto personal Datos Fondos de Cultura, una aplicación web para el analizar y comparar proyectos de los Fondos de Cultura del Gobierno de Chile.**

> site description

## Links

- [Sitio web](https://datosfondosdecultura.vercel.app)
- [Respositorio](https://github.com/strocs/datosfondosdecultura)

## Tecnologías

- **Lenguajes:** TypeScript, Python, NodeJs
- **Frameworks:** NextJs
- **UI:** Shadcn, TailwindCSS
- **Database:** Turso, SQLite
- **ORM:** Prisma
- **Bundler:** Turbopack
- **Hosting:** Vercel

## Estado del proyecto

En desarrollo.

## Proceso de desarrollo

El prouecto nace de la necesitdad de analisis y comparación de proyectos de los Fondos de Cultura del Gobierno de Chile de manera visual e interactiva, ya que actualmente la unica manera de encontrar esta información es a través de los PDF subidos en la plataforma del gobierno y resulta engorroso filtrar y manejar la información.

El sitio busca ser una herramienta que permita a los usuarios generar compraciones respecto a asignaciones regionales y por tipo de proyectos, de forma de tener un mejor entendimiento de cómo se distribuyen los recursos de cultura en el territorio y tener un amplio marco de analisis.

Encontré en e desarrollo de este proyecto una oportunidad de aprender más sobre tecnologís de desarrollo moderno y de como enfrentar un proyecto que toca todos los aspectos del desarrollo web, como el backend, frontend, análisis de datos, etc.

### Desarrollo

#### Recolección de los datos

La priemra etapa del proyecto consistía en recolectar los datos de los proyectos y guardarlos en una base de datos, para esta tarea utilicé tanto nodejs como python, con nodejs realicé el scrappeo del sitio de forma de obtener los links de los pdf separados y categorizados, desarrollando un script que me permite recolectar nuevos resultados a medida que aparecen en el sitio oficial.

Luego los dato son analizados por un script de python utilizando la libreríá pymupdf par extraer los datos de los pdfs. Estos datos son almacenados en archivos JSON en local, para ser parseados y analisados evitando cualquier error antes de ser guardados en la base de datos.

#### Desarrollo de la aplicación

Una vez recolectados los datos, se crea una aplicación web con NextJs, que permite a los usuarios visualizar los datos recolectados, y realizar análisis de datos sobre los proyectos que consta de tabla de datos, gráficos y mapas que permiten visualizar claramente la distribuición e proyectos a lo largo del territorio.


- Cacheo de información
- Implementación de cache en varios capas para evitar repetir consultas y reducir costos.

- Se espera desarrollar una API para que los datos sean consumidos por otros proyectos.

### Aprendizajes

## Galería
