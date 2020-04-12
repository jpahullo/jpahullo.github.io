---
layout: post
section-type: post
title: "Cómo puedo copiar ficheros de un Android a mi pc por línea de comandos?"
description: >-
  Sin herramientas extra, y con la fiabilidad de la línea de comandos,
  podemos copiar ficheros de tu dispositivo Android a tu pc.
category: technical
tags: [ 'Android', 'linux', 'ubuntu', 'rsync', 'command line' ]
image: /img/de_movil_a_discoduro.png
---

Me gusta poder copiar los ficheros tal cual como backup de mis dispositivos Android,
guardarlos en como mínimo mi disco duro externo. Pero navegar desde un ordenador 
por las carpetas del dispositivo Android, o copiar y demás operaciones, no son ágiles para nada. 
Por ejemplo, cuando navegamos por carpetas con fotos, el ordenador suele previsualizarlas.
Si hace mucho que no vaciamos de fotos y tenemos miles de fotos, entrar en esa carpeta es.... 
muerte. 

<!--excerpt-->

`¿Cómo puedo copiar mis fotos, descargas y demás ficheros importantes de mi Android a
mi pc de forma fiable?`

### Opción fácil: la nube

Tenemos muchas opciones para subir nuestro contenido, o parte de él, a la nube para nuestros
dispositivos Android. Y de la nube a nuestro pc ya es más fácil, aunque no sea inmediato.

Con Google Photos podremos subir nuestras fotos a la nube. Para la mayoría de las personas
las fotos son la parte más importante del contenido de su dispositivo.
Además, si escogemos subirlas en su calidad óptima (la opción la
encontraremos dentro de la aplicación, en la sección de sincronización), tendremos almacenamiento
ilimitado para nuestras fotos. Aunque no sea su calidad real, para la mayoría de
los usos no notaremos ninguna pérdida de calidad en esas imágenes si, por ejemplo, las mandamos a imprimir
en nuestro estudio fotográfico. Pero ya estamos asumiendo en este caso una pérdida de calidad 
de la foto, aspecto que me gustaría prevenir. Y paro aquí, porque este post no va de Google Photos ;-) 

Para quien use estas aplicaciones de sincronización de contenidos a la nube, debe responsabilizarse
de lo que acepta por su uso, aunque sea gratis. Es más, si el uso es gratis, tú eres el producto.

Retomando el objetivo de mi post, lo que sí me gusta es tener en tamaño real y sin retoques aquello que dispongo en mi
dispositivo Android para futuros usos.

### Cómo podemos copiar del Android al PC directamente?

Tenemos muchas opciones para copiar ficheros de nuestro dispositivo Android a nuestro PC,
principalmente cualquiera de ellas está dentro de estas tres categorías:

1. Conectando el móvil por USB al PC.
1. Con aplicaciones que instalas en tu PC que se conectan a tu móvil (por wifi o por cable).
1. Con aplicaciones que instalas en tu Android y que permiten navegar via wifi por los archivos
de tu dispositivo desde tu PC.

### Mis criterios para la elección

Siempre busco en este tipo de cuestiones:

1. La simplicidad del proceso, 
1. Descartando aplicaciones innecesarias,
1. Seguridad y confianza en la transmisión de los ficheros,
1. Repetibilidad de la operación en caso de fallo, retomando la operación desde donde se quedó.
1. Sin coste, a poder ser.

### Mi elección

Con todo esto en mente, me queda una sola opción: usar el cable USB para conectar el móvil al PC
y usar alguna herramienta estándar, como `rsync`.

[Cuando conectamos nuestro móvil por USB al PC], podemos elegir diferentes opciones dentro del móvil,
como que sólo cargue, que se conecte por MTP -para transmisión de cualquier tipo de fichero- o 
por PTP -para transmisión de imágenes-.

Selecciono la opción `MTP` y automáticamente vamos a ver nuestro dispositivo como una unidad de disco
en nuestro escritorio Ubuntu:

![Mi móvil como unidad de disco en mi escritorio](/img/de_movil_a_discoduro.png)

En esta imagen podemos ver el icono del móvil y el del disco duro donde voy a copiar los ficheros.

Entonces, lo que desearía poder hacer es usar un terminal y poder ejecutar un comando del estilo:

```bash
time rsync -av /ficheros/de/mi/móvil /destino/en/mi/disco/duro
```

con lo que:

* `time` me va a ofrecer el tiempo que ha necesitado `rsync` para completar la operación,
* `rsync -av` me va a copiar todos los ficheros y directorios, donde con `-a` selecciono todos los ficheros
y con `-v` escojo que liste todo fichero que va copiando.
 
Pero cuáles son los dos path que necesito?

### Gestión del sistema de ficheros en Ubuntu

Cuando conectamos un disco duro externo a nuestro Ubuntu, éste suele aparecer en el sistema como
`/media/{tuusuario}/{nombre del disco duro}`. Así ocurre con el disco duro de arriba y me aparece
como `/media/jordi/Seagate\ Expansion\ Drive/`. Nuestro linux lo gestiona así para que tu usuario tenga
todos los permisos para poder gestionarlo, sin tener que ser root.

Cabría esperar que el dispositivo móvil apareciese ahí también, pero no! Aquello que se conecta
por MTP aparece en tu sistema de ficheros bajo el path `/run/user/{userid}/gvfs/mtp\:host[...]`.
En mi caso, aparece como `/run/user/1000/gvfs/mtp\:host\=%5Busb%3A001%2C010%5D/`, porque mi usuario 
`jordi` tiene el id `1000`, y el dispositivo móvil tiene el identificador `host\=%5Busb%3A001%2C010%5D/`.
Por lo tanto, llegados a este punto, `/run/user/1000/gvfs/mtp\:host\=%5Busb%3A001%2C010%5D/` equivale
al icono en el escritorio. Ahora ya solo necesitamos ir aplicando los comandos, como por ejemplo:
 
```
$ time rsync -av /run/user/1000/gvfs/mtp\:host\=%5Busb%3A001%2C010%5D/Almacenamiento\ del\ Teléfono/DCIM/ /media/jordi/Seagate\ Expansion\ Drive/fotos_movil/
```

De esta forma, podré copiar todo el contenido de las capetas de mi dispositivo Android a mi pc,
donde más me apetezca. Y gracias a `rsync`, si repito el comando una segunda vez, me aseguraré que 
todo esté copiado, sin repetir el copiado entero, que puede llegar a durar mucho (una hora o más!).

### Para qué uso esta operación?

Varios son los motivos que me llevan a sincronizar el contenido de mi Android al pc:

1. Por falta de espacio en mi móvil. Así, copio las fotos y lo que necesite en mi pc, y luego vacío
el móvil de aquello que ya dispongo copia.
1. Por tener copia de seguridad de mi viejo Android, antes de darle otro uso, por ejemplo, para 
que mi hija pequeña pueda usarlo sin riesgo alguno.

### Problemas que me he encontrado

Pues sí, me he encontrado con problemas, concretamente uno, y que me llevó de cabeza durante un buen
tiempo:

1. El cable USB

El cable debe ser del tipo que necesitas y que funcione, de verdad. Me sucedió que mi cable USB se
estropeó y se comportaba erróneamente. Al principio se conectaba y podía lanzar el comando `rsync`,
pero con el tiempo se desconectaba. Como tardaba mucho el copiado, más de una hora, y lo dejaba 
desatendido, no sabía a priori qué era lo que causaba la interrupción (el linux, el Android, el qué?).
Depurando todo lo que podía probar del Android, del linux, buscando por foros, al final cambié 
el cable por otro, aplicando el lema `divide y vencerás`. Y a partir de ahí ya funcionó todo a la perfección.

### Conclusiones

Hemos visto opciones cómodas y fáciles como la sincronización en la nube del contenido de nuestro
móvil. Pero si quieres una copia idéntica y real de lo que aparece en tu móvil, tienes que ir a
buscar otras opciones. Para mi, la que más me ha gustado de lo que he probado, es la conexión
por `MTP` de tu móvil Android al pc, y el uso de `rsync` por línia de comandos. La verdad que 
tal vez no es la opción más cómoda para mucha gente. Para mi, en cambio, es la mejor opción de lo que
he visto hasta el momento. Tienes alguna otra propuesta? Coméntamelo!

[Cuando conectamos nuestro móvil por USB al PC]: https://www.howtogeek.com/192732/android-usb-connections-explained-mtp-ptp-and-usb-mass-storage/

