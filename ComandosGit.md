# Comandos en Git

## git init

Empezar en la carpeta del disco duro un repositorio, esto crea la carpeta .git que es una carpeta oculta y es lo que git maneja para entender todo lo que estas creando, modificando.

# Proceso entre git add y git commit

## git [add](https://git-scm.com/docs/git-add) "nombreArchivo".extension

Agrega los cambios del archivo al staging area, si no existe el archivo aún los crea.

## git add .

Esto agrega todos los cambios de todos los archivos al stanging area

## [git commit](https://git-scm.com/docs/git-commit)

Una vez agregados los cambios al staging area, registramos estos cambios al repositorio.
Una forma ideal de hacer commit es hacerlo con un mensaje de cambio ej:
**git commit -m "Primera version"**
Si no ponemos un mensaje nos lleva a un editor vim, para que pongamos el mensaje.
Una vez colocado el mensaje para el commit, salimos del vim con **esc + shift + zz** o escribimos **wq**.

**git commit -am " "**

Con esto podemos hacer un commit sin necesidad de hacer un git add anteriormente. Pero para los archivos que ya se hicieron git add anteriormente, si el archivo es totalmente nuevo esto no funcionará.

![Proceso de Git](https://res.cloudinary.com/practicaldev/image/fetch/s--D7nJOADN--/c_imagga_scale,f_auto,fl_progressive,h_900,q_auto,w_1600/https://cl.ly/569e7f0bbfaf/download/Image%25202018-08-29%2520at%25208.26.35%2520PM.png)

Working directory: es nuestro directorio en el que estamos trabajando, el directorio que estamos modificando en nuestra pc.

Staging area:

---

## git status

Muestra el estado del repositorio, con todas las informaciones. Este refleja si nuestro directorio ha sufrido cambios y no hemos realizado esos cambios en el repositorio.

Tambien muestra en que rama nos encontramos.

Ej: un archivo que hemos cambiado algo o una carpeta nueva y un archivo nuevo.

## git show

Esto muestra todos los cambios hechos en el ultimo commit.

## git show nombreArchivo.extension

Muestra el ultimo commit realizado con los cambios realizados.

## git log

Muestra todos los commits realizados. En cada commit nos muestra el codigo del commit, autor con el correo, la fecha, y el msj del commit.

## git log nombreArchivo.extension

Muestra todos los commits hecho a ese archivo.

Si en lugar del nombre del archivos ponemos el codigo del commit nos muestras todos los commit hechos hasta ese commit.

## git rm --cached nombreArchivo.extension

Este elimina el archivo modificado de nuestro staging area. Sirve cuando hacemos un add y luego lo borramos antes de hacer el commit.

## git diff **codigo commit a** **codigo commit b**

Esto nos devuelve la diferencia entre el commit a con el commit b, nos devuelve que cambios difieren entre esos dos commit.

Para ver los codigos de commit esto se hace con **git log** el codigo es es el que le sigue a la palabra commit

![git log](https://desarrolloweb.com/archivoimg/general/4092.png)

son esos codigos de b2c07....
Ej: git diff b2c07.. fa42f3..

Para mejor compresion del git diff es colocar primero el codigo del commit de arriba con uno de abajo. Esto es porque el commit mas arriba representa el commit mas reciente y el de abajo el commit mas viejo.

Esto es bueno ya que asi podemos saber que de nuevo tiene nuestro archivo comparado con el viejo. Sale en **verde** lo que se agregó y en **rojo** lo que se eliminó.

<br>

## git reset CommitId

Nos permite volver a la version de ese commit.
Git reset tiene 1 parametro adicional --soft o --hard "este parametro va después del commitId".

--soft: nos devuelve a esa version pero todo lo que seguia en el staging area sigue ahi.

--hard: nos devuelve a esa version completamente. Es decir si volvemos al primer commit hecho nos traerá todos los primeros cambios que hemos hechos en ese commit y los cambios siguientes con los otros commit quedarán eliminados.

## git checkout commitId archivo.extension

Nos regresa a como era el archivo en ese commit.

👀❗Esto nos modifica a como estaba el achivo, si hacemos git add y luego git commit, perdemos como se veia nuestro archivo originalmente. Para volver a su estado original es con el comando de abajo.

## git checkout main archivo.extension

Nos regresa a como está originalmente luego del ultimo commit.

Git checkout si nos permite volver al futuro luego de ir al pasado. Git reset no, nos deja ahi y nos borra todo el historial siguiente al commit volvido.

![](https://static.platzi.com/media/user_upload/Git%20rm%20Git%20Reset-91d9ece5-b894-48ca-8102-f3bc9e91c5f1.jpg)

## git branch nombredelarama

Con esto podemos crear una nueva rama, al principio solo existe la rama main, pero con git branch creamos una nueva rama.

La rama sirve para que los desarrolladores trabajen en algo en especifico y no modifiquen la rama main, como por ejemplo a alguien se le asigno la rama cabecera y con git branch crea esa rama sin modificar la rama main. **git branch cabecera**

Para movernos de una rama a otra rama, como por ejemplo de la rama main a la rama head, lo hacemos con git checkout nombrerama,

git checkout main: nos lleva a la rama main.

git checkout otraRama: nos lleva a esa rama.

Estando en la otra rama podemos hacer commit y todo pero solo afectará a esa rama. Con git log veremos los commits de la rama main con los commit de la nueva rama, pero si estamos en la rama main con git log solo podremos ver los commits de la rama main.

Ojo 👀❗:**Si hicimos cambios en una rama y no hicimos commit y vamos a la rama main, vamos a perder todos los cambios en esa rama. Por lo tanto siempre hacer un commit antes de cambiar de rama**.

Si hacemos solo **git branch** sin el nombre de la rama, esto nos devolverá las ramas que existen.

## git merge nombreRama

Esto nos fusiona el contenido de nombreRama con nuestra rama actual, con **git status** podemos ver nuestra rama actual.

Si creamos una rama cabecera y queremos ya mezclar el contenido de esa rama con nuestra rama principal, estando en la rama main hacemos **git branch cabecera**. Esto añadirá todos los cambios que hicimos en la rama cabecera a la rama main.

❗**Siempre es bueno agregar a la rama main en lugar de agregar a la rama secundaria el contenido de la rama main.**
