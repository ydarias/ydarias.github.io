---
layout: post
title: La empresa es mía y la organizo como me da la gana
date: '2014-12-14T16:21:00.000Z'
author: Yeray Darias
tags: [agile, work, spanish]
modified_time: '2014-12-14T16:21:23.412Z'
feature_image: images/mi-trello.png
---

Mis listas de artículos para leer en Pocket o de ideas sobre las que escribir, poco a poco, tienden al infinito. Desgraciadamente no tengo el tiempo o mejor dicho las ganas para escribir en el blog tanto como debería, pero no hay nada que la manía de David Bonilla de bromear por Twitter no pueda conseguir.

<blockquote class="twitter-tweet"><p lang="es" dir="ltr">El nivel de &quot;caos organizado&quot; en Otogami es TAL, que <a href="https://twitter.com/ydarias?ref_src=twsrc%5Etfw">@ydarias</a> usa un Trello a escondidas -para él solo- para que no le estalle la cabeza ^_^</p>&mdash; David Bonilla (@david_bonilla) <a href="https://twitter.com/david_bonilla/status/543358137089417217?ref_src=twsrc%5Etfw">December 12, 2014</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script> 

Y no es sólo que escriba algo en Twitter y quedé ahí por los tiempos de los tiempos, sino que esa acción que para él dura unos segundos tiene repercusiones durante días. Pues bien, tendré que explicar porqué razón uso un Trello personal en mi día a día y cómo afecta eso a la organización del trabajo en Otogami Technologies S.L.

<!--more-->

## Otogami no es sólo Otogami

Sí, habéis leído correctamente, yo no trabajo exactamente para Otogami.com sino para Otogami Technologies S.L. que parece lo mismo pero no lo es. ¿Cuál es la diferencia? pues que la primera es un producto y la segunda es la empresa tras el producto.

Como empresa, necesitamos una organización y esa es la que llevamos en el Jira "coorporativo", a nivel general y de la que todos tenemos constancia, es lo que denominaremos como organización del equipo. Hay que tener en cuenta que la empresa, pese a estar compuesta únicamente por 5 personas, tiene diferentes departamentos y varios productos, por lo que en ese Jira hemos decidido no poner detalles de como se realiza cada historia de usuario, funcionalidad, tarea o como lo queramos llamar. Simplemente es algo que tiene la prioridad necesaria para que debamos hacerlo en el momento actual, algunas cosas son tareas y otras se definen como historias de usuario.

Cada persona hace labores de distintos departamentos, pero si nos enfocamos en mi ámbito de conocimiento, que es ingeniería, dos personas estamos dividas para la construcción de cada producto. Jero se encarga de Otogami y yo de Runnics. El porqué es así y no de otra manera no lo voy a explicar aquí porque es un artículo por si mismo, pero es así, nos funciona y yo tengo que gestionarme teniendo esto en cuenta. Eso es a lo que denominaremos organización personal, básicamente porque yo sólo soy una persona. ¿Un equipo de una persona?, sí, a veces pasa.

## Todas las tareas son del proyecto, ¿no?

En este punto y si estamos de acuerdo en que es mi organización personal, y por extensión la de Runnics, yo lo gestionaré como crea adecuado y con las herramientas que mejor me sirvan. Y así respondemos a porqué uso Trello, una aplicación sencilla y que cuando es necesario puedo usar de forma colaborativa, que me permite ir al detalle de grano fino de las cosas que debo hacer, sin añadir más complejidad a mi trabajo. Jira es una gran herramienta, pero muy compleja para la gestión de lo que por ahora es un equipo de una sóla persona.

<blockquote class="twitter-tweet"><p lang="es" dir="ltr"><a href="https://twitter.com/ydarias?ref_src=twsrc%5Etfw">@ydarias</a> <a href="https://twitter.com/david_bonilla?ref_src=twsrc%5Etfw">@david_bonilla</a> era pq cada uno hacemos siempre lo q nos funcione mejor pero siendo estrictos todas las tareas son del proyecto, no?</p>&mdash; Ricardo Varela (@phobeo) <a href="https://twitter.com/phobeo/status/543391068122021888?ref_src=twsrc%5Etfw">December 12, 2014</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script> 

Cuando otra persona necesita saber en que estoy trabajando lo puede ver en el Jira general, pero si quiere saber cuánto me queda de mi labor actual tiene que hacer lo que es más coherente, preguntarme a mi, y yo puedo ir a mi Trello y ver que tareas me faltan para completar la historia de usuario con la que estoy ahora. Por lo tanto sí, son tareas del proyecto, y están en el panel del proyecto, que es mi Trello, pero esas tareas generalmente tienen un caríz técnico en el que otras personas pueden no estar interesadas, por lo que llenar el Jira con esas tareas no mejoraría nada sino que haría que fuese más difícil de leer.

Dejadme poner un ejemplo para que se vea de forma más clara. Un lunes nos reunimos todos y reorganizamos nuestras prioridades, de donde, por ejemplo, sale una de las historias de usuario con las que trabajaré más adelante.

* Como runnics/empresa quiero que los usuarios puedan comentar una zapatilla para que se genere más contenido por ficha de zapatilla y Google nos posicione mejor en el ranking, trayendo más tráfico a la web y por lo tanto mejorando las ventas.

Para nosotros se trata de una historia de usuario clara y con un objetivo bien definido que queremos alcanzar, pero para hacerla o no, además de la importancia que tenga o su valor como historia de usuario, necesitamos una estimación temporal de cuánto más o menos puedo tardar en completarla. Es en este punto y mientras sigo hablando con Jero y con David sobre lo que podemos hacer, cuando descompongo esa historia en detalles técnicos.
 
* Incluir Disqus como sistema de comentarios en la ficha de zapatilla.
* Recuperar cada x minutos los nuevos comentarios de Disqus para almacenarlos en nuestra BD.
* Precargar los últimos x comentarios de una zapatilla para que Google lo pueda leer con sus robots y detecte que hay más contenido.

Ahora puedo dar una estimación mejor y estas tareas las incluyo en mi tablón de Trello. Pero además hay que tener en cuenta que mientras implemento la funcionalidad pueden salir nuevas tareas. Ir anotandolas me ayuda a que no se me olviden, porque no siempre son tan importantes como para que las recuerdes, pero son igualmente necesarias.

* Revisar la internacionalización de Disqus para que los textos aparezcan en castellano.

Y esta es la forma en la que voy controlando el desarrollo de producto.

## Conclusión
Después del ladrillo y para resumir, las respuestas a las preguntas que han surgido son las siguientes.

### ¿Eso no os iría mejor tenerlo en compartido, por visibilidad del equipo?

Sí, sin dudas, y lo tenemos porque el equipo soy yo sólo. Todos somos la empresa no el equipo de desarrollo de Runnics ^_^

### ¿Siendo estrictos todas las tareas son del proyecto, no?

Nuevamente sí, pero la respuesta es la misma que antes, el proyecto tiene todas sus tareas representadas en el tablón de Trello. Jira se usa para la gestión de la empresa completa.

### ¿Por qué Trello y no Jira, qué diferencias hay?

Pues hay muchas diferencias pero la razón por la que utilizo Trello son las siguientes.

* Es muy muy fácil de usar.
* Se puede usar "out of the box", mientras que Jira suele necesitar una configuración más compleja.
* Funciona y carga más rápido que Jira on demand.

Cierto, tienes menos funcionalidades, pero me sirve muy bien para la fase en la que estamos.
