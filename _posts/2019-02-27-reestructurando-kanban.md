---
layout: post
section-type: post
title: "Reestructurando tu kanban"
description: >-
  Cambio en el uso del kanban para reflejar mejor las necesidades en 
  tu día a dia
category: technical
tags: [ 'agile', 'kanban' ]
image: /img/kanban.jpg
---

Sacándole más provecho a nuestro Kanban!

<!--excerpt-->

Antes de entrar en materia, permitidme mostraros cómo funcionamos
y cuál es nuestra estructura, para así ayudar a entender mejor
el porqué de cómo lo usábamos y cómo hemos pasado a usarlo.

## Contexto

En el [SREd] usamos internamente el [Kanban] en los proyectos
técnicos, principalmente en aquello relativo al conjunto de 
aplicaciones que forman el Campus Virtual de la [URV], con el
[Campus Virtual URV] (Moodle) como el gran referente.

El equipo técnico y expertos funcionales usamos una herramienta
[Kanban] para ayudarnos a visualizar y priorizar lo que tenemos
entre manos.

Además, cabe señalar que nuestro equipo técnico de 3 personas
nos encargamos de realizar principalmente tareas de mantenimiento,
integración de servicios y resolución de problemas en cualquiera
de las aplicaciones del Campus Virtual. Por este motivo, y por 
poner un ejemplo, cuando
el Moodle no funciona por cualquier motivo, las alertas saltan
y alguno de nosotros (o más de uno según sea el caso) nos 
arremangamos y analizamos (incluso a nivel forense) lo que está 
pasando, coordinándonos immediatamente con el resto del equipo
informático del [SRITIC].

Por tanto, nuestro día a día, sino hay interrupciones por cuestiones en
producción, es de mantenimiento y mejora de los procesos 
existentes, tendiendo a añadir mejor experiencia de uso a los 
usuarios, reducción de bugs heredados (legacy code) y adaptación
e integración de servicios.

Usamos sprints semanales. Ello viene dado porque tenemos que adaptarnos
al cambio de prioridades en las tareas y bugs detectados en 
producción. Todo ello está en nuestro funcionamiento normal del día a día.
Con el sprint semanal nos permite adaptarnos a todo ello, teniendo
cierta calma dentro de cada semana, requisito para tener un mayor
grado de productividad y eficiencia de los recursos.

Y siempre seguimos la filosofía **pull** para selección de tarea nueva: 
es el técnico el que elige la tarea a desarrollar,
siguiendo las prioridades establecidas. Y si hay varias con la misma prioridad, el técnico 
puede elegir cualquiera de ellas. Entre nosotros no nos aplicamos filosofía push, 
designando quién debe atender qué tarea.


## Kanban

Permitidme expresar lo que es [Kanban] para mi, sin usar una definición formal:

* Es una metodología ágil.
* Permite visualizar en un solo lugar en forma de plafón toda tarea en la que tu equipo está trabajando.
* El plafón Kanban puede materializarse en una herramienta analógica o digital.
* Para ello se definen unas columnas que expresan el flujo de trabajo, vinculadas a las fases por las que
pasa cualquier tarea.
* Las tareas se muestran como postits que se mueven de la columna de la izquierda hasta la 
de más a la derecha.
* Cuando una tarea llega a la columna de más a la derecha, la tarea se considera completada.

Además de todo aquella ayuda visual, que no es poca, también sirve para:

* Ajustar el número de columnas y orden. 
* Definir límites WIP (Work in progress). Con ello definimos el número máximo de
tareas que tendremos en una columna.

Cualquier metodología ágil es ágil en si, con lo cual tiene un margen para permitir
la adaptación de la misma a las nuevas necesidades del equipo.

En nuestro caso particular, por ejemplo, hemos añadido alguna que otra regla:

* Aquella tarea que requiera nuestra atención que esté situada más a la derecha tiene
mayor prioridad para proseguir con su desarrollo. Una vez ya no requiera nuestra atención
seguimos con la siguiente tarea de mayor prioridad. Si resulta que estamos libres, cogemos 
una nueva tarea.

Con todo esto, si aprovechamos para cuantificar el esfuerzo previsto que cada tarea nos
va a requerir, al final de cada sprint tendremos aquello completado en la columna de más a 
la derecha. Si sumamos las magnitudes del esfuerzo previsto completado, obtendremos 
la medida de lo que tu equipo es capaz de afrontar por sprint.


## Cómo usábamos Kanban

Teníamos 6 columnas en nuestro Kanban, con el siguiente funcionamiento:

| Product Backlog | Sprint Backlog | Developing | Peer Review | Testing | Done |
|----|----|----|----|---|---|
| Aquí todo aquello pendiente por realizar, sin priorización alguna | Aquello priorizado para el sprint actual | Aquellas tareas asignadas y bajo desarrollo | Tareas desarrolladas pendientes de revisión por un igual, diferente al que lo desarrolló | Tareas revisadas a nivel técnico, pendientes de revisión por una tercera persona a nivel funcional | Tarea completada |

Cada semana priorizábamos tareas y actualizábamos la columna `Sprint Backlog`, 
según la candidad de esfuerzo previsto que podemos completar.

Esto tenía sus pros y contras:

Pros:

* Tenemos muy claro el objetivo a completar por sprint: todo aquello no completado
incluido en todas las columnas, exceptudando la `Product Backlog`. 

Contras:

* En cada sprint hay que actualizar el `Sprint Backlog` según las nuevas prioridades.
* No podíamos predecir para cuando podía estar completada una tarea. Sólo podíamos anunciar 
cuándo la íbamos a empezar.
* No hay una visión de camino, hacia dónde se dirige este equipo con este proyecto.

## Cómo usamos ahora Kanban

| Product Backlog | Developing | Peer Review | Testing | Done |
|----|----|----|----|---|
| Tareas priorizadas | Aquellas tareas asignadas y bajo desarrollo | Tareas desarrolladas pendientes de revisión por un igual, diferente al que lo desarrolló | Tareas revisadas a nivel técnico, pendientes de revisión por una tercera persona a nivel funcional | Tarea completada |
| Tareas sin priorizar | | | | |

Hemos quitado una columna! Ya no tenemos `Sprint Backlog`. Y esto, ¿por qué?

Pros:

* Sabemos lo que hay que completar, todo aquello que hay en todas las
columnas, incluyendo aquello priorizado del `Product Backlog`. Ahora el concepto es lo que hay que
ir desarrollando y en qué prioridad; ya no se refiere a un conjunto de tareas concretas a finalizar
según el esfuerzo previsto de completación.
* Podremos empezar a predecir para cuando una tarea se va a poder completar. Inclusive 
en situaciones donde tengamos emergencias en producción y tengamos que dejar nuestras
tareas.
* Simplifica la gestión de las priorización de las tareas.
* Ayuda a visualizar la línia de trabajo (medio plazo) dentro de ese proyecto, pues las tareas
en `Product Backlog` se pueden ir acumulando debidamente priorizadas.
Usamos un kanban por proyecto.
* Seguimos visualizando y midiendo el trabajo previsto completado en la columna `Done`.

Y con un par de semanas de aplicación, aún no le hemos visto pegas a este enfoque.

Aún no hemos llegado a predecir el tiempo de completación de tareas, pero estamos en camino.

## Agradecimientos

Quiero agradecer a [Josep Ma. Rocamora] el tiempo compartido en los meetups de Tarragona,
así como especialmente nuestro encuentro en la [CAS 2018] en donde Josep Ma. 
me sugirió este cambio. De hecho, estamos pendientes que nos haga una formación
para ahondar aún más en todos estos aspectos.

Josep Ma. es Scrum Master y experto agilista. No dudéis en 
contactarle si tenéis cualquier duda en vuestra empresa o unidad de trabajo. Os lo recomiendo!


## Conclusión

No importa si usas una metodología u otra. Si estás interesado en la agilidad,
ten en cuenta esta frase que acuñé en una conversación informal:

> 
> La agilidad, al igual que la felicidad, no es una meta, sino un camino.
>

[SREd]: http://www.sre.urv.cat
[Kanban]: https://es.wikipedia.org/wiki/Kanban_(desarrollo)
[Campus Virtual URV]: https://campusvirtual.urv.cat
[URV]: https://www.urv.cat
[SRITIC]: http://www.urv.cat/es/universidad/estructura/gestion/apoyo-actividad/recursos-informaticos-tic/
[Josep Ma. Rocamora]: https://twitter.com/AgileTgn
[CAS 2018]: https://cas2018.agile-spain.org/
