---
id: 1727877654-memoria-audiovisual
aliases:
  - Memoria Audiovisual
tags:
  - projects
  - work
  - typescript
  - astro
  - tailwind
  - vercel
---

# Memoria Audiovisual

**Desarrollo web para el proyecto Memoria Audiovisual realizado en 2023 por la Escuela de Arquitectura de la Universidad de La Serena.**

> Memoria Audiovisual busca ser una ventana de difusión para trabajos de titulación con la comunidad dentro y fuera de la universidad, además de servir como material de apoyo para estudiantes que comienzan su proceso, mostrando cómo otros superaron las barreras del mismo.

## Links

- [Sitio web](https://memoriaaudiovisual.vercel.app/)
- [Repositorio](https://github.com/strocs/MemoriaAudiovisual)

## Tecnologías

- **Lenguajes:** JavaScript, TypeScript
- **Frameworks:** Astro, TailwindCSS
- **CDN:** BunnyCDN, Cloudflare
- **Bundler:** Vite
- **Hosting:** Vercel

## Estado del proyecto

Finalizado en 2023.

## Proceso de desarrollo

Fui contactado para desarrollar el sitio web **Memoria Audiovisual**, cuyo propósito era difundir los trabajos de titulación de la Escuela de Arquitectura de la Universidad de La Serena. El proyecto actúa como un repositorio digital que exhibe cuatro proyectos de titulación, cada uno acompañado de un video donde los estudiantes explican su proceso, además de incluir imágenes y descripciones detalladas.

El requerimiento principal era crear un sitio con una experiencia similar a los **reels de Instagram**, implementando un **scroll infinito** con videos resumen de cada proyecto, desde los cuales los usuarios pudieran acceder a más detalles de cada trabajo.

### Diseño

El diseño adoptó una **línea minimalista** con colores básicos, enfocándose en destacar los videos y el contenido clave de manera clara y sencilla. Se priorizó una **experiencia optimizada para dispositivos móviles**, emulando el comportamiento de una **aplicación web** en lugar de un sitio tradicional.

- Los videos resumen de 15 segundos ocupan el centro de la interfaz, permitiendo navegar intuitivamente mediante **gestos de swipe**.
- El diseño minimalista realza la información sin distracciones, optimizando la experiencia del usuario en móviles, donde gran parte del público objetivo interactuaría con la plataforma.

### Desarrollo

A pesar de que **React** hubiera sido una opción lógica por la alta interactividad de la plataforma, opté por [**Astro**](https://astro.build/) como un desafío personal. Astro permite una **generación estática** eficiente y, como metaframework, permite integrar otros frameworks si fuese necesario, lo que añade flexibilidad a largo plazo.

Para el diseño, utilicé [**TailwindCSS**](https://tailwindcss.com/), lo que me permitió mantener una estructura de código limpia y responsiva, mientras que las pruebas de rendimiento y navegabilidad se realizaron utilizando [**Playwright**](https://playwright.dev/), asegurando una experiencia fluida en distintos navegadores y dispositivos.

Uno de los principales desafíos fue garantizar una **carga rápida** de los videos en la página de inicio y permitir su reproducción automática sin afectar la velocidad de navegación. Para abordar este problema, implementé un **CDN con capacidad de streaming**. Esto mejoró drásticamente los tiempos de carga, especialmente en móviles.

### Optimización y aprendizajes

Uno de los mayores aprendizajes fue la importancia de **optimizar el contenido multimedia** utilizando **CDN distribuidos** cercanos a los usuarios finales. Inicialmente, implementé **BunnyCDN** para reducir la latencia y mejorar la entrega de los videos, pero luego añadí la **capa gratuita de Cloudflare** para aprovechar su red global, asegurando que el contenido se cargara rápidamente desde el servidor más cercano a los usuarios.

Este proyecto me permitió profundizar en la importancia de la **optimización de contenido multimedia**, la integración de servicios de **streaming eficientes** y el impacto positivo que esto tiene en la experiencia del usuario.

## Galería
