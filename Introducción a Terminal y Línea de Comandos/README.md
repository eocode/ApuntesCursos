# Introducción a Terminal y Línea de Comandos<!-- omit in toc -->

## Tabla de Contenido<!-- omit in toc -->
- [Administración de procesos en backgroun y foreground](#administraci%c3%b3n-de-procesos-en-backgroun-y-foreground)
  - [Lista de comandos](#lista-de-comandos)
    - [Listar](#listar)
    - [Ver directorio actual](#ver-directorio-actual)
    - [Cambiar de directorio](#cambiar-de-directorio)
    - [Crear una carpeta](#crear-una-carpeta)
    - [Crear archivos](#crear-archivos)
    - [Mover un archivo](#mover-un-archivo)
    - [Cambiar de nombre a un archivo](#cambiar-de-nombre-a-un-archivo)
    - [Eliminar archivos](#eliminar-archivos)
    - [Ayuda](#ayuda)
    - [Copiar](#copiar)
    - [Navegar entre 2 directorios](#navegar-entre-2-directorios)
    - [Abrir un archivo](#abrir-un-archivo)
    - [Ver las primeras líneas de un archivo](#ver-las-primeras-l%c3%adneas-de-un-archivo)
    - [Imprimir todo el contenido de un archivo](#imprimir-todo-el-contenido-de-un-archivo)
    - [Ver las últimas líneas de un archivo](#ver-las-%c3%baltimas-l%c3%adneas-de-un-archivo)
    - [Ver ruta ejecutable de un comando](#ver-ruta-ejecutable-de-un-comando)
    - [Alias para comandos](#alias-para-comandos)
    - [Ver los procesos que están corriendo](#ver-los-procesos-que-est%c3%a1n-corriendo)
    - [Matar procesos](#matar-procesos)
    - [Ejecutar en 2do plano (background)](#ejecutar-en-2do-plano-background)
    - [Ejecutar varios procesos](#ejecutar-varios-procesos)
    - [Mostrar cantidad de procesos](#mostrar-cantidad-de-procesos)
    - [Tiempo de prendida de la computadora](#tiempo-de-prendida-de-la-computadora)
    - [Uso del disco](#uso-del-disco)
    - [Links](#links)
    - [Nombre de usuario](#nombre-de-usuario)
- [Streams](#streams)
- [Power Tools](#power-tools)
  - [Buscar cadenas de caracteres](#buscar-cadenas-de-caracteres)
  - [Buscar archivos](#buscar-archivos)
  - [Fecha actual](#fecha-actual)
  - [Tiempo del procesador](#tiempo-del-procesador)
    - [Tiempo de ejecución de un proceso](#tiempo-de-ejecuci%c3%b3n-de-un-proceso)
    - [Emular un navegador](#emular-un-navegador)
    - [Comprimir archivos](#comprimir-archivos)
  - [Pipe](#pipe)
  - [Crontab](#crontab)
- [Control de accesos y usuarios](#control-de-accesos-y-usuarios)
  - [Permisos](#permisos)
    - [Ejecutar como super user](#ejecutar-como-super-user)
- [Convertir archivos a ejecutable](#convertir-archivos-a-ejecutable)
- [Compresión de archivos](#compresi%c3%b3n-de-archivos)
- [Búsqueda de archivos](#b%c3%basqueda-de-archivos)
- [Interacción por HTTP](#interacci%c3%b3n-por-http)
- [Acceso seguro a otras computadoras](#acceso-seguro-a-otras-computadoras)
  - [Manejo de paquetes](#manejo-de-paquetes)
- [Automatización de tareas](#automatizaci%c3%b3n-de-tareas)
  - [Programar tareas](#programar-tareas)
- [Power Shell](#power-shell)

## Introducción

La línea de comandos te permite hacer de todo: configuraciones, editar texto, compilar código y utilizar las herramientas que existen dentro de tu sistema operativo.

Todos los comandos se pueden buscar con el comando `man`.

**Shorcuts**
* `Control + L` Limpiar la pantalla
* `Control + R` Buscar comandos usados anteriormente

**Ventajas**

* `Ahorras memoria` puesto que no hay una interfaz gráfica
* `Ahorras tiempo` pues hace más sentillo el trabajo.

**¿Qué es bash?**
GNU Bash o simplemente Bash es un lenguaje de comandos y shell de Unix escrito por Brian Fox para el Proyecto GNU como un reemplazo de software libre para el shell Bourne.​ ​

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Comandos

Los comandos, en su mayor parte, no son realmente más que pequeños programas incorporados en el sistema operativo.

Los `flags` (o banderas) sirven para decirle al comando cómo queremos que realice la acción en particular.

**Puntos a tener en cuenta**

* Los comandos se pueden poner todos con un solo `-`. Por ejemplo, estos dos comandos hacen lo mismo:
    ```bash
    $ ls -l -h 
    $ ls -lh 
    ```
* El punto `.` es el directorio actual.
* El doble punto `..` es el directorio padre.
* El sombrerito de eñe `~` sirve para ir a mi carpeta personal (home).

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

### Variables de entorno

Para el comando
`echo hola`

Si ejecutamos

`whereis echo`

Nos da como resultado su dirección donde está ubicado

`echo: /bin/echo /usr/share/man/man1/echo.1.gz`

Pero para poder usarlo en cualquier parte y no tener que escribir toda la ruta, todo se guarda en el PATH

`echo $PATH`

Para ver algunos de los comandos mapeados

`ls /usr/bin/ -l | more`

Para asignar usamos

`export myvar = valor`

`echo $myvar`

## Sistema de archivos

## Organización de información
* Archivos
* Directorios

Existen jerarquias entre cada uno de los directorios

### Comandos para trabajar desde nuestra ubicación

Lista los archivos que se encuentran en el directorio sobre el que estamos trabajando:

```shell
ls
```

Lista todos los archivos incluyendo aquellos que se han definido como ocultos:

```shell
ls -a
```

Todos los directorios contienen los archivos . y .., estos son punteros a directorios.

>.. --> directorio padre
>. --> directorio actual

Otros parámetros que puedes usar con el comando ls:

Ordena los archivos por fecha de modificación:

```shell
ls -t
```

Ordena los archivos por extensión:

```shell
ls -x
```

Muestra toda la información: usuario, grupo, permisos, tamaño, fecha y hora de creación.

```shell
ls -l
```

Muestra la misma información que ls -l pero con las unidades de tamaño en KB, MB:

```shell
ls -lh
```

Muestra el contenido de todos los subdirectorios de forma recursiva:

```shell
ls -R
```

Ordena los resultados por tamaño de archivo:
 
```shell
ls -S
```

### Comandos para cambiar de ubicación

Print Working Directory: se usa para mostrar el directorio actual en el que nos encontramos trabajando.

```shell
pwd
```

cd: se utiliza para cambiar de directorio. Luego del comando se debe especificar la ruta del directorio al que nos queremos mover. Por ejemplo:

```shell
cd /home/mi_usuario
```

### Comandos para mover, copiar o borrar

cp: copiar un archivo hacia un directorio.

```shell
cp [archivo que se va a copiar] [directorio hacia el que se va a mover]
```

rm: eliminar un archivo.

```shell
rm archivo.txt
```

`mv``: mover un archivo, cambiar su ubicación. La sintaxis es así:

```shell
mv [ruta del archivo] [directorio hacia el que se va a mover]
```

rmdir: eliminar un directorio. En este caso es importante resaltar que, para que el directorio pueda ser eliminado, no puede contener archivos u otros directorios en su interior.

```shell
rmdir [ruta / nombre del directorio a eliminar]
```

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Archivos de texto y utilidades interactivas

Un archivo de texto se compone por caracteres y es legible por humanos. Para poder leerlos tenemos dos opciones principales

* **VIM**
  * `vim archivo.txt`
  * Difícil empezar a trabajar con y maestro. La edición de comandos y modos de confundir a los principiantes.
  * Sesión de recuperación
  * Pantalla dividida
  * Ficha de expansión
  * Finalización de comandos
  * El coloreado de la sintaxis
* **Nano**
  * `nano archivo.txt`
  * Fácil de usar y dominar.
  * Nano tiene la mayoría de las combinaciones de teclas que aparecen en la parte inferior de la ventana, por lo que es extremadamente simple de usar.
  * Función de búsqueda
  * Buscar y reemplazar
  * "Ir a la línea de comandos"
  * Sangría automática

### Primeros pasos en VIM

Dentro de nano el interprete de comandos se activa con ESC y permite las siguientes acciones:

* `:i` permite activar el modo de insersión
* `:w` guarda el contenido
* `:q` sale del editor
* `:wq` guarda y sale
* `:q!` sale sin guardar 

## Utilidades batch y batch avanzadas

Son programas que procesan texto y emiten el resultado

### Trabajo fundamental con archivos de texto

touch: nos permite crear archivos.

```bash
touch archivo.txt
```

cat: nos permite visualizar todo el contenido de nuestros archivos.

```bash
cat archivo.txt
```

head: es muy parecido al comando cat. También nos permite visualizar el contenido de nuestros archivos, pero debemos indicarle cuántas líneas nos debe mostrar. Por defecto nos mostrará las primeras 10.

Primeras 10 líneas
```bash
head archivo.txt
```

Primeras 20 líneas

```bash
head -n 20 archivo.txt
```

tail: funciona igual que el comando head, pero al revés. También debemos indicarle cuántas líneas nos debe mostrar, la diferencia es que no las mostrará de abajo hacia arriba. Por defecto nos mostrará las últimas 10.

```bash
tail archivo.txt
```

Últimas 5 líneas
```bash
tail -n 5 archivo.txt
```

### Búsqueda y tratamiento de texto

El comando grep permite filtrar las líneas que queremos visualizar utilizando (o no) expresiones regulares:

```shell
grep “palabra-clave” archivo_gigante.txt
```

Si nos da igual si la palabra clave incluye mayúsculas o minúsculas podemos utilizar el flag -i:

```shell
grep -i “pAlaBra-cLAvE” archivo_gigante.txt
```

También podemos verificar si la línea incluye esta palabra clave al final:

```bash
grep “palabra-clave$” archivo_gigante.txt
```

O si la incluye al principio:

```bash
grep “^palabra-clave” archivo_gigante.txt
```

También hay situaciones donde necesitamos modificar un poco la información que obtenemos de un archivo de texto.

Por ejemplo, imagina que nuestro archivo contiene un poema, frase o saludo para responderle a los usuarios de nuestra aplicación. El problema es que cada usuario tiene un nombre diferente.

> ¡Hola, NOMBRE_USUARIO! Felicitaciones por completar tu desafío con PUNTOS_USUARIO puntos.

No queremos editar este archivo. Solo necesitamos cambiar los caracteres NOMBRE_USUARIO por el verdadero nombre del usuario.

Para esto podemos utilizar el comando ``sed``. 

Solo debemos indicarle que queremos realizar una sustitución (s/), la palabra que vamos a cambiar (NOMBRE_USUARIO), la nueva palabra que vamos a incluir (Ana) y cerrar con el símbolo /.

```shell
sed ‘s/NOMBRE_USUARIO/Ana’ archivo-saludo.txt
```

Ahora imagina que, además del nombre, debemos cambiar también la puntuación que obtuvo el usuario:

```shell
sed ‘s/NOMBRE_USUARIO/Ana/; s/PUNTOS_USUARIO/35/’ archivo-saludo.txt
```

Más usos de Sed: https://likegeeks.com/es/sed-de-linux/

Para tratar texto delimitado existe el comando `awk`

```shell
Awk -F ['delimitador;'] '{print$1}'# Sirve para tabajar con archivos estructurados ejemplo .csv, este ejemplo trae la primera columna
```

## Procesamiento de datos

Sigue el flujo estándar

* Entrada
* Procesamiento
* Salida
* Error

Los datos pueden venir de un teclado o de un archivo que ya tenemos

Los datos pueden enviarse en lugar de a una pantalla a un archivo

Encadenamiento de procesos

* Un ``pipe`` o ``tuberia``

Podemos concatenar dos o más comandos entre sí

```bash
cat archivo.txt | wc -l
```

Para el siguiente archivo `index.html`

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    
</body>
</html>
```

Ejecutaremos lo siguiente:

```bash
cat index.html | wc -l
head -n 15 index.html > index2.html | tail -n 15 index.html > index3.html | date >> index.html
```

# Administración de procesos en backgroun y foreground

Todos los comandos son procesos

* ``&`` => al final de un comando nos permite seguir trabajando mientras un proceso se ejecuta.
* ``ctrl + z`` => Me permite poner un proceso en background y poder seguir utilizando la linea de comandos.
* ``fg`` => Me permite poder volver a ese proceso.
Herramientas:
* ``ps`` => Me permite ver los procesos que se estan ejecutando.
* ``top`` => Me permite ver en tiempo real como los procesos van cambiando.

Como detener procesos:
* ``ctrl + c`` = nos permite terminar un programa en ejecucion en la consola.
* ``ps`` ax => nos permite ver los procesos y con el numero de id del procesos lo podemos eliminar.

Para eliminarlos por el id del proceso:
* ``kill`` => elimina el proceso por el id. kill -9 elimina el procesos inmediatamente.
* ``killall`` => elmina el proceso por el nombre del ejecutable.

## Lista de comandos

### Listar

`ls` lista las capetas y archivos que hay
* `-l` lista las capetas y archivos con su información básica
* `-h` ver de forma que sea facil de entender (para humanos)
* `-a` ver archivos ocultos

`ls usr/bin` ver los binarios ejecutables tengo por el sistema
`ls usr/bin | wc -l` ver la cantidad de ejecutables (comandos)

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

### Ver directorio actual

`pwd` 

Print Work Directory. Muestra el directorio donde me encuentro.

```bash
$ pwd
output: /home/toshio
```

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

### Cambiar de directorio

`cd [ruta]`

Change Directory. Sirve para moverse entre directorios.

`cd ..` retrocede un directorio.
`cd ~` se mueve al home.

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

### Crear una carpeta

`mkdir [directorio]` 

Make Directory. Crea un directorio.

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

### Crear archivos

`touch [archivo]` 
* Si no existe el archivo lo va a crear.
* Si existe le cambia la fecha de modificación.

`touch {1, 2, 3}.txt` permite crear varios archivos

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

### Mover un archivo

`mv [origen] [destino]`

Mueve un archivo a una ruta destino.

```bash
$ mv archivo.txt C:/
```

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

### Cambiar de nombre a un archivo

`mv [archivo] [nuevo nombre]`

Este comando también se usa para renombrar un archivo.

```bash
$ mv archivo.txt nuevo.txt
```

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

### Eliminar archivos

`rm [archivo]` elimina archivos o links. No funciona para eliminar un directorio.
`rm -rf [directorio]` elimina un directorio/carpeta recursivamente.

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

### Ayuda

`man [comando]` 

Es el manual de la terminal, puedes utilizarlo para entender qué hace un comando y sus banderas. Con espacio pasas una página, - con b te regresas una página y con q sales del manual.

Es equivalente a --help

```bash
$ man cd
$ cd --help
```

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

### Copiar

`cp [archivo/folder] [pegar]`

Copia un archivo a otro directorio.

```bash
$ cp archivo.txt C:/
```

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

### Navegar entre 2 directorios

pushd y popd: te permiten navegar entre dos directorios fácilmente.

`pushd [directorio a guardar]`
`popd` me permite regresar al directorio guardado.

Si no se especifica la ruta de `pushd`, se guarda el directorio actual.

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

### Abrir un archivo

`open [archivo]`

Abre el archivo especificado.

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

### Ver las primeras líneas de un archivo

`more [archivo]`

Te da las primeras líneas de lo que hay en el archivo. 
* Para ver la siguiente página utilizamos espacio.
* Enter para pasar línea por línea.
* b para regresar.

`less [archivo]` 

En algunas distribuciones ya no se usa more sino less.

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

### Imprimir todo el contenido de un archivo

`cat [archivo]`

Imprime todo el contenido de un archivo en pantalla.

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

### Ver las últimas líneas de un archivo

`tail [archivo]` te muestra las últimas 10 líneas de un archivo. 
* `-[número]` puedes agregarle un número con el - y pedir más que 10 líneas.
* `-f:` muestra en tiempo real las ultimas lineas del archivo.

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

### Ver ruta ejecutable de un comando

`which [comando]` 

Especifica donde se encuentra el ejecutable del comando

```bash
$ which ls
output: /usr/bin/ls
```

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

### Alias para comandos

`alias [comando_alias]='[comando]'`

Crea un alias para un comando definido. 

```bash
$ alias ll='ls -lh'
```
En este ejemplo se está creando el comando `ll` que ejecutará `ls -lh`. 

Todo lo que se agregue después del alias se agrega automáticamente luego del comando.

```bash
$ ll -a
$ ls -lh -a
```

En el ejemplo, los 2 comandos hacen lo mismo.

Cada vez que abrimos la terminal se ejecuta un programa llamado `.bash_profile` que es una serie de comandos que da de alta unas variables.

En el `.bash_profile` se guardan los alias.

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

### Ver los procesos que están corriendo

`top`

Ver todos los procesos que están corriendo en la computadora de manera interactiva. Es decir, la lista de procesos se va actualizando.

`ps -wA` 

Muestra todos los procesos que se están ejecutando y desde donde vienen. Este comando no es interactivo.

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

### Matar procesos

`kill -9 [proceso id]`

Mata un proceso.

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

### Ejecutar en 2do plano (background)

` &` espacio y amberson para dejar un proceso en background. Esto quiere decir que el usuario va a seguir teniendo el control de la terminal.

```bash
$ npm start &
output: [1] 23954 (Id del proceso)
```

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

### Ejecutar varios procesos

`;` con un punto y coma puedo separar procesos para que se ejecuten en una misma linea. El segundo proceso se ejecuta cuando termine el anterior.

```bash
$ ls; echo "hola"
```

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

### Mostrar cantidad de procesos

`ps -wA | wc -l`

Muestra la cantidad de procesos que se están ejecutando actualmente.

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

### Tiempo de prendida de la computadora

`uptime` 

* Muestra cuánto tiempo lleva prendida la computadora
* Cuántos usuarios se han logueado
* La carga promedio

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

### Uso del disco

`du` muestra la cantidad de espacio usado por los archivos en un directorio. 
* `-h` muestra el output de una manera que se pueda leer mejor.
* `-d [numero]` nivel de profundidad. Cuántos niveles baja de carpeta.

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

### Links

`ln -s [ruta del directorio] [alias]` Crea un alias que apunta a un directorio.
* `-s` link simbolico. Si se usa este parámetro con `rm` solo se elimina el acceso directo.

```bash
ls -s C:/carpeta alias_file 
cd alias_file
```

La terminal está interpretando `cd C:/carpeta`.

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

### Nombre de usuario

`whoami` 

Te dice cual es el usuario que esta operando

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

# Streams

Los streams son una forma de enviar datos a un comando y recibir un output de salida.

* `STDIN` Standard Input. Parametro de entrada.
* `STDOUT` Standard Output. Es la salida por defecto.
* `STDERR` Standard Error. Es la salida en caso suceda un error.

```php
<?php 
echo "número: ";
$d = trim(fread(STDIN, 100));
$i = 0;

while(true) {
  if(++$i % $d == 0) {
    fwrite(STDOUT, sprintf("El %d es múltiplo de %d.\n", $i, $d));
  } else {
    fwrite(STDERR,
    sprintf("Error, El %d NO es múltiplo de %d \n", $i, $d));
  }
  sleep(1);
}
?>
```

```bash
php 1-streams.php 1> salida.log 2> error.log
```
* `>` manda el output a un archivo
* Se guarda la salida en un archivo salida y el error en un archivo error
* Si se usa `>>` en vez de `>`, entonces el archivo se concatena en vez de sobreescribirse

```bash
php 1-streams.php 1> salida.log 2>&1
```
El error y el output aparecen en el mismo archivo

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

# Power Tools

## Buscar cadenas de caracteres

`grep -r [ruta] -e [expresion]` nos ayuda a encontrar cadenas de caracteres dentro de todos los archivos de la ruta que le demos, con expresiones regulares.
* -r: que sea recursivo
* -n: numero de linea donde se encuentra la palabra en el archivo
* -e: expresion regular
* -i: no importa si es mayuscula o minuscula
* -v: muestra solo los resultados que no cumplen con el patrón.

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Buscar archivos

`find [ruta] -name [nombre]` busca en base al nombre y la metadata dentro del directorio que le digamos.
* -name: el nombre del archivo (*.js devuelve todos los archivos que terminan con .js)
* -type: el tipo

`find directorio_origen -type f -name [name] -exec [acción] {} ./directorio_destino \;` busca archivos
según criterio de búsqueda y los copia o mueve todos a un directorio indicado.
* -acción: puede ser `mv` para mover o `cp` para copiar

> `Nota:` colocar el atributo -type f para seleccionar solo los archivos y colocar \; para terminar el comando.

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Fecha actual

`date`

Muestra la fecha actual.

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Tiempo del procesador

`time` 

Muestra tiempo del procesador

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

### Tiempo de ejecución de un proceso

`date; [proceso]; date` 

Con este comando se puede evaluar cuánto se demora en ejecutar un proceso

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

### Emular un navegador

`curl [url]` emula un navegador.
* `> [nombre]` descarga el archivo con el nombre que le has dado.
* `-o [nombre]` igual que el anterior

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

### Comprimir archivos

`zip [nombre.zip] [archivo a comprimir]`: agrega o reemplaza las entradas de un archivo zip de la lista, que puede incluir el nombre especial para comprimir la entrada.

`upzip [archivo]` descomprime un .zip
* `-vl` no descomprime sino que ve lo que hay adentro

`tar` es un comando similar a zip, junta varios archivos en uno solo sin comprimirlos. Después se le dicta un algoritmo de compresión, que es zip.
* `cfz [archivo.tar.gz]` junta y comprime 
* `xfz [archivo .tar.gz]` descomprime

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Pipe

Sirve para encadenar el standard output de un comando con el standard input de otro comando. Pa esto se usa `|`.

* `| wc -l` muestra cantidad de lineas del output.
```bash
$ ls -l | wc -l
```
* `| grep [patrón]` devuelve las lineas que cumplen con el patrón.
```bash
$ cat peliculas.csv | grep Thriller
```
* `| more` muestra la lista de resultados por paginas.
```bash
$ cat peliculas.csv | more
```

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

## Crontab

`crontab` permite programar la ejecución de scripts.
* `-l` muestra la lista de crontab
* `-e` editar la tabla crontab. Con esto se pueden agregar más scripts

```bash
0   16  *   *   *    $Home/src/cronjobs/daily.sh
0   *   *   *   *    $Home/src/cronjobs/hourly.sh
*   *   *   *   *    $Home/src/cronjobs/minutely.sh
```

Columnas:
* minuto 0-59
* hora 0-23
* dia mes 1-31
* mes 1-12
* dia semana: 0-7 (0 y 7 domingo)
* script/comando

**Ejemplo 1 para la columna minuto**
`1` Se ejecuta en el minuto 1
`1,10,18` Se ejecuta en el minuto 1, 10 y 18
`*/5` Se ejecuta cada 5 minutos
`1-10` Se ejecuta los primeros 10 minutos de cada hora
`*` Se ejecuta cada minuto

**Ejemplo 2**
```bash
*/15 4 * * * script.sh
```

Ejecuta script.sh:
* todos los días de la semana
* todos los meses
* todos los días del mes
* a las 4 am
* cada 15 minutos

**Ejemplo 3**
```bash
0 3 * * 1 script.sh
```

Ejecuta script.sh:
* solo si es lunes
* todos los meses
* todos los días del mes
* a las 3 am
* en el minuto cero

**Nota**: al momento de editar la tabla de crontab, asegurarse que se vea ordenado las columnas.

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

# Control de accesos y usuarios

Usurios
* Dueño
* Grupo
* Otros

Operaciones
* Leer
* Escribir
* Ejecutar

Cumple la siguiente matriz

<table>
  <tr>
    <td></td>
    <td>Lectura</td>
    <td>Escritura</td>
    <td>Ejecución</td>
  </tr>
  <tr>
    <td>Dueño</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Grupo</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
  <tr>
    <td>Otros</td>
    <td></td>
    <td></td>
    <td></td>
  </tr>
</table>

## Permisos

Podemos ver los permisos que tiene un archivo con `ls -l`.

```
$ ls -l
drwxr-xr-x 1 Sergio 197609   0 Jul  9 16:43 'a.txt'
```

Los permisos se muestran en el primer bloque del resultado. En el ejemplo anterior sería `drwxr-xr-x`.

Los permisos se pueden separar de la siguiente manera:

```
F/---/---/---
-: dir/link/file
---: permisos del owner (yo)
---: permisos del gropo
---: permisos de todo el mundo
```

Tipos de permisos:
* `r-–` permiso de lectura
* `rw-` permiso de lectura y escritura
* `rwx` permiso de lectura, escritura y ejecución

Los permisos tiene valores numéricos: 
* r = 4
* w = 2
* x = 1

Para otorgar permisos debemos darle un número que sea la suma de cada una de estas tres letras:

```
---: 0
--x: 1
-r-: 2
-wx: 3
r--: 4
r-x: 5
rw-: 6
rwx: 7
````

Para asignar los permisos se debe de dar el número tanto para el owner, el grupo y el público.
```
---/---/---
666: rw-rw-rw-
750: rwxr-x---`
```

Quitar permisos

`chmod o-w nuevo.txt`

Agrega permiso para ejecutar
`chmod +x nuevo.txt`

**Cambiar permisos**

`chmod [numero] [archivo]` 

Permite cambiar los permisos a un archivo.

```bash
$ chmod 750 archivo.txt
```

Comandos importantes

* **chmod** - Cambiar individualmente los permisos
* **chown** - cambiar propietario del archivo
* **chgrop** - cambiar gurpo al que pertenece un archivo

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

### Ejecutar como super user

`sudo [script/comando]`

Ejecuta un comando como super usuario.

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

# Convertir archivos a ejecutable

`#! [ruta del ejecutable]` 

Vuelve un archivo como ejecutable, estamos especificando quién va a ejecutar el comando que sigue.

`#!` necesariamente debe incluirse al inicio del archivo. En la primera línea. 

```php
#! /usr/local/bin/php
<?php
date_default_timezone_set("America/Bogota");
printf("%s\n", data("Y-m-d H:i:s"));
```
En este caso, estamos indicando a `/usr/local/bin/php` que ejecute el comando que está en las líneas posteriores.

De este modo cuando ejecutamos `ejemplo.php` se ejecuta automáticamente y ya no hay que indicar quién se va a encargar de su ejecución.

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

# Compresión de archivos

Comprimir
`gzip archivo.txt`

Descomprimir
`gzip -d archivo.txt`

Combinación de archivos
`tar cf backup.tar backup/*`

Ver contenido
`tar tf backup.tar`

Desagrupar
`tar xf backup.tar`

# Búsqueda de archivos

locate. Búscar en todo el sistema de archivos con sólo el nombre


```bash
sudo updatedb
locate hello.php
```

whereis. Ubica comandos

`whereis echo`

find. Búsca dentro de un arbol de directorio con una serie de criterios

`find . -user mauro -perm 644`
`find . -type f -mtime +7 -exec cp {} ./backup/ \`

# Interacción por HTTP

curl.- Hace pedidos crudos

`curl https://google.com`

Datos crudos
`curl -v https://platzi.com | more`

`curl -v https://platzi.com > dev/null`

wget.- Realiza descargas desde servidores HTTP

wget https://www.php.net/distributions/php-7.3.10.tar.bz2

# Acceso seguro a otras computadoras

## Manejo de paquetes
Exiten los siguientes según la distribución que se este usando

* apt
* zypper
* rpm

Para instalar paguetes:
`apt install lynx`

El paquete anterior permite ver sitios en modo texto

<div align="right">
  <small><a href="#tabla-de-contenido">🡡 volver al inicio</a></small>
</div>

# Automatización de tareas

Bash es un lenguajes de programación y permite automatizar tareas con comandos

Los scripts se deben guardar con extensión .sh

```bash
#!/bin/bash
NEW_DIR=midir

if [ ! -d"~/$NEW_DIR" ]; then
        mkdir ~/$NEW_DIR
fi

cp ejemplo.txt ~/$NEW_DIR/
echo"Todo bien Jefe"``
```

Algunos scripts se ejecutan al iniciar el sistema

`cat /etc/enviroment`

Crea el archivo y agregar algo al PATH
`nano .bashrc`
Ejecuta
`source .bashrc`
Para ver
`echo $PATH`

## Programar tareas

at programa tareas con temporalizador
`date`
`at now +2 minutes`
`>at echo "Hola  mundo" > /home/eocode/hola.txt`
`date ; ls hola.txt`

cron

`crontab -e`

# Power Shell

Para usar power shell puedes usar lo siguiente:

https://esgeeks.com/como-usar-windows-powershell-guia-basica/