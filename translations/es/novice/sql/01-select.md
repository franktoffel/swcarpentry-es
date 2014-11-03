---
layout: lesson
root: ../..
---

## Seleccionando Datos


<div>
<p>Durante finales de la década de 1920 e inicios de la década de 1930, William Dyer, Frank Pabodie, y Valentina Roerich lideraron expediciones hacia el <a href="http://es.wikipedia.org/wiki/Polo_de_inaccesibilidad">Polo de Inaccesibilidad</a> en el Pacífico Sur, y luego hacia la Antártica. Hace dos años, sus expediciones fueron halladas en un casillero en la Universidad de Miskatonic. Hemos escaneado la información que contienen, y le hicimos un reconocimiento óptico de caracteres (OCR), y ahora queremos almacenar dicha información de una manera que facilite su búsqueda y análisis.</p>
<p>Básicamente tenemos tres opciones: archivos de texto, una hoja de cálculo, o una *database* (base de datos). Los archivos de texto son los más fáciles de crear, y funcionan bien con sistemas de control de versiones, pero entonces nosotros mismos tendríamos que desarrollar herramientas de búsqueda y análisis. Las hojas de cálculo son útiles para realizar análisis simples, aunque no manejan muy bien conjuntos de datos que sean grandes y complejos. Por lo tanto, nos gustaría colocar toda esta información en una base de datos, y estas lecciones mostrarán cómo hacer eso.</p>
</div>


<div class="objectives">
<h4 id="objectives">Objetivos</h4>
<ul>
<li>Explicar la diferencia entre una tabla, un registro, y un campo.</li>
<li>Explicar la diferencia entre una base de datos y un gestor de bases de datos.</li>
<li>Escribir una *query* para seleccionar todos los valores correspondientes a campos específicos de una tabla.</li>
</ul>
</div>

### Algunas Definiciones


<div>
<p>Una <a href="../../gloss.html#relational-database">*relational database*</a> es una forma de almacenar y manipular información organizada en <a href="../../gloss.html#table-database">*tables*</a> (tablas). Cada tabla tiene columnas (también conocidas como <a href="../../gloss.html#field-database">*fields*</a>(campos)) las cuales describen los datos, y filas (también conocidas como <a href="../../gloss.html#record-database">*records*</a>) las cuales contienen los datos.</p>
<p>Cuando utilizamos una hoja de cálculo, introducimos fórmulas en las celdas para calcular nuevos valores en base a los valores ya conocidos. Cuando utilizamos una base de datos, enviamos comandos (usualmente llamados <a href="../../gloss.html#query">*queries*</a>(consultas)) a un <a href="../../gloss.html#database-manager">*database manager*</a> (gestor de bases de datos): un programa que manipula la base de datos por nosotros. El gestor de bases de datos realiza todas las búsquedas y cálculos especificados en la *query*, devolviendo los resultados organizados en una tabla que luego podremos utilizar como punto de partida para *queries* posteriores.</p>
<blockquote>
<p>Cada gestor de bases de datos—Oracle, IBM DB2, PostgreSQL, MySQL, Microsoft Access, and SQLite—almacena datos de modo diferente, asi que una base de datos creada con alguno de ellos no puede ser utlizada directamente por otro. Sin embargo, cada gestor de bases de datos puede importar y exportar datos en una variedad de formatos, por lo tanto <em>es</em> posible mover información de uno a otro.</p>
</blockquote>
<p>Las *queries* son escritas en un lenguaje llamado <a href="../../gloss.html#sql">SQL</a>, cuyas siglas en inglés representan  &quot;*Structured Query Language*&quot;. SQL proporciona cientos de diferentes formas de analizar y recombinar datos; sólo prestaremos atención a unos pocos, pero que son válidos para la mayor parte del trabajo que los científicos realizan.</p>
<p>Las siguientes tablas muestran la base de datos que utilizaremos en nuestros ejemplos:</p>
</div>


<div>
<table>
<tr>
<td valign="top">
<p><strong>Person</strong>: las personas que tomaron mediciones.</p>
<table>
  <tr> <th>
ident
</th> <th>
personal
</th> <th>
family
</th> </tr>
  <tr> <td>
dyer
</td> <td>
William
</td> <td>
Dyer
</td> </tr>
  <tr> <td>
pb
</td> <td>
Frank
</td> <td>
Pabodie
</td> </tr>
  <tr> <td>
lake
</td> <td>
Anderson
</td> <td>
Lake
</td> </tr>
  <tr> <td>
roe
</td> <td>
Valentina
</td> <td>
Roerich
</td> </tr>
  <tr> <td>
danforth
</td> <td>
Frank
</td> <td>
Danforth
</td> </tr>
</table>

<p><strong>Site</strong>: ubicaciones geográficas dónde se tomaron las mediciones.</p>
<table>
  <tr> <th>
name
</th> <th>
lat
</th> <th>
long
</th> </tr>
  <tr> <td>
DR-1
</td> <td>
-49.85
</td> <td>
-128.57
</td> </tr>
  <tr> <td>
DR-3
</td> <td>
-47.15
</td> <td>
-126.72
</td> </tr>
  <tr> <td>
MSK-4
</td> <td>
-48.87
</td> <td>
-123.4
</td> </tr>
</table>

<p><strong>Visited</strong>: las fechas en que se tomaron las mediciones.</p>
<table>
  <tr> <th>
ident
</th> <th>
site
</th> <th>
dated
</th> </tr>
  <tr> <td>
619
</td> <td>
DR-1
</td> <td>
1927-02-08
</td> </tr>
  <tr> <td>
622
</td> <td>
DR-1
</td> <td>
1927-02-10
</td> </tr>
  <tr> <td>
734
</td> <td>
DR-3
</td> <td>
1939-01-07
</td> </tr>
  <tr> <td>
735
</td> <td>
DR-3
</td> <td>
1930-01-12
</td> </tr>
  <tr> <td>
751
</td> <td>
DR-3
</td> <td>
1930-02-26
</td> </tr>
  <tr> <td>
752
</td> <td>
DR-3
</td> <td bgcolor="red">
 
</td> </tr>
  <tr> <td>
837
</td> <td>
MSK-4
</td> <td>
1932-01-14
</td> </tr>
  <tr> <td>
844
</td> <td>
DR-1
</td> <td>
1932-03-22
</td> </tr>
</table>
</td>
<td valign="top">
<p><strong>Survey</strong>: las mediciones tomadas.</p>
<table>
  <tr> <th>
taken
</th> <th>
person
</th> <th>
quant
</th> <th>
reading
</th> </tr>
  <tr> <td>
619
</td> <td>
dyer
</td> <td>
rad
</td> <td>
9.82
</td> </tr>
  <tr> <td>
619
</td> <td>
dyer
</td> <td>
sal
</td> <td>
0.13
</td> </tr>
  <tr> <td>
622
</td> <td>
dyer
</td> <td>
rad
</td> <td>
7.8
</td> </tr>
  <tr> <td>
622
</td> <td>
dyer
</td> <td>
sal
</td> <td>
0.09
</td> </tr>
  <tr> <td>
734
</td> <td>
pb
</td> <td>
rad
</td> <td>
8.41
</td> </tr>
  <tr> <td>
734
</td> <td>
lake
</td> <td>
sal
</td> <td>
0.05
</td> </tr>
  <tr> <td>
734
</td> <td>
pb
</td> <td>
temp
</td> <td>
-21.5
</td> </tr>
  <tr> <td>
735
</td> <td>
pb
</td> <td>
rad
</td> <td>
7.22
</td> </tr>
  <tr> <td>
735
</td> <td bgcolor="red">
 
</td> <td>
sal
</td> <td>
0.06
</td> </tr>
  <tr> <td>
735
</td> <td bgcolor="red">
 
</td> <td>
temp
</td> <td>
-26.0
</td> </tr>
  <tr> <td>
751
</td> <td>
pb
</td> <td>
rad
</td> <td>
4.35
</td> </tr>
  <tr> <td>
751
</td> <td>
pb
</td> <td>
temp
</td> <td>
-18.5
</td> </tr>
  <tr> <td>
751
</td> <td>
lake
</td> <td>
sal
</td> <td>
0.1
</td> </tr>
  <tr> <td>
752
</td> <td>
lake
</td> <td>
rad
</td> <td>
2.19
</td> </tr>
  <tr> <td>
752
</td> <td>
lake
</td> <td>
sal
</td> <td>
0.09
</td> </tr>
  <tr> <td>
752
</td> <td>
lake
</td> <td>
temp
</td> <td>
-16.0
</td> </tr>
  <tr> <td>
752
</td> <td>
roe
</td> <td>
sal
</td> <td>
41.6
</td> </tr>
  <tr> <td>
837
</td> <td>
lake
</td> <td>
rad
</td> <td>
1.46
</td> </tr>
  <tr> <td>
837
</td> <td>
lake
</td> <td>
sal
</td> <td>
0.21
</td> </tr>
  <tr> <td>
837
</td> <td>
roe
</td> <td>
sal
</td> <td>
22.5
</td> </tr>
  <tr> <td>
844
</td> <td>
roe
</td> <td>
rad
</td> <td>
11.25
</td> </tr>
</table>
</td>
</tr>
</table>

</div>


<div>
<p>Nótese que tres entradas—una en la tabla <code>Visited</code>, y dos en la tabla <code>Survey</code>—se muestran en rojo ya que no contienen ningún dato: volveremos a estos valores faltantes <a href="#s:null">luego</a>. Por ahora, escribamos una *query* SQL que muestre los nombres de los científicos. Para esto, utilizamos el comando SQL <code>select</code>, proporcionando los nombres de las columnas que deseamos y la tabla de la cual deseamos que provengan. Nuestra *query* y su resultado se ven así:</p>
</div>


<div class="in">
<pre>%load_ext sqlitemagic</pre>
</div>
`'sqlitemagic' es una extensión de iPython que permite ejecutar queries SQL y mostrar su resultado en tablas.`


<div class="in">
<pre>%%sqlite survey.db
select family, personal from Person;</pre>
</div>
`los nombres de las columnas "family" y "personal" son, respectivamente, abreviaturas de "family name" (apellido) y "personal name" (nombre propio).`

<div class="out">
<pre><table>
<tr><td>Dyer</td><td>William</td></tr>
<tr><td>Pabodie</td><td>Frank</td></tr>
<tr><td>Lake</td><td>Anderson</td></tr>
<tr><td>Roerich</td><td>Valentina</td></tr>
<tr><td>Danforth</td><td>Frank</td></tr>
</table></pre>
</div>


<div>
<p>El símbolo punto y coma al final de la *query* le indica al gestor de bases de datos que la consulta está completada y lista para ser ejecutada. Hemos escrito nuestros comandos y el nombre de columna en letra minúscula, y el nombre de la tabla con la primera letra en mayúscula, pero no estamos obligados a hacerlo: como se muestra en el siguiente ejemplo, SQL es <a href="../../gloss.html#case-insensitive">*case insensitive*</a> (insensible a mayúsculas y minúsculas).</p>
</div>


<div class="in">
<pre>%%sqlite survey.db
SeLeCt FaMiLy, PeRsOnAl FrOm PeRsOn;</pre>
</div>

<div class="out">
<pre><table>
<tr><td>Dyer</td><td>William</td></tr>
<tr><td>Pabodie</td><td>Frank</td></tr>
<tr><td>Lake</td><td>Anderson</td></tr>
<tr><td>Roerich</td><td>Valentina</td></tr>
<tr><td>Danforth</td><td>Frank</td></tr>
</table></pre>
</div>


<div>
<p>Cualquiera que sea la distribución de mayúsculas y minúsculas que utilices, por favor se consistente: las *queries* complejas son suficientemente difíciles de leer sin la carga cognitiva adicional causada por un uso aleatorio de las mayúsculas y minúsculas.</p>
</div>


<div>
<p>Volviendo a nuestra *query*, es importante entender que las filas y columnas en una base de datos, en realidad, no están almacenadas en ningún orden particular. Ellas siempre serán <em>displayed</em> en algún orden, pero podemos controlar eso de varias maneras. Por ejemplo, podríamos intercambiar las columnas en el resultado escribiendo nuestra *query* así:</p>
</div>


<div class="in">
<pre>%%sqlite survey.db
select personal, family from Person;</pre>
</div>

<div class="out">
<pre><table>
<tr><td>William</td><td>Dyer</td></tr>
<tr><td>Frank</td><td>Pabodie</td></tr>
<tr><td>Anderson</td><td>Lake</td></tr>
<tr><td>Valentina</td><td>Roerich</td></tr>
<tr><td>Frank</td><td>Danforth</td></tr>
</table></pre>
</div>


<div>
<p>o también repetir columnas:</p>
</div>


<div class="in">
<pre>%%sqlite survey.db
select ident, ident, ident from Person;</pre>
</div>
`select (seleccionar): Comando SQL utilizado para indicar los campos de la tabla cuyos datos deseamos extraer`
`from (de, desde): Palabra reservada SQL utilizada para hacer referencia a la tabla de la cual deseamos extraer`
`el nombre de la columna "ident" es la abreviatura de "identification" (identificación)`

<div class="out">
<pre><table>
<tr><td>dyer</td><td>dyer</td><td>dyer</td></tr>
<tr><td>pb</td><td>pb</td><td>pb</td></tr>
<tr><td>lake</td><td>lake</td><td>lake</td></tr>
<tr><td>roe</td><td>roe</td><td>roe</td></tr>
<tr><td>danforth</td><td>danforth</td><td>danforth</td></tr>
</table></pre>
</div>


<div>
<p>Y como atajo, podemos seleccionar todas las columnas en una tabla utilizando <code>*</code>:</p>
</div>


<div class="in">
<pre>%%sqlite survey.db
select * from Person;</pre>
</div>

<div class="out">
<pre><table>
<tr><td>dyer</td><td>William</td><td>Dyer</td></tr>
<tr><td>pb</td><td>Frank</td><td>Pabodie</td></tr>
<tr><td>lake</td><td>Anderson</td><td>Lake</td></tr>
<tr><td>roe</td><td>Valentina</td><td>Roerich</td></tr>
<tr><td>danforth</td><td>Frank</td><td>Danforth</td></tr>
</table></pre>
</div>


<div>
<h4 id="challenges">Desafíos</h4>
<ol style="list-style-type: decimal">
<li><p>Escribe una *query* que seleccione solamente los nombres de sitio de la tabla <code>Site</code>.</p></li>
<li><p>Muchas presonas escriben sus *queries* con el siguiente formato:</p>
<pre><code>SELECT personal, family FROM person;</code></pre>
<p>o así:</p>
<pre><code>select Personal, Family from PERSON;</code></pre>
<p>¿Cuál de estos estilos te parece más fácil de leer, y por qué?</p></li>
</ol>
</div>


<div class="keypoints">
<h4 id="key-points">Aspectos Clave</h4>
<ul>
<li>Una base de datos relacional almacena información en tablas, cada una de las cuales tiene un número fijo de columnas y un número variable de registros.</li>
<li>Un gestor de bases de datos es un programa que manipula información almacenada en una base de datos.</li>
<li>Escribimos *queries* en un lenguaje especializado llamado SQL para extraer información de bases de datos.</li>
<li>SQL es insensible a mayúsculas y minúsculas.</li>
</ul>
</div>
