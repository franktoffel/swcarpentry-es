---
layout: lesson
root: ../..
title: Creando cosas
---
<div class="objectives" markdown="1">

#### Objectivos
*   Crear una jerarquía de directorios que coincida con un esquema determinado.
*   Crear archivos a partir de esa jerarquía con un editor o copiando y renombrando los archivos existentes.
*   Mostrar el contenido de un directorio empleando la línea de comandos.
*   Eliminar archivos especificados y/o directorios.

</div>

Sabemos ahora cómo explorar archivos y directorios,
pero ¿cómo los creamos en primer lugar?
Volvamos al *home* (directorio de inicio) de Vlad,
`/users/vlad`,
y usemos `ls -F` para ver qué contiene:

~~~
$ pwd
~~~
{:class="in"}
~~~
/users/vlad
~~~
{:class="out"}
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

Creemos un nuevo directorio llamado `thesis` empleando el comando `mkdir thesis`
(el cual no produce salida):

~~~
$ mkdir thesis
~~~
{:class="in"}

`mkdir` proviene del inglés *make directory* (crear directorio).
Como thesis es una ruta relativa,
es decir, no tiene barra al inicio,
el nuevo directorio se crea bajo el actual directorio de trabajo:

~~~
$ ls -F
~~~
{:class="in"}
~~~
bin/         data/     mail/      music/
notes.txt    papers/   pizza.cfg  solar/
solar.pdf    swc/      thesis/
~~~
{:class="out"}

Sin embargo, todavía no hay nada dentro de él:

~~~
$ ls -F thesis
~~~
{:class="in"}

Cambiemos nuestro directorio de trabajo a `thesis` empleando`cd`,
entonces ejecutemos un editor de texto llamado Nano para crear un archivo llamado `draft.txt`:

~~~
$ cd thesis
$ nano draft.txt
~~~
{:class="in"}

> #### ¿Qué editor?
> 
> Cuando decimos que "`nano` es un editor de texto", realmente significa "texto": sólo puede
> funcionar con los caracteres habituales, sin tablas, imágenes o cualquier otro objeto
> familiar. Lo empleamos en ejemplos porque casi cualquiera puede
> manejarlo en cualquier lugar sin entrenamiento, pero por favor, usa algo
> mas potente en tu lugar de trabajo. En los sistemas Unix (tales como Linux o Mac OS X)
> muchos programadores emplean [Emacs](http://www.gnu.org/software/emacs/)
> o [Vim](http://www.vim.org/) (los cuales son completamente no intuitivos
> incluso para los estándares de Unix), o un editor gráfico como
> [Gedit](http://projects.gnome.org/gedit/). En Windows, tal vez debas usar
> [Notepad++](http://notepad-plus-plus.org/).
> 
> No importa el editor que uses, necesitarás saber dónde busca
> y guarda archivos. Si lo abres desde la shell probablemente
> empleará tu directorio de trabajo actual como la localización por defecto. Si empleas
> el menú de inicio de tu ordenador, tal vez quiera guardar los archivos en tu escritorio o
> en el directorio de documentos. Puedes cambiar esto navegando
> en otros directorios y seleccionando el que prefieras la primera vez que realices
> "*Save as…*" (Guardar como...).

Escribamos en unas pequeñas líneas de texto y
entonces usamos Ctrl-O para escribir nuestra información en el disco:

<img src="img/nano-screenshot.png" alt="Nano en Acción" />

Una vez que nuestro archivo está guardado,
podemos usar Ctrl-X para salir del editor y volver a la shell.
(La documentación de Unix a menudo emplea la abreviación `^A` para "Ctrl-A".)
`nano` no muestra ninguna salida en la pantalla después de que salga,
pero `ls` muestra que hemos creado un archivo llamado `draft.txt`:

~~~
$ ls
~~~
{:class="in"}
~~~
draft.txt
~~~
{:class="out"}

Let's tidy up by running `rm draft.txt`:

~~~
$ rm draft.txt
~~~
{:class="in"}

Este comando elimina archivos ("`rm`" es la abreviación en ingles de *remove* - 'eliminar').
Si ejecutamos `ls` de nuevo,
su salida aparece vacía una vez más,
lo que nos indica que nuestro archivo se ha eliminado.

~~~
$ ls
~~~
{:class="in"}

> #### Eliminar es para Siempre
> 
> Unix no tiene una papelera de reciclaje: cuando eliminamos archivos, ellos son desenganchados
> del sistema de archivos para que su espacio de almacenamiento en disco se pueda 
> reciclar. Existen herramientas para encontrar y recuperar archivos eliminados, pero
> no se garantiza que funcionen en cualquier situación, ya que
> el ordenador puede haber reutilizado el espacio de disco de los archivos.

Volvemos a crear ese archivo
y subimos un directorio hacia `/users/vlad` empleando `cd ..`:

~~~
$ pwd
~~~
{:class="in"}
~~~
/users/vlad/thesis
~~~
{:class="out"}
~~~
$ nano draft.txt
$ ls
~~~
{:class="in"}
~~~
draft.txt
~~~
{:class="out"}
~~~
$ cd ..
~~~
{:class="in"}

Si intentamos eliminar el directorio `thesis` empleando `rm thesis`,
obtenemos el siguiente mensaje de error:

~~~
$ rm thesis
~~~
{:class="in"}
~~~
rm: cannot remove `thesis': Is a directory
~~~
{:class="err"}

Esto sucede porque `rm` solo funciona sobre archivos, no directorios.
El comando correcto es `rmdir`,
el cual es la abreviación del inglés *remove directory* (eliminar directorio).
Aunque esto tampoco funciona
porque el directorio que estamos intentando eliminar no está vacío:

~~~
$ rmdir thesis
~~~
{:class="in"}
~~~
rmdir: failed to remove `thesis': Directory not empty
~~~
{:class="err"}

Este pequeña característica de seguridad puede ahorrarte muchas penas,
particularmente si eres un mal mecanógrafo.
Para realmente deshacerse de `thesis` debemos eliminar primero el archivo `draft.txt`:

~~~
$ rm thesis/draft.txt
~~~
{:class="in"}

El directorio ahora está vacío, por tanto `rmdir` puede eliminarlo:

~~~
$ rmdir thesis
~~~
{:class="in"}

> #### Un Gran Poder Acarrea Una Gran Responsabilidadw
> 
> La eliminación de archivos en un directorio sólo para que podamos eliminar
> el directorio, rápidamente se convierte en una tarea aburrida.
> En su lugar, podemos emplear `rm` con la
> opción `-r` (que proviene de "recursivo"):
> 
> ~~~
> $ rm -r thesis
> ~~~
> 
> Esto elimina todo en el directorio, incluido el directorio en si. Si
> el directorio contiene sub-directorios, `rm -r` les hace la misma cosa
> a ellos y sucesivamente. Es muy útil, pero puede provocar muchos daños si
> no se emplea cuidadosamente.

Creamos ese directorio y archivo una vez más.
(Nota que esta vez estamos ejecutando `nano` con la ruta `thesis/draft.txt`,
en vez de ir dentro del directorio `thesis` y ejecutar `nano` sobre `draft.txt`.)

~~~
$ pwd
~~~
{:class="in"}
~~~
/users/vlad
~~~
{:class="out"}
~~~
$ mkdir thesis
~~~
{:class="in"}
~~~
$ nano thesis/draft.txt
$ ls thesis
~~~
{:class="in"}
~~~
draft.txt
~~~
{:class="out"}

`draft.txt` no es un nombre particularmente informativo,
así que cambiemos el nombre del archivo empleando `mv`,
que es la abreviación de *move* (mover):

~~~
$ mv thesis/draft.txt thesis/quotes.txt
~~~
{:class="in"}

El primer parámetro le dice a `mv` qué estamos "moviendo",
mientras que el segundo es dónde tiene que ir.
En este caso,
estamos moviendo `thesis/draft.txt` a `thesis/quotes.txt`,
lo que tiene el mismo efecto que renombrar el archivo.
Efectivamente,
`ls` nos muestra que `thesis` ahora contiene un archivo llamado `quotes.txt`:

~~~
$ ls thesis
~~~
{:class="in"}
~~~
quotes.txt
~~~
{:class="out"}

Sólo por mantener la inconsistencia,
`mv` también funciona en directorios&mdash;no hay un comando `mvdir` aparte.

Movamos `quotes.txt` al directorio de trabajo actual.
Empleamos `mv` una vez más,
pero esta vez usaremos únicamente el nombre de un directorio como el segundo parámetro
para decirle a `mv` que queremos mantener el nombre del archivo,
pero en un lugar nuevo.
(Es por ello por lo que el comando se llama "mover".)
En este caso,
el nombre de directorio que usamos es el nombre especial `.` que introducimos anteriormente.

~~~
$ mv thesis/quotes.txt .
~~~
{:class="in"}

Esto resulta en que se ha movido el archivo del directorio en el que estaba al directorio de trabajo actual.
`ls` muestra ahora que `thesis` está vacío:

~~~
$ ls thesis
~~~
{:class="in"}

Además,
`ls` con un fichero o directorio como parámetro solo muestra ese fichero o directorio.
Podemos usar esto para ver que `quotes.txt` se encuentra en nuestro directorio actual:

~~~
$ ls quotes.txt
~~~
{:class="in"}
~~~
quotes.txt
~~~
{:class="out"}

El comando `cp` funciona casi igual que `mv`,
excepto en que copia en vez de mover el archivo.
Podemos probar que hace lo que esperamos usando `ls`
con las dos rutas como parámetros&mdash; como la mayoría de los comandos en Unix,
se le puede indicar a `ls` miles de rutas a la vez:

~~~
$ cp quotes.txt thesis/quotations.txt
$ ls quotes.txt thesis/quotations.txt
~~~
{:class="in"}
~~~
quotes.txt   thesis/quotations.txt
~~~
{:class="out"}

Para confirmar que hemos hecho una copia,
borremos el fichero `quotes.txt` del directorio de trabajo actual
y ejecutemos el mismo `ls` otra vez.
Esta vez nos dice que no puede encontrar `quotes.txt` en el directorio actual,
pero si encuentra la copia  que no borramos en `thesis`:

~~~
$ ls quotes.txt thesis/quotations.txt
~~~
{:class="in"}
~~~
ls: cannot access quotes.txt: No such file or directory
thesis/quotations.txt
~~~
{:class="err"}

> #### Otra Abreviación Útil
> 
> La terminal interpreta el caracter `~` (vírgola) al principio de una ruta
> como "el directorio *home* del usuario actual". Por ejemplo, si el directorio
> *home* de Vlad es `/home/vlad`, entonces `~/data` es equivalente a
> `/home/vlad/data`.  Esto sólo funciona si la vírgola es el primer caracter en
> la ruta: `aqui/alli/~/cualquierlugar` *no* es `/home/vlad/cualquierlugar`.

<div class="keypoints" markdown="1">

#### Puntos Clave
*   La documentación de Unix usa '^A' refiriéndose a "Ctrl-A".
*   La shell no tiene una papelera de reciclaje: cuando algo se borra, se borra para siempre.
*   Nano es un editor de texto muy simple&mdash;por favor, usa otro distinto para el trabajo de verdad.

</div>

<div class="challenge" markdown="1">
En la siguiente sequiencia de comandos ¿qué mostrará el último `ls`?

~~~
$ pwd
/home/thing/data
$ ls
proteins.dat
$ mkdir recombine
$ mv proteins.dat recombine
$ cp recombine/proteins.dat ../proteins-saved.dat
$ ls
~~~
</div>

<div class="challenge" markdown="1">
Si:

~~~
$ ls -F
analyzed/  fructose.dat    raw/   sucrose.dat
~~~

¿Qué comando(s) deberás ejecutar para que los siguientes comandos muestren lo siguiente?

~~~
$ ls
analyzed   raw
$ ls analyzed
fructose.dat    sucrose.dat
~~~
</div>

<div class="challenge" markdown="1">
¿Qué hará `cp` cuando se ejecuta con mltiples nombres de ficheros y un nomre de directorio como
se muestra a continuación?

~~~
$ mkdir backup
$ cp thesis/citations.txt thesis/quotations.txt backup
~~~

¿Qué hará `cp` cuando se le da tres o más nombres de ficheros como en el siguiente ejemplo?

~~~
$ ls -F
intro.txt    methods.txt    survey.txt
$ cp intro.txt methods.txt survey.txt
~~~
</div>

<div class="challenge" markdown="1">
El comando `ls -R` muestra el contenido de directorios recursivamente,
esto es, muestra los subdirectorios, subsubdirectorios, etc
en orden alfabético en cada nivel.
El comando `ls -t` lista el contenido dependiendo la la última modificación,
mostrando los más recientes al comienzo.
¿En qué orden `ls -R -t` mostrará el contenido?
</div>
