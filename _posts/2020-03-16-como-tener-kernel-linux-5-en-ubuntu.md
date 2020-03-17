---
layout: post
section-type: post
title: "Cómo tener el kernel linux 5.* en tu Ubuntu?"
description: >-
  Ubuntu LTS lleva su propio kernel estable, pero fácilmente
  puedes pasarte a versiones posteriores.
category: technical
tags: [ 'kernel', 'linux', 'ubuntu' ]
image: /img/ubuntu_kernel_5.png
---

Salió en el [Slack] de [Tarragona Developers Meetup], de mano de 
[Santi Frias], que había puesto el kernel 5 en su pc antiguo y 
que notó una notable mejora en rendimiento y velocidad.
Y me pregunté `¿Cómo puedo tener el kernel 5.*
en mi Ubuntu?`

<!--excerpt-->

Lo que busco es una opción sostenible en el tiempo, cómoda, y que se
actualice automáticamente. Ello conlleva a descartar directamente opciones
donde haga falta compilación desde mi pc.

Pues la verdad que no me costó demasiado encontrar [un foro]
en el que explicara cómo hacerlo. Aunque ahí habla del kernel 5.0,
en mi caso, se ha instalado un kernel superior, el 5.3.

Sigo los pasos del foro, con lo que vemos que tengo este sistema:

```bash
$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 18.04.4 LTS
Release:	18.04
Codename:	bionic
```

y el kernel release (he cambiado la opción `-a`, que lo muestra todo, por `-r` que sólo muestra la release del kernel):

```bash
$ uname -r
4.15.0-91-generic
```

Vale... esta es mi situación actual. 

### Y ahora qué? 

Cómo hago por tener el kernel 5?

Sin más, el foro nos explica que Ubuntu LTS dispone del `hardware enablement stack` ([HWE]),
que provee de las últimas versiones del kernel y drivers gráficos xorg para tu versión
LTS actual.

Entendido esto, sólo necesito instalar unos paquetes y reiniciar tu pc:

```bash
sudo apt install --install-recommends linux-generic-hwe-18.04 xserver-xorg-hwe-18.04
sudo reboot
```

La verdad que en la parte gráfica, como pide que se instale todo aquello recomendado,
instala muchos paquetes xorg que seguro no necesitarán mi pc. No obstante, prefiero
seguir los pasos en una primera instancia sin cambios y experimentar después.

Una vez reiniciado el PC, puedo observar que la primer versión del kernel es:

```bash
Ubuntu, amb el Linux 5.3.0-42-generic
Ubuntu, with Linux 5.3.0-42-generic (recovery mode)
Ubuntu, amb el Linux 4.15.0-91-generic
Ubuntu, with Linux 4.15.0-91-generic (recovery mode)
Ubuntu, amb el Linux 4.15.0-88-generic
Ubuntu, with Linux 4.15.0-88-generic (recovery mode)
``` 

Y una vez estoy dentro del sistema, vuelvo a comprobar la release 
del kernel:

```bash
$ uname -r
5.3.0-42-generic
```

Éxito!

### He notado algo distinto?

La experiencia de usuario iniciando con el kernel 5.3 es realmente notorio:

1. Tarda mucho menos desde el menú de boot hasta ver la pantalla de login.
Ahora apenas de 3 a 4 segundos, cuando antes eran unos 10 segundos.
1. Autenticarme en el pc y ver el escritorio listo para su uso también tarda bastante menos.
1. La respuesta de las aplicaciones y del sistema en general lo siento más
rápido y fluido. 

Por ahora, todo lo que usaba sigue funcionando igual de bien, y no he tenido 
problemas con hardware alguno. Realmente, como decía Santi, ofrece una mejor gestión
de los recursos y eso se nota.

Y tú? Quieres beneficiarte del último kernel en Ubuntu?

### Otras opciones

La verdad que no es que haya solo esta opción que he usado. Si buscas
encontrarás más alternativas para actualizar tu kernel sin tocar todo lo demás.

Por ejemplo, en [addictivetips.com] hablan del UKUU (Ubuntu Kernel Upgrade Utility)
que te permite seleccionar qué kernel quieres usar. Lo encuentro más adecuado si,
por tu hardware, necesitas una versión concreta de kernel y que no sea la última.

También hablan de compilar del código fuente, opción que me niego, por lo
arriesgado de la operación y su mantenimiento con el tiempo.

En una línea más parecida al UKUU, hay el post en [sourcedigit.com] con lo
que puedes descargarte el paquete del kernel que tú quieras, por ejemplo del ya [5.5].
Muestra cómo instalarlo para arquitectura x86 y 64 bits.

[Slack]: https://tgndevs.slack.com/
[Tarragona Developers Meetup]: https://www.meetup.com/Tarragona-Developers-Meetup/
[Santi Frias]: https://github.com/sfrias
[un foro]: https://itsfoss.com/ubuntu-hwe-kernel/
[HWE]: https://wiki.ubuntu.com/Kernel/LTSEnablementStack
[addictivetips.com]: https://www.addictivetips.com/ubuntu-linux-tips/linux-kernel-5-on-ubuntu-18-04-lts/
[sourcedigit.com]: https://sourcedigit.com/24899-update-and-install-linux-kernel-5-4-on-ubuntu-linux/
[5.5]: https://kernel.ubuntu.com/~kernel-ppa/mainline/v5.5/
