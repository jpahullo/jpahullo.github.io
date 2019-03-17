---
layout: post
section-type: post
title: "Facilitando una sesión de Event Storming"
description: >-
  Experiencia facilitando una sesión introductoria a la
  metodología Event Storming
category: technical
tags: [ 'meetup', 'tgndevs', 'agility', 'agile', 'event storming' ]
image: /img/grupo_vino_400x300.jpg
---

¿Vemos cómo hemos montado una sesión práctica de Event Storming?

<!--excerpt-->

## Contexto

Formo parte del [Meetup Tarragona Developers]. 
Mi participación actualmente es como co-organizador, junto con Adri y Guille, que me
invitaron a unirme a la organización. Os agradezco la propuesta, pues me ha sido
una grata experiencia hasta hoy día.

Este Meetup es auto-organizado y las charlas las damos entre todos los participantes, uniendo quien
tiene ganas de ponerse en la palestra con quien está interesado en el contenido de la
sesión. O como dice Juanka, no hay que ser bueno por ponerse ahí delante, sinó un buen par.

## Event Storming

Hace un tiempo hice una [charla introductoria] sobre la metodología **Event Storming**, 
donde presenté el contenido de [mis slides][mis slides eventstorming]. Estas slides resumen
la experiencia con mi equipo de trabajo, aprendiendo de forma autodidacta.
Como añadido, al final de las slides hay unos consejos para quien quiera aprender a 
facilitar sesiones de Event Storming.

Ahora ya iba siendo hora de compartirlo y montar una sesión práctica. Esta tenía
que ser para todos los públicos, incluyendo asistentes que no sabían nada al respecto.

Procedimos a limitar la sesión a 33 participantes, pues podía contar con dos compañeros de trabajo,
Dani y Christian, para facilitar hasta 3 grupos de hasta 8-9 personas cada uno (el máximo establecido 
según la propia metodología).

Reservamos un aula en el Campus Sescelades de la [URV] donde poder realizar la sesión, y ya
sólo faltaba que llegase el día.

Finalmente fuimos 14 asistentes, 2 facilitadores (Dani y yo) y 12 participantes. Fue todo un reto.
Hasta la fecha habíamos facilitado sesiones con grupos de hasta 3 participantes.

Montamos una sesión práctica introductoria, donde cada grupo lo pusimos delante del siguiente
escenario:

1. Quieren montar un servicio de venta online con carrito de la compra de un producto
o servicio.
1. Cada grupo tenía que decidir qué vendía. De aquí salieron los grupos:
   * `Aceide de oliva`, con producción propia.
   * `Vino`, de compra-venta de vino mundial, y artículos relacionados.
1. Distribuimos a los participantes no técnicos homogéneamente entre los dos
grupos, y asumieron el rol de negocio (stakeholders).
1. Cómo sólo había uno de negocio por grupo, pedimos que otro miembro de cada grupo
asumiera el rol de negocio.
1. Esta primera sesión práctica les serviría para dibujar la `big picture`, o
las líneas en alto nivel de su negocio.
1. Mantuvimos 3 rondas de 15 minutos, con unos 7 minutos de reorganización.
1. Para motivar que todo el mundo pusiera post-its, añadimos la regla de gamificación
en la que cada uno debía añadir un mínimo de 3 post-its durante la primera ronda.

Las dos horas pasaron volando: entre presentación del Meetup por parte de Adri, introducción
breve a Event Storming, presentación de las reglas de juego y las diferentes rondas, el 
resultado fue el siguiente en cada uno de los grupos:


Grupo `Aceite de Oliva`

![Resultado big picture del grupo Aceite de Oliva](/img/grupo_aceiteoliva_400x300.jpg)

Grupo `Vino`

![Resultado big picture del grupo Vino](/img/grupo_vino_400x300.jpg)

## Conclusiones y lecciones aprendidas

Lo que nos percatamos Dani y yo fue de lo siguiente:

1. La regla sencilla de gamificación de poner 3 post-its por participante fue todo un éxito.
Todo el mundo la cumplió en seguida y en la primera ronda.
1. La escritura en `participio` de los `eventos` se adquirió en seguida, con algunas excepciones.
1. En seguida aparecieron diferentes términos para un mismo concepto. Entonces, el `ubiquitous
language` vino al rescate para unificar un término con un significado.
1. La lectura de derecha a izquierda dio otro punto de vista a los participantes. Sobre todo
cuando se les planteaba cuestiones del estilo: `¿sólo a este evento 2 llegamos desde este evento 1?`.
1. Detectamos confusión entre secuencia lógica de eventos (de izquierda a derecha) y 
paralelismo de eventos (de arriba a abajo en la misma vertical). Debemos recordar en estos casos que
un evento puede promover que aparezcan nuevos eventos, e incluso varios a la vez, con su propia
secuencia.
1. Para los más técnicos aparecieron las dudas típicas de plasmar bucles y condicionales en
Event Storming. Tomamos las siguientes convenciones:
   * Los `condicionales` (if-then-else) los pusimos como diferentes post-its, con el `happy path`
   en la misma línia de izquierda a derecha, y los otros casos excepcionales en diferentes alturas
   (encima o debajo del happy path).
   * Los `bucles` pueden ser debidos a diferentes motivos. Por ejemplo, por las acciones de usuario 
   cuando añade diferentes artículos al carrito de la compra. Los bucles ya quedan reflejados
   en el propio happy path, y acordamos no reflejarnos de ningún modo.
1. Con 6 participantes por grupo, en seguida aparecieron dos grupos simultáneos, con diferentes
dinámicas entre si. Como facilitadores debemos motivar la colaboración y dinámicas saludables
y acuerdos, sin contradicciones. Motivamos las siguientes dinámicas y sinergias:
   1. Si una discusión no era enriquecedora, generadora de conocimiento, sino de contraposición de
   opiniones, se corta la discusión y se establece a un portavoz para que genere una solución. Luego
   se debate sobre la solución con la secuencia propuesta de eventos.
   1. Si un miembro del grupo no comparte la opinión de lo que expresan los eventos, preguntamos
   quien puso esos eventos y promovemos la generación del conocimiento preguntando el `¿por qué?`.
   Hay que evitar que unos muevan libremente los eventos propuestos por otros. Eso no es generar 
   conocimiento, sinó plasmar una opinión.
   1. Cuando un grupo, experto en una parte del problema, considera que ha terminado de proponer
   eventos en su zona de experiencia, debemos promover que revisen el resto del sistema, para 
   valorar posibles vínculos con su experiencia, o añadir conocimiento o refinamiento en el resto
   del sistema.
1. Hay que llevar muchos post-its. Como los naranjas para eventos, como propone Alberto Brandolini, 
son escasos y cuestan de encontrar, acordamos usar los amarillos para eventos. Más allá de los que 
queden en la foto final, hay que contar con la reescritura para unificación según el `ubiquitous
language`, por reenfoque de la línea de negocio, y sobre todo evitar tachones que previenen su
correcta lectura.
1. Propusimos que trajeran un bolígrafo por cabeza para escribir en los post-its, 
aunque vimos que es mucho más legible con un rotulador. Josep Ma lo trajo y se notó la diferencia.
1. Cómo facilitadores, tragimos post-its azules en previsión de si llegábamos a poner `commands`
después de los eventos. Vimos que finalmente no llegamos a ello, y que en próximas ocasiones 
seremos más conservadores con las expectativas.

## Agradecimientos

Quiero agradecer al Meetup que nos dejaran realizar la sesión práctica de Event Storming.
Enseñando se aprende, y nosotros aprendimos mucho.

Gracias también a Dani por liarse en seguida en esta aventura, y por toda su ayuda en todo el proceso.

Por último, gracias a todos los que asististeis al Meetup, que pusieron todas las ganas de
participar, compartir y aprender entre todos.

Nos vemos en próximos meetups!

[Meetup Tarragona Developers]: https://www.meetup.com/Tarragona-Developers-Meetup/
[charla introductoria]: https://www.meetup.com/Tarragona-Developers-Meetup/events/251019288/
[handson]: https://www.meetup.com/Tarragona-Developers-Meetup/events/257666172/
[mis slides eventstorming]: https://jpahullo.github.io/slides/eventstorming/
[URV]: https://www.urv.cat
