---
layout: lesson
root: .
title: Introduction
---

Este es el sueño:

> Los ordenadores han revolucionado la investigación, y esta revolución
> está únicamente empezando. Cada día, científicos e ingenieros de todo
> el mundo los emplean para estudiar cosas que son demasiado grandes,
> demasiado pequeñas, demasiado rápidas, demasiado lentas, demasiado caras,
> demasiado peligrosas, o simplemente demasiado difíciles para estudiar de otra manera.

Ahora, esta es la realidad:

> Cada día, los científicos e ingenieros de todo el mundo desperdician
> su tiempo peleándose con los ordenadores. Tareas que deberían realizarse
> en unos pocos minutos, tardan horas o días en llevarse a cabo, y muchas
> cosas no terminan de funcionar correctamente. E incluso cuando las cosas funcionan,
> la mayoría de los científicos no tienen ni idea de cómo de fiables son los resultados.

El mayor dolor de cabeza de los investigadores proviene de no saber cómo desarrollar software de forma sistemática, cómo determinar si sus programas están funcionando correctamente, cómo compartir su trabajo con otros (excepto por archivos adjuntos vía email) o cómo monitorizar los avances que han hecho. Esta situación persiste por cuatro razones:

*   *Sin espacio, sin tiempo.*
    La agenda de todo el mundo está llena, simplemente no hay espacio para añadir más sobre computación científica sin tener que decir que no a alguna otra cosa.

*   *Sin estándares.*
    Los reviewers y agencias que subvencionan proyectos no comprueban si el software es correcto, preguntan cuánto llevo escribirlo o lo valoran según antigüedad, con lo que no hay incentivos para que los científicos lo hagan mejor.

*   *El ciego guiando a los ciegos.*
    Los investigadores senior no pueden enseñar a la siguiente generación cómo hacer cosas que ellos no saben hacer por sí mismos.

*   *El culto al poder.*
    La atención y los fondos van mayoritariamente hacia cosas de las que los políticos y los rectores de universidades puedan alardear en inauguraciones, más que a las habilidades básicas que casi todo el mundo emplea.

Nuestra misión es enseñar a los investigadores habilidades básicas informáticas aplicables en el ámbito científico, herramientas y técnicas que ayudarán a hacer más cosas en menos tiempo y de forma menos dolorosa. Los instructores son voluntarios y han impartido más de un centenar de eventos a miles de científicos en los últimos dos años y medio. Todos los materiales de las lecciones son libremente reutilizables bajo la licencia Creative Commons, Sin embargo, el contenido está escrito en inglés y supone un grado de dificultad añadido para todo aquel que quiera empezar a aprender. El objetivo de esta traducción es facilitar los primeros pasos, no traducir toda la información relacionada.

Nuestra meta es mostrar a los científicos e ingenieros cómo hacer más en menos tiempo y de forma menos dolorsa. Nuestras lecciones han sido empleadas por más de cuatro mil principiantes en alrededor de cien talleres de dos días desde la primavera de 2010.

Así es como te ayudamos:

*   Si alguna vez has sobreescrito el archivo erróneo, te mostraremos cómo emplear un controlador de versiones (*version control*).
*   Si alguna vez has pasado horas escribiendo los mismos comandos una y otra vez, te mostraremos cómo automatizar estas tareas empleando scripts simples.
*   Si alguna vez has pasado una tarde intentando descubrir lo que el programa que escribiste la semana pasada realmente hace, te mostraremos cómo dividir tu código en módulos que puedas leer, eliminar errores (*bugs*) y mejorarlo bloque por bloque.
*   Si alguna vez has pasado días copiando y pegando información en archivos de texto y hojas de cálculo, te mostraremos cómo una base de datos puede hacer el trabajo por ti.

### Sobre nosotros

Software Carpentry es un proyecto *open source* (código abierto).
Nuestros instructores son voluntarios y todas las lecciones son libremente reutilizables bajo licencia [Creative Commons - Atribución](http://creativecommons.org/licenses/by/3.0/es/deed.es), por lo que puede reutilizar y modificar todo el material teniendo solo que citarnos como fuente original.

Como todos los proyectos con voluntarios, Software Carpentry necesita tu ayuda para crecer. Si encuentras un *bug* (fallo), por favor envía un informe a [nuestro repositorio en GitHub](https://github.com/swcarpentry/bc/). Si te gustaría realizar un taller en tu centro, por favor [ponte en contacto con nosotros](mailto:admin@software-carpentry.org); si te gustaría enseñar, tenemos un [curso de preparación para instructores](http://teaching.software-carpentry.org); y si te gustaría escribir lecciones o ejercicios, por favor [háznoslo saber](mailto:admin@software-carpentry.org).

Para descubrir más, por favor visita [Software-Carpentry.org](http://software-carpentry.org) o lee 
[estos](http://www.plosbiology.org/article/info%3Adoi%2F10.1371%2Fjournal.pbio.1001745)
[papers](http://arxiv.org/abs/1307.5448)
o [las entradas del blog más pupulares](http://software-carpentry.org/blog/index.html#popular) (enlaces en Inglés).

### Agradecimientos

Software Carpentry ha sido possible gracias al generoso apoyo de: 

*   [Continuum Analytics](http://continuum.io/)
*   [Indiana University](http://www.indiana.edu)
*   [Lawrence Berkeley National Laboratory](http://www.lbl.gov)
*   [Los Alamos National Laboratory](http://www.lanl.gov)
*   [MathWorks](http://www.mathworks.com)
*   [Michigan State University](http://www.msu.edu)
*   [Microsoft](http://www.microsoft.com)
*   [MITACS](http://www.mitacs.ca)
*   [The Mozilla Foundation](http://mozillafoundation.org)
*   [The Python Software Foundation](http://www.python.org/psf/)
*   [Queen Mary University of London](http://www.qmul.ac.uk)
*   [Scimatic Software](http://www.scimatic.com)
*   [SciNet](http://www.scinet.utoronto.ca)
*   [SHARCNET](http://www.sharcnet.ca)
*   [The Alfred P. Sloan Foundation](http://www.sloan.org)
*   [The Space Telescope Science Institute](http://www.stsci.edu)
*   [The UK Meteorological Office](http://www.metoffice.gov.uk)
*   [The University of Alberta](http://www.ualberta.ca)
*   [The University Consortium for Atmospheric Research](http://www.ucar.edu)
*   [The University of Toronto](http://www.utoronto.ca)

Gracias especialmente a Brent Gorda,
quien ayudó a construir y enseñear la primera versión de este curso.

### Traducción

Las lecciones de este curso han sido traducidas del Inglés por [voluntarios](https://github.com/franktoffel/swcarpentry-es/tree/master/translations/es#colaboradores) y tienen como objetivo facilitar (que no sustituir) la versión original de las mismas. 

<div align="center" markdown="1">
Este libro está dedicado a
[Betty Jennings](http://en.wikipedia.org/wiki/Jean_Bartik),
[Betty Snyder](http://en.wikipedia.org/wiki/Betty_Holberton),
[Fran Bilas](http://en.wikipedia.org/wiki/Frances_Spence),
[Kay McNulty](http://en.wikipedia.org/wiki/Kathleen_Antonelli),
[Marlyn Wescoff](http://en.wikipedia.org/wiki/Marlyn_Meltzer),
y [Ruth Lichterman](http://en.wikipedia.org/wiki/Ruth_Teitelbaum),
<br/>
los programadores originales de [ENIAC](http://en.wikipedia.org/wiki/ENIAC).
</div>
