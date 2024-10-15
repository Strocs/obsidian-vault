---
id: 1727963010-festival-frijol-magico
aliases:
  - Festival Frijol Magico
tags:
  - projects
  - work
  - typescript
  - astro
  - react
  - tailwind
  - vercel
---

# Festival Frijol Magico

**Desarrollo web para el Festival Frijol Mágico, una plataforma de difusión de ilustradores emergentes en la Región de Coquimbo, organizado por la Asociación Cultural Frijol Mágico.**

> Frijol Mágico es un espacio que reúne a las y los Ilustradores de la Región de Coquimbo, generando distintas instancias que ayuden a potenciar su trabajo.

## Links

- [Sitio web](https://frijolmagico.cl)
- [Respositorio](https://github.com/strocs/frijolmagico)

## Tecnologías

- **Lenguajes:** TypeScript
- **Frameworks:** Astro, React, TailwindCSS
- **Testing:** Playwright 
- **Bundler:** Vite
- **Hosting:** Vercel

## Estado del proyecto

Lanzado en 2022, actualmente en su tercera edición con nuevas secciones y funcionalidades.

## Proceso de desarrollo

La página web del Festival Frijol Mágico ha evolucionado a lo largo de tres ediciones, adaptándose para incluir nuevas funcionalidades como una galería interactiva de ilustradores, que sigue creciendo con cada edición.

He sido responsable del desarrollo y mantenimiento del sitio desde la primera edición en 2022. La primera versión fue un desafío único al ser mi primera experiencia desarrollando un sitio web, utilizando **Vanilla JavaScript, CSS y HTML**. A medida que el festival creció, realicé la transición tecnológica a **Astro y React**, lo que mejoró significativamente la escalabilidad del proyecto y permitió agregar nuevas funcionalidades en cada nueva edición.

### Diseño

Para la última edición del festival, implementé un diseño basado en **bento grid** que mejora la navegación y resalta las secciones clave del sitio, como la galería de ilustradores. Este diseño facilita la expansión del sitio en futuras ediciones, permitiendo una integración rápida de nuevas secciones y funciones.

### Desarrollo

La versión actual del sitio está desarrollada con [**Astro**](https://astro.build) para mejorar el rendimiento y la facilidad de mantenimiento. Utilicé [**React**](https://react.dev) para componentes interactivos clave y [TailwindCSS](https://tailwindcss.com) para agilizar la creación de estilos. También implementé pruebas automáticas con [**Playwright**](https://playwright.dev) para asegurar la compatibilidad multiplataforma, garantizando una experiencia de usuario fluida en diferentes navegadores.

Para esta edición, implementé el uso de **Google Sheets** como un **Headless CMS**, de acuerdo a lo que me solicitó el cliente, de forma de poder actualizar y agregar nuevos ilustradores desde la misma aplicación que utiliza para la coordinación del festival. Esto lo resolví utilizando la API que entrega google, y realizando la solicitud desde el servidor, de forma de evitar un gasto mayor y manteniendo el rendimiento del sitio.

El principal desafío ha sido mantener la **escalabilidad** del sitio, dado que en cada edición se han incorporado nuevas secciones y funcionalidades que transforman el sitio en una fuente de referencia para la comunidad artística de la región.

### Aprendizajes

A lo largo del desarrollo del proyecto, he aplicado conceptos clave de **arquitectura de software**, lo que ha mejorado la organización del código y su legibilidad. Esto me ha permitido escalar el sitio de forma eficiente, agregando nuevas funcionalidades sin comprometer el rendimiento ni la facilidad de mantenimiento.

## Galería

