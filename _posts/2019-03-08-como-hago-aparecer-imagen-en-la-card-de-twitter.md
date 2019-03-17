---
layout: post
section-type: post
title: "Cómo hago aparecer la imagen en la card de Twitter?"
description: >-
  Después de diversas pruebas, finalmente conseguí mostrar
  la imagen den las cards de Twitter. Os explico cómo lo conseguí.
category: technical
tags: [ 'twitter' ]
image: /img/por-fin.png
---

Le das vueltas y vueltas y no consigues visualizar la imagen
en las cards de Twitter? Aquí te explico mi secreto!

<!--excerpt-->

La verdad es que en mi caso, usando Jekyll, con los plugins 
`jekyll-feed` y `jekyll-seo-tag` lo tenía todo bastante 
automático para empezar.

Con el `jekyll-seo-tag` veía todas las cabeceras que debía tener,
según la [documentación de Twitter sobre cards].

Tal como me comentó en seguida Víctor, tenemos a nuestra disposición
el [Twitter Card validator] que nos facilita el asegurar que las
imágenes se vean.

Disponía de todas estas cabeceras (en el código HTML dentro del tag `html -> meta`),
por ejemplo este:

```html
<meta name="generator" content="Jekyll v3.7.4" />
<meta property="og:title" content="Reestructurando tu kanban" />
<meta name="author" content="Jordi Pujol Ahulló" />
<meta property="og:locale" content="es_ES" />
<meta name="description" content="Cambio en el uso del kanban para reflejar mejor las necesidades en tu día a dia" />
<meta property="og:description" content="Cambio en el uso del kanban para reflejar mejor las necesidades en tu día a dia" />
<link rel="canonical" href="https://jpahullo.github.io/2019/02/27/reestructurando-kanban.html" />
<meta property="og:url" content="/2019/02/27/reestructurando-kanban.html" />
<meta property="og:site_name" content="Cosas que pasan" />
<meta property="og:image" content="/img/kanban.jpg" />
<meta property="og:type" content="article" />
<meta property="article:published_time" content="2019-02-27T00:00:00+00:00" />
<meta name="twitter:card" content="summary" />
<meta name="twitter:site" content="@jpahullo" />
<meta name="twitter:creator" content="@Jordi Pujol Ahulló" />
``` 

Hasta aquí la teoría, y todo parece estar correcto.

**¿¿¿¡¡Pero por qué a mi no me aparecían las imágenes!!???**

A que no le ves nada raro... yo tampoco!

Hoy, después de hacer una búsqueda en google y foros, encontré un comentario
que hablaba de *urls relativas*. Tate... aquí hay tomate.

Justamente el el tag `og:image` tiene url relativa!!! Será por eso?

Nada, cojo el fichero `_config.yml` y le actualizo la variable de configuración
`url` de `""`, a:

```yml
url: "https://jpahullo.github.io"
```

Et voilá!

El código html generado ahora es con URL absoluta, y puedo ver en el
[Twitter Card validator] que por fin lo conseguí:

![Usa url absoluta y no relativas en tus cabeceras](/img/por-fin.png)

[documentación de Twitter sobre cards]: https://developer.twitter.com/en/docs/tweets/optimize-with-cards/guides/getting-started
[Twitter Card validator]: https://cards-dev.twitter.com/validator
