---
layout: lesson
root: ../..
title: Introducción a la Terminal
---
<div class="objectives" markdown="1">

#### Objectivos
*   Explicar cómo la *shell* (terminal) relaciona el teclado, la pantalla, el sistema operativo y los programas del usuario.
*   Explicar cuándo y por qué la shell se deberían usar en vez de interfaces gráficas.

</div>

Nelle Nemo, un biólogo marino,
acaba de regresar de una expedición de 6 meses del
[Giro del Pacífico Norte](http://es.wikipedia.org/wiki/Giro_oce%C3%A1nico#Mayores_giros),
donde ha estado tomando muestras de la vida marina gelatinosa en el
[Gran mancha de basura del Pacífico](http://es.wikipedia.org/wiki/Sopa_de_pl%C3%A1stico).
Ha obtenido 300 muestras en total y ahora necesita:

1.  Pasar cada muestra a través de una máquina de ensayos
    que medirá la abundancia relativa de 300 proteínas diferentes.
    La máquina produce por cada muestra un
    archivo con una línea para cada proteína.
2.  Calcular las estadísticas para cada una de las proteínas por separado
    empleando un programa que su supervisor escribió llamado `goostat`.
3.  Comparar las estadísticas para cada proteína
    con las correspondientes estadísticas  para cada otra proteína
	empleando `goodiff`, un programa que otro estudiante de doctorado escribió.
4.  Redactar un artículo.
    A su supervisor realmente le gustaría que terminara esto a finales de mes
    para que su artículo pueda aparecer en la siguiente edición especial de *Aquatic Goo Letters*.

La máquina de ensayos tarda media hora en procesar cada muestra.
La buenas noticia es
que sólo tarda dos minutos en preparar cada una.
Como su laboratorio tiene ocho máquinas de ensayos, ella puede usarlas en paralelo
y este paso le llevará "sólo" dos semanas.

La mala noticia es que si ella tiene que ejecutar `goostat` y `goodiff` a mano,
tendrá que escribir los nombres de los archivos y pulsar "OK" 45150 veces
(300 ejecuciones para `goostat`, más 300&times;299/2 ejecuciones de `goodiff`).
Si le lleva 30 segundos para cada uno de ellas,
este proceso le llevará más de 2 semanas.
No solo se pasaría de la fecha límite de entrega del artículo,
sino que las probabilidades de que ella escriba correctamente todos y cada uno de los comandos son prácticamente cero.

Las siguientes lecciones explorarán lo que ella debería hacer en vez de lo anterior.
Más específicamente,
explican cómo se puede emplear un comando shell
para automatizar pasos repetitivos en el transcurso de su proyecto
consiguiendo que su ordenador pueda trabajar 24 horas al día mientras ella escribe su artículo.
Además,
una vez que ella haya puesto su trabajo junto,
será capaz de emplearlo de nuevo cuando colecte nuevas muestras.

### Qué y por qué

A modo de resumen, los ordenadores hacen cuatro cosas:

-   Ejecutar programas,
-   almacenar información,
-   comunicarse entre ellas, e
-   interactuar con nosotros.

Pueden hacer el último punto de esta lista de diversas maneras,
incluyendo enlaces directos con nuestro cerebro e interfaces habladas. 
Como estas están aún su infancia,
la mayoría de nosotros usa ventanas, iconos, el ratón y punteros.
Estas tecnologías no se generalizaron hasta los ochenta,
pero sus raíces se remontan al trabajo de Doug Engelbart en los sesenta,
que puedes ver en lo que ha sido llamado
"[La madre de todos los demos](http://www.youtube.com/watch?v=a11JDLBXtPQ)".

Yendo incluso más atrás,
la única manera de interactuar con los primeros ordenadores era recableándolos.
Pero entre medias,
desde los años cincuenta hasta los ochenta,
la mayoría de la gente usaba impresoras de líneas.
Estos aparatos sólo permitían la entrada y salida de letras, números y la puntuación encontrada en un teclado estándar,
con lo que los lenguajes de programación y las interfaces tenían que ser diseñadas alrededor de esta restricción.

Este tipo de interfaz se denomina
[*command-line interface*](../../gloss.html#cli)(interfaz de línea de comandos), o CLI,
para distinguirlo de la
[*graphical user interface*](../../gloss.html#gui)(interfaz gráfica de usuario, o GUI,
usada ahora por la mayoría de la gente.
El nucleo de una CLI es un [*read-evaluate-print loop*](../../gloss.html#repl)(bucle leer-evaluar-imprimir), o REPL:
cuando el usuario escribe un comando y pulsa Enter (o return),
la computadora lo lee,
lo ejecuta
y muestra o imprime su salida.
El usuario entonces escribe otro comando
y así sucesivamente hasta que el usuario cierra su sesión.

Esta descripción hace que suene como si el usuario envía comandos directamente a la computadora,
y la computadora envía la salida directamente al usuario.
En realidad,
normalmente hay un programa en medio llamado
[*command shell*](../../gloss.html#shell).
Lo que el usuario escribe se ingresa en la shell;
que reconoce qué comandos hay que ejecutar y ordena al ordenador que lo haga.

La shell es un programa como cualquier otro.
Lo que lo hace especial es que su trabajo es ejecutar otros programas 
más que hacer cálculos por sí mismo.
La Unix shell más popular es Bash,
el *Bourne Again Shell*
(llamado así porque está derivado de una shell escrita por Stephen Bourne&mdash;esto
es lo que se conoce como humor entre programadores).
Bash es la shell por defecto en la mayoría de las implementaciones modernas de Unix
y en la mayoría de los paquetes que proporcionan herramientas de tipo Unix para Windows.

A veces, usar Bash o cualquier otro shell
se parece más a programación que emplear un ratón.
Los comandos son concisos (a veces de tan sólo un par de caracteres),
sus nombres son frecuentemente enigmáticos,
y sus respuestas son líneas de texto en vez de algo visual como una gráfica.
Por otro lado,
el shell nos permite combinar las herramientas existentes de maneras poderosas con solo un par de pulsaciones
y configurar procesos con grandes cantidades de información automáticamente.
Además,
la línea de comando es a menudo el modo más sencillo de interactuar con máquinas remotas.
Como los clústers y la computación en la nube se está convirtiendo más popular para la reducción de datos científicos,
ser capaz de manejarlos se está convirtiendo en una habilidad necesaria.

<div class="keypoints" markdown="1">

#### Puntos Clave
*   Una shell es un programa cuyo propósito primario es leer comandos y ejecutar otros programas.
*   Las principales ventajas de la shell son su elevada relación acción-por-pulsación,
    su apoyo para automatizar tareas repetitivas
    y que puede ser usado para acceder a otras máquinas en la red.
*   Las principales desventajas de la shell son su naturaleza primaria textual
    y cuan enigmáticas pueden ser sus comandos y operaciones.

</div>
