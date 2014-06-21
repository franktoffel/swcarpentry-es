swcarpentry-es
==============

Este repositorio pretende ser un punto de partida para la traducción de las lecciones de http://software-carpentry.org/lessons.html

### Motivación

[Software Carpentry](http://software-carpentry.org/) tiene como misión enseñar a los investigadores habilidades básicas informáticas aplicables en el ámbito científico: las herramientas y técnicas que ayudarán a hacer más cosas en menos tiempo y de forma menos dolorosa. Los instructores son voluntarios y han impartido más de un centenar de eventos a miles de científicos en los últimos dos años y medio. Todos los materiales de las lecciones son libremente reutilizables bajo la licencia [Creative Commons](http://creativecommons.org/licenses/by/3.0/es/deed.es),
Sin embargo, el contenido está escrito en inglés y supone un grado de dificultad añadido para todo aquel que quiera empezar a aprender. El **objetivo de esta traducción** es facilitar los primeros pasos, no traducir toda la información relacionada.

### ¿Cómo colaboro?

Dada la relativa complejidad del [contenido original](https://github.com/swcarpentry/bc), se ha optado por crear este repositorio independiente.

Utilizaremos GitHub para la coordinación. Si tus conocimientos de esta plataforma son limitados, te recomendamos que leas la lección de SW Carpentry dedicada [al software de control de versiones](http://software-carpentry.org/v5/novice/git/index.html).

La mayor parte del contenido se puede editar directamente en GitHub como texto plano ya que sigue un formato tipo Markdown([guía rápida de Markdown](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)).

Existen también lecciones de Python y SQL que están escritas en Notebooks de IPython. Si desconoces IPython Notebook, dale un vistazo a este [curso de introducción a Python](http://cacheme.org/curso-online-python-cientifico-ingenieros/) (y [cómo instalarlo](http://cacheme.org/curso-online-python-cientifico-ingenieros/)).

El contenido se divide en los siguientes temas, entre paréntesis se indica si han sido asignados a algún voluntario están libres:

* [Introduction](http://software-carpentry.org/v5/intro.html) (preasignado)
*	[The Unix Shell](http://software-carpentry.org/v5/novice/shell/index.html)  (preasignado)
*	[Version Control with Git](http://software-carpentry.org/v5/novice/git/index.html)  (¡libre!)
*	[Programming with Python](http://software-carpentry.org/v5/novice/python/index.html) (preasignado)
*	[Using Databases and SQL](http://software-carpentry.org/v5/novice/sql/index.html) (¡libre!)
*	[A Few Extras](http://software-carpentry.org/v5/novice/extras/index.html) (¡libre!)
*	[Instructor's Guide](http://software-carpentry.org/v5/novice/teaching/index.html) (¡libre!)

Nota: Para escoger la que más te guste accede a la [página de Issues](https://github.com/franktoffel/swcarpentry-es/issues?state=open).

###  Guía de estilo

El resultado de estas traducciones será hospedado en la página oficial de Software-Carpentry.org por las **traducciones deben ser lo más fidedignas a la versión original**. Por ello, es preferible utilizar los mismos ejemplos de código (en inglés) y explicar el significado con comentarios (en el código o de forma posterior). Las palabras técnicas también se mantendrán en inglés poniendo su traducción al español la primera vez que aparezcan.

El **objetivo** es facilitar el aprendizaje en los primeros pasos, pero también a familiarizarse con el vocabulario técnico en inglés que es la *lingua franca de la informática*. 

Los archivos e imágenes del contenido original mantendrán su nombre, y estructura pero en la carpeta `translations/es/` creada a tal efecto.

La idea principal es actualizar el repositorio con los cambios que hagan en el original y al actualizar cada fichero - cada commit - haciendo referencia al último número del commit del original.
Haciendo esto, cuando algo cambie en algún fichero podemos ver a que línea se refiere.

#### Ejemplo, traducción de `01-shell.md`:

Se copia la lección (y, si lo tiene, el contenido necesario para la misma) del original, en este caso:

Vamos a,
`franktoffel/swcarpentry-es/novice/shell/01-shell.md`

y copiamos todo el contenido que vayamos traduciendo dentro de la ruta `translations/es` pero manteniendo la misma estructura y nombre de archivo. Así, para el ejemplo, quedaría como:

`franktoffel/swcarpentry-es/translations/es/swcarpentry-es/novice/shell/01-shell.md` 

Ahora, cuando hagamos el commit de dicho fichero traducido se pone algo como:

`[es] - Translation of 01-shell.md based on a6fd62d2ba`

Ese número se ve en el log de cada fichero con 'git log fichero' o en la página de history del repositorio.

Así, cuando hay nuevas actualizaciones los traductores podemos ver que ha cambiado directamente en la página de git, por ejemplo:
https://github.com/franktoffel/swcarpentry-es/commit/a6fd62d2baffad9d41f7391c1ddfd4d37ad3048f

De esta forma, si se realizan cambios, podremos detectarlos y comparar ambas versiones. Finalmente se mandará un pull request a la repo original con los archivos traducidos.

### Colaboradores

* Fran Navarro - [@franktoffel](https://github.com/franktoffel), coordinación.
* David PS [@dpshelio](https://github.com/dpshelio), Linux Shell.
* Javier J. Gutiérrez [@javierj](https://github.com/javierj), revisión.
* Daniel Domene y Zuri Bauer, Python.
* Jorge Bernabé, introducción.

###  Contacto

La organización de estas traducciones las realiza Fran Navarro de [CAChemE.org](http://cacheme.org), puedes contactar con nosotros mediante el [formulario de contacto](http://cacheme.org/contacto/).

Disclaimer
---------
¡Te recordamos que esto es una labor de voluntarios y cualquier ayuda, pull request, crítica o sugerencia son bienvenidas! 
