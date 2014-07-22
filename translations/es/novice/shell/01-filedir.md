---
layout: lesson
root: ../..
title: Archivos y Directorios
---
<div class="objectives" markdown="1">

#### Objectivos
*   Explicar las similitudes y diferencias entre un archivo y un directorio.
*   Convertir una ruta absoluta en una ruta relativa y viceversa.
*   Construir rutas absolutas y relativas que identifiquen archivos y directorio específicos.
*   Explicar los pasos del ciclo leer-ejecutar-imprimir de la shell.
*   Identificar los comandos, señales y nombres de archivos en la línea de comandos.
*   Demostrar el uso de completado por tabulador y explicar su ventajas.

</div>

La parte del sistema operativo responsable de manejar archivos y directorios
se llama [*file system*](../../gloss.html#filesystem) (sistema de archivos).
Su función es organizar nuestra información en archivos,
que contienen la información,
y directorios (también llamados “carpetas”)
que contienen a su vez archivos u otros directorios.

Varios comandos se emplean a menudo para crear, inspeccionar, renombrar y eliminar archivos y directorios.
Para comenzar a explorarlos,
abramos una ventana de shell:

~~~
$
~~~
{:class="in"}

El signo del dólar es un [*prompt*](../../gloss.html#prompt) (indicador),
que nos muestra que la shell está esperando que introduzcas la entrada;
tu Shell tal vez muestre algo más elaborado.

Escribe el comando `whoami`,
y presiona la tecla Enter (algunas veces aparece como Return) para enviar el comando a la shell.
La salida del comando es la ID del actual usuario,
es decir,
nos muestra quién cree la Shell que somos:

~~~
$ whoami
~~~
{:class="in"}
~~~
vlad
~~~
{:class="out"}

Más específicamente, cuando escribimos`whoami` la shell:

1.  encuentra un programa llamado `whoami`,
2.  ejecuta ese programa,
3.  muestra la salida de ese programa, y entonces
4.  muestra un nuevo *prompt* para decirnos que está listo para más comandos.

A continuación,
descubramos dónde estamos mediante la ejecución del comando  `pwd`
(que viene del inglés *"print working directory"* - imprimir directorio de trabajo).
En cualquier  momento,
nuestro [*current working directory*](../../gloss.html#current-working-directory) (directorio de trabajo actual) es nuestro directorio actual por defecto,
es decir,
el directorio que el ordenador asume que queremos para ejecutar comandos
a menos que explícitamente especifiquemos lo contrario.
Aquí,
la respuesta del ordenador es `/users/vlad`,
que es el directorio [*home*](../../gloss.html#home-directory) (de inicio) de Vlad:

~~~
$ pwd
~~~
{:class="in"}
~~~
/users/vlad
~~~
{:class="out"}

> #### Sopa de letras
>
> Si el comando para descubrir quién somos es `whoami`, el comando para encontrar
> dónde estamos debería llamarse `whereami`, por tanto, ¿por qué se usa `pwd`?
> La respuesta más común es que a principios de los setenta, cuando se 
> estaba comenzando a desarrollarse Unix, cada pulsación contaba: los aparataos de la época
> eran lentos y retroceder un espacio en un teletipo era muy costoso con lo que disminuir
> el número de pulsaciones para disminuir el número de posibles errores escribiendo era
> realmente una victoria. La realidad es que los comandos se fueron añadiendo a
> Unix uno a uno, sin ningún plan maestro, por gente que estaba inmersa en
> su propia jerga. El resultado es tan inconsistente como las reglas ortográficas del inglés
> con las que estamos atascados hoy en día.

Para comprender lo que es un directorio *"home"*,
echemos un vistazo a cómo se organiza un sistema de archivos.
En un principio, está el directorio [*root*](../../gloss.html#root-directory) (raíz)
que contiene todo lo demás.
Nos referimos a él empleando la barra inclinada `/`;
esta es la barra inicial de `/users/vlad`.

Dentro de ese directorio hay otros directorios:
`bin` (que es donde algunos programas compilados se almacenan),
`data` (para archivos de información diversa),
`users` (donde se localizan los directorios personales del usuario)
`tmp` (para archivos temporales que no necesitan ser almacenados durante mucho tiempo)
y otros:

<img src="img/filesystem.svg" alt="El sistema de ficheros" />

Sabemos que nuestro directorio de trabajo actual `/users/vlad` está dentro de `/users`
porque `/users` es la primera parte de su nombre.
Igualmente,
sabemos que `/users` está almacenado dentro del directorio *root*
porque su nombre comienza con `/`.

Debajo de `/users`,
encontramos un directorio para cada usuario con una cuenta en dicha máquina.
Los archivos de Mummy están almacenados en `/users/imhotep`,
los de Wolfman en `/users/larry`
y los nuestros en `/users/vlad`,
lo cual explica por qué vlad es la última parte del nombre del directorio.

<img src="img/home-directories.svg" alt="Directorios home" />

> Date cuenta que hay dos significados para el carácter `/`.
> Cuando aparece delante de un archivo o nombre de directorio,
> se refiere al directorio *root*. Cuando aparece dentro de un nombre
> es solo un separador.

Veamos que hay en el directorio *home* de Vlad mediante la ejecución de `ls`,
que proviene del inglés *listing* (listado).

~~~
$ ls
~~~
{:class="in"}
~~~
bin          data      mail       music
notes.txt    papers    pizza.cfg  solar
solar.pdf    swc
~~~
{:class="out"}

<img src="img/vlad-homedir.svg" alt="Directorio Home de Vlad" />

`ls` muestra los nombres de los archivos y directorios en la actual dirección en orden alfabético,
dispuestos ordenadamente en columnas.
Podemos hacer su salida más comprensible mediante el empleo de la [*flag*](../../gloss.html#command-line-flag) (o indicador) `-F`,
que le dice a ls que añada una `/` al final de cada uno de los nombres de los directorios:

~~~
$ ls -F
~~~
{:class="in"}
~~~
bin/         data/     mail/      music/
notes.txt    papers/   pizza.cfg  solar/
solar.pdf    swc/
~~~
{:class="out"}

Aquí,
podemos ver que `/users/vlad` contiene siete [subdirectorios](../../gloss.html#sub-directory).
Los nombres que no tienen barras al final
como `notes.txt`, `pizza.cfg` y `solar.pdf`,
son simplemente archivos y no directorios.
Además, date cuenta que hay un espacio entre `ls` y `-F`:
sin él, la shell cree que estamos intentado ejecutar un programa llamado `ls-F`,
el cual no existe.

> #### ¿Qué aparece en un nombre?
> 
> Tal vez te hayas dado cuenta que todos los nombres de los archivos de Vlad son 
> “algo punto algo”. Esto es sólo una convención: podemos llamar a un archivo  `mythesis` o
> casi cualquier otra cosa que queramos. Sin embargo, la mayoría de la gente emplea nombres de dos partes
> casi siempre como ayuda para ellos mismos (y sus programas) para indicar diferentes tipos 
> de archivos. La segunda parte de dicho nombre se llama
> [extensión](../../gloss.html#filename-extension), e indica 
> qué tipo de datos contiene el archivo: `.txt` se refiere a un archivo de texto plano; `.pdf`
> indica un documento PDF, `.cfg` es un fichero de configuración lleno de parámetros
> para algún programa y así el resto de extensiones.
>
> Esto es solo una convención, aunque importante. Los archivos contienen 
> bytes: nos toca a nosotros y a nuestros programas interpretarlos
> de acuerdo a las reglas para documentos PDF, imágenes o lo que sea. 
>
> Nombrar una imagen PNG de una ballena como `ballena.mp3` no convierte 
> mágicamente la imagen a una grabación del sonido de una ballena, aunque *tal vez*
> provoque que el sistema operativo intente abrirlo con un reproductor de música
> cuando alguien hace doble click sobre el archivo.

Ahora, echemos un vistazo a lo que hay en el directorio `data` de Vlad ejecutando `ls -F data`,
es decir,
el comando `ls` con los [argumento](../../gloss.html#argument) `-F` y `data`.
El segundo argumento&mdash;el único *sin* guión delante&mdash;le dice a `ls` que
queremos un listado de alguna otra cosa diferente a nuestro directorio de trabajo actual:

~~~
$ ls -F data
~~~
{:class="in"}
~~~
amino-acids.txt   elements/     morse.txt
pdb/              planets.txt   sunspot.txt
~~~
{:class="out"}

La salida nos muestra que hay cuatro archivos de texto y dos sub-sub-directorios.
Organizar las cosas jerárquicamente de esta manera nos ayuda a mantener claro nuestro trabajo:
es posible poner cientos de archivos en nuestro *home*,
así como es posible apilar cientos de papeles impresos en nuestro escritorio,
pero es una estrategia contraprodcente.

Nótese, por la forma que deletreamos el directorio `data`.
No tiene barra al final:
se agrega a los nombres del directorio `ls` cuando usamos el indicador `-F` para ayudarnos a que nos diga cosas aparte.
Y no comienza con una barra porque es una [ruta relativa](../../gloss.html#relative-path),
es decir, le dice a `ls` cómo encontrar algo desde donde estamos,
en vez de la raíz del sistema de archivos.

> #### Parámetros vs. Argumentos
>
> De acuerdo con [Wikipedia](https://en.wikipedia.org/wiki/Parameter_(computer_programming)#Parameters_and_arguments),
> el término [argumento](../../gloss.html#argument) y [parámetro](../../gloss.html#parameter)
> significan cosas un poco diferente.
> En práctica,
> sin embargo,
> la mayoría lo usan indistintamente o de manera inconsistente,
> y así haremos aquí también.

Si ejecutamos `ls -F /data` (*con* una barra inicial) obtenemos una respuesta diferente,
porque `/data` es una [ruta absoluta](../../gloss.html#absolute-path):

~~~
$ ls -F /data
~~~
{:class="in"}
~~~
access.log    backup/    hardware.cfg
network.cfg
~~~
{:class="out"}

La barra inicial `/` le dice al ordenador que siga la ruta desde el *root* del sistema de archivos,
para que siempre se refiera a exactamente un directorio,
sin importar dónde estamos cuando ejecutamos el comando.

¿Y si queremos cambiar nuestro directorio de trabajo actual?
Antes de que hagamos esto,
`pwd` nos muestra que estamos en `/users/vlad`
y `ls` sin ningún argumento nos muestra el contenido del directorio:

~~~
$ pwd
~~~
{:class="in"}
~~~
/users/vlad
~~~
{:class="out"}
~~~
$ ls
~~~
{:class="in"}
~~~
bin/         data/     mail/      music/
notes.txt    papers/   pizza.cfg  solar/
solar.pdf    swc/
~~~
{:class="out"}

Podemos usar `cd` seguido por un nombre de directorio para cambiar nuestro directorio de trabajo.
`cd` significa *change directory* (cambio de directorio)
lo cual es un poco engañoso:
el comando no cambia el directorio,
cambia la idea de la shell de en qué directorio estamos.

~~~
$ cd data
~~~
{:class="in"}

`cd` no imprime nada,
pero si ejecutamos `pwd` tras ello, podemos ver que ahora estamos en `/users/vlad/data`.
Si ahora ejecutamos `ls` sin argumentos,
se muestran los contenidos de `/users/vlad/data`,
porque es donde estamos ahora:

~~~
$ pwd
~~~
{:class="in"}
~~~
/users/vlad/data
~~~
{:class="out"}
~~~
$ ls
~~~
{:class="in"}
~~~
amino-acids.txt   elements/     morse.txt
pdb/              planets.txt   sunspot.txt
~~~
{:class="out"}

Ahora sabemos cómo bajar en un árbol de directorios:
¿cómo vamos hacia arriba?
Podríamos usar una ruta absoluta:

~~~
$ cd /users/vlad
~~~
{:class="in"}

pero es casi siempre más simple emplear: `cd ..` para ascender un nivel:

~~~
$ pwd
~~~
{:class="in"}
~~~
/users/vlad/data
~~~
{:class="out"}
~~~
$ cd ..
~~~
{:class="in"}

`..` es un nombre de directorio especial que significa 
"el directorio que contiene en el que estamos",
o más sucintamente,
el [padre](../../gloss.html#parent-directory) del directorio actual.
Seguramente,
si ejecutamos `pwd` después de ejecutar `cd ..` estamos de vuelta en `/users/vlad`:

~~~
$ pwd
~~~
{:class="in"}
~~~
/users/vlad
~~~
{:class="out"}

El directorio especial `..` habitualmente no aparece cuando ejecutamos `ls`.
Si queremos que aparezca, podemos darle a `ls` el indicador `-a`:

~~~
$ ls -F -a
~~~
{:class="in"}
~~~
./           ../       bin/       data/
mail/        music/    notes.txt  papers/
pizza.cfg    solar/    solar.pdf    swc/
~~~
{:class="out"}

`-a` indica *show all* (que se muestre todo);
fuerza a `ls` para que nos muestre los nombres de los archivos y directorios que comienzan con `.`,
incluyendo `..` (lo que, si estamos en `/users/vlad`, se refiere al directorio `/users`).
Como puedes ver,
también muestra otro directorio especial que se llama simplemente `.`,
lo que significa "el directorio actual de trabajo".
Tal vez parezca redundante tener un nombre para ello,
pero veremos algunos usos para ello pronto.

> #### Ortogonalidad
> 
> Los nombres especiales `.` y `..` no pertenecen a `ls`;
> son interpretados igualmente por todo los programas.
> Por ejemplo,
> si estamos en `/users/vlad/data`,
> el comando `ls ..` nos dará un listado de `/users/vlad`.
> Cuando el significado de las partes sea el mismo no importa cómo estén combinados,
> los programadores dicen que son [ortogonales](../../gloss.html#orthogonal):
> los sistemas ortogonales tienden a ser más fáciles de aprender para la gente
> porque hay muy pocos casos especiales y excepciones que no se ajusten a ello.

### El proyecto de Nelle: Organizando archivos

Sabiendo tanto como hasta ahora sobre archivos y directorios,
Nelle está lista para organizar los archivos que la máquina de ensayos de proteínas creará.
Primero,
ella crea un directorio llamado `north-pacific-gyre`
(para recordarse de dónde vino la información).
Dentro de ese directorio,
crea una carpeta llamada `2012-07-03`,
que es la fecha de cuando empezó a procesar las muestras.
Ella solia usar nombres como `conference-paper` y `revised-results`,
pero encontró difícil de entenderlos después de un par de años.
(el lío final fue cuando se encontró a sí misma creando
una carpeta llamada `revised-revised-results-3`.)

> Nelle nombra sus carpetas "año-mes-día",
> con ceros delante de los meses y días que corresponda,
> porque el Shell expone los nombres de archivos y carpetas en orden alfabético
> Si emplease nombres de meses,
> diciembre iría antes que julio;
> si ella no usara ceros,
> noviembre ('11') iría antes que julio ('7').

Cada una de sus muestras está etiquetada de acuerdo a la convención de su laboratorio
con una identificación única de 10 caracteres
tal como: "NENE01729A".
Esto es lo que empleaba en su cuaderno de registros
para añadir la localización, la hora, la profundidad y otras características de la muestra,
así que decide emplearlo como parte de cada uno de los nombres de los archivos.
Como la salida de la máquina de ensayos es en texto plano,
llamará a sus archivos `NENE01729A.txt`, `NENE01812A.txt`, etc.
Los 1520 ficheros irán al mismo directorio.

Si ella está en su directorio *home*,
puede ver qué archivos tiene empleando el comando:

~~~
$ ls north-pacific-gyre/2012-07-03/
~~~
{:class="in"}

Esto es mucho para escribir,
pero ella puede hacer que la shell haga la mayor parte del trabajo.
Si escribe:

~~~
$ ls no
~~~
{:class="in"}

y entonces presiona tabulador,
la shell automáticamente completa el nombre del directorio por ella:

~~~
$ ls north-pacific-gyre/
~~~
{:class="in"}

Si ella presiona el tabulador de nuevo,
Bash añadirá `2012-07-03/` al comando,
ya que es la única posible combinación.
Presionar el tabulador de nuevo no hace nada,
ya que hay 1520 posiblidades;
presionar el tabulador dos veces hace aparecer una lista de todos los archivos,
etc.
Esto se llama [*tab completion*](../../gloss.html#tab-completion) (completado por tabulador),
y lo veremos en otras muchas herramientas mientras continuamos.

<div class="keypoints" markdown="1">

#### Puntos Clave
*   El sistema de archivos es responsable de manejar información del disco.
*   La información se almacena en archivos, los cuales están almacenados en directorios (carpetas)
*   Los directorios pueden también almacenar otros directorios, lo cual forma un árbol de directorios.
*   `/` por si sola es el directorio *root* (raíz) de todo el sistema de archivos.
*   Una ruta relativa especifica una localización a partir de la localización actual.
*   Una ruta absoluta especifica una localización a partir de la raíz del sistema de archivos.
*   Los nombres de directorios en una ruta están separados con `/` en Unix, pero `\\` en Windows.
*   `..` significa "el directorio por encima del actual";
    `.` por sí solo significa "el directorio actual".
*   La mayoría de los nombres de los archivos son `algo.extension`.
    La extensión no es requerida,
    y no garantiza nada,
    pero normalmente se emplea para indicar el tipo de información en el archivo.
*   La mayoría de los comandos toman opciones (indicadores) que comienzan con `-`.

</div>

<img src="img/filesystem-challenge.svg" alt="Sistema de ficheros para el desafío" />

<div class="challenge" markdown="1">
Si `pwd` muestra /`/users/thing`, ¿qué mostrará `ls ../backup`?

1.  `../backup: No such file or directory`
2.  `2012-12-01 2013-01-08 2013-01-27`
3.  `2012-12-01/ 2013-01-08/ 2013-01-27/`
4.  `original pnas_final pnas_sub`
</div>

<div class="challenge" markdown="1">
Si `pwd` muestra `/users/backup`
y `-r` le dice a `ls` que muestre cosas en orden inverso,
que comando mostrará: 

~~~
pnas-sub/ pnas-final/ original/
~~~

1.  `ls pwd`
2.  `ls -r -F`
3.  `ls -r -F /users/backup`
4.  Cualquiera entre \#2 o \#3, pero no \#1.
</div>

<div class="challenge" markdown="1">
¿Qué hace el comando `cd` sin un nombre de directorio?

1.  No tiene efecto
2.  Cambia el directorio de trabajo a `/`.
3.  Cambia el directorio de trabajo al directorio *home* del usuario.
4.  Produce un mensaje de error.
</div>

<div class="challenge" markdown="1">
¿Qué hace el comando `ls` cuando se usa con los argumentos `-s` and `-h`?
</div>
