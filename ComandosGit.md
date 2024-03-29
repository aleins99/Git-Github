# Comandos en Git

## git init

Empezar en la carpeta del disco duro un repositorio, esto crea la carpeta .git que es una carpeta oculta y es lo que git maneja para entender todo lo que estas creando, modificando.

# Proceso entre git add y git commit

## git [add](https://git-scm.com/docs/git-add) "nombreArchivo".extension

Agrega los cambios del archivo al staging area, si no existe el archivo aún, los crea.

## git add .

Esto agrega todos los cambios de todos los archivos del directorio en el que estamos al stanging area

## [git commit](https://git-scm.com/docs/git-commit)

Una vez agregados los cambios al staging area, registramos estos cambios al repositorio.
Una forma ideal de hacer commit es hacerlo con un mensaje de cambio ej:
**git commit -m "Primera version"**
Si no ponemos un mensaje, nos lleva a un editor vim o (nano en ubuntu), para que pongamos el mensaje.
Una vez colocado el mensaje para el commit, salimos del vim con **esc + shift + zz** o escribimos **wq**.

**git commit -am " "**

Con esto podemos hacer un commit sin necesidad de hacer un git add anteriormente. Pero esto sirve para los archivos que ya se hicieron git add anteriormente, si el archivo es totalmente nuevo esto no funcionará.

**git commit --amend**

Con este comando deshacemos el ultimo commit. Esto sirve por si hacemos un commit mal, ya sea pusimos mal el mensaje o no incluimos todos los archivos.

Obs: se modifica los archivos antes de hace el commit --amend, si por ejemplo no incluimos un archivo y hicimos commit para agregar ese archivo al commit, hacemos git add del archivo y luego hacemos commit --amend.

![Proceso de Git](https://res.cloudinary.com/practicaldev/image/fetch/s--D7nJOADN--/c_imagga_scale,f_auto,fl_progressive,h_900,q_auto,w_1600/https://cl.ly/569e7f0bbfaf/download/Image%25202018-08-29%2520at%25208.26.35%2520PM.png)

Working directory: es nuestro directorio en el que estamos trabajando, el directorio que estamos modificando en nuestra pc.

Staging area: es donde se guarda antes de mandarlo al repositorio.

repository : este seria el repositorio donde vamos a tener guardado todos nuestros archivos.

## git status

Muestra el estado del repositorio, con todas las informaciones. Este refleja si nuestro directorio ha sufrido cambios y no hemos realizado esos cambios en el repositorio.

Tambien muestra en que rama nos encontramos.

Ej: un archivo que hemos cambiado algo o una carpeta nueva y un archivo nuevo.

## git show

Esto muestra todos los cambios hechos en el ultimo commit.

## git show nombreArchivo.extension

Muestra todos los cambios que hicimos en el último commit pero a este archivo en específico.

## git log

Muestra todos los commits realizados. En cada commit nos muestra el codigo del commit, autor con el correo, la fecha, y el msj del commit.

Podemos agregar parametros como **--oneline** esto hace que solo veamos el prefijo del commitId con solo el mensaje.

Otro parametro es **--abbrev-commit** como su nombre lo indica nos trae todos los commits pero con una abreviacion del commitId.

## git log nombreArchivo.extension

Muestra todos los commits hecho a ese archivo.

Si en lugar del nombre del archivo ponemos el codigo del commit, nos muestras todos los commit hechos hasta ese commit (HEAD -> ramaActual).

## git rm --cached nombreArchivo.extension

Este elimina el archivo modificado de nuestro staging area. Sirve cuando hacemos un add y luego lo borramos antes de hacer el commit.

## git diff **codigo commit a** **codigo commit b**

Esto nos devuelve la diferencia entre el commit a con el commit b, nos devuelve que cambios difieren entre esos dos commit.

Para ver los codigos de commit esto se hace con **git log** el codigo es es el que le sigue a la palabra commit.

![git log](https://desarrolloweb.com/archivoimg/general/4092.png)

son esos codigos de b2c07....
Ej: git diff b2c07.. fa42f3..

Para mejor compresion del git diff es colocar primero el codigo del commit de arriba con uno de abajo. Esto es porque el commit mas arriba representa el commit mas reciente y el de abajo el commit mas viejo.

Esto es bueno ya que asi podemos saber que de nuevo tiene nuestro archivo comparado con el viejo. Sale en **verde** lo que se agregó y en **rojo** lo que se eliminó.

<br>

## git reset CommitId

Nos permite volver a la version de ese commit.
Git reset tiene 1 parametro adicional --soft o --hard "este parametro va después del commitId".

--soft: nos devuelve a esa version pero todo lo que seguia en el staging area sigue ahí.

--hard: nos devuelve a esa version completamente. Es decir si volvemos al primer commit hecho nos traerá todos los primeros cambios que hemos hechos en ese commit y los cambios siguientes con los otros commit quedarán eliminados.

## git checkout commitId archivo.extension

Nos regresa a como era el archivo en ese commit. Pero a diferencia de git reset, podemos volver sin problemas a como estaba anteriormente.

👀❗Esto nos modifica a como estaba el achivo, si hacemos git add y luego git commit, perdemos como se veia nuestro archivo originalmente. Para volver a su estado original es con el comando de abajo.

## git checkout main archivo.extension

Nos regresa a como está originalmente luego del ultimo commit.

Git checkout si nos permite volver al futuro luego de ir al pasado. Git reset no, nos deja ahi y nos borra todo el historial siguiente al commit volvido.

![](https://static.platzi.com/media/user_upload/Git%20rm%20Git%20Reset-91d9ece5-b894-48ca-8102-f3bc9e91c5f1.jpg)

## git branch nombredelarama

Con esto podemos crear una nueva rama, al principio solo existe la rama main, pero con git branch creamos una nueva rama.

La rama sirve para que los desarrolladores trabajen en algo en especifico y no modifiquen la rama main, como por ejemplo a alguien se le asigno la rama cabecera y con git branch crea esa rama sin modificar la rama main. **git branch cabecera**

Para movernos de una rama a otra rama, como por ejemplo de la rama main a la rama head, lo hacemos con **git checkout nombrerama**,

git checkout main: nos lleva a la rama main.

git checkout otraRama: nos lleva a esa rama.

Estando en la otra rama podemos hacer commit y todo pero solo afectará a esa rama. Con git log veremos los commits de la rama main con los commit de la nueva rama, pero si estamos en la rama main con git log solo podremos ver los commits de la rama main.

Ojo 👀❗:**Si hicimos cambios en una rama y no hicimos commit y vamos a la rama main, vamos a perder todos los cambios en esa rama. Por lo tanto siempre hacer un commit antes de cambiar de rama**.

Si hacemos solo **git branch** sin el nombre de la rama, esto nos devolverá las ramas que existen.

## git merge nombreRama

Esto nos fusiona el contenido de nombreRama con nuestra rama actual, con **git status** podemos ver nuestra rama actual.

Si creamos una rama cabecera y queremos ya mezclar el contenido de esa rama con nuestra rama principal, estando en la rama main hacemos **git branch cabecera**. Esto añadirá todos los cambios que hicimos en la rama cabecera a la rama main.

❗**Siempre es bueno agregar a la rama main en lugar de agregar a la rama secundaria el contenido de la rama main.**

## git switch nombreRama

Nos movemos a nombreRama, es lo mismo que git checkout nombreRama pero este es mas práctico.

Tambien tenemos **git switch -c nombreRama**: este comando nos crea una nueva rama y nos mueve a esa rama de una, es un shortcut al **git branch nombreRama y luego git switch nombreRama**.

## git stash

Con este comando podemos guardar cambios que no aun no queremos hacerles commits, serviría por _EJ_: si hacemos cambios a un archivo y aun no queremos hacer **git add** ni **git commit** y queremos mudarnos a otra rama sin perder esos cambios. Para esto nos sirve **git stash**, nos guarda los cambios que hicimos, poder cambiarnos a otra rama y luego volver a nuestra rama y recuperar esos cambios con **git stash pop**.

## git rebase

Git rebase es una operación fundamental en Git que se utiliza para combinar cambios de una rama en otra de una manera más limpia y lineal que una fusión tradicional (merge). A continuación, te explicaré cómo funciona el comando **git rebase** y cuándo es útil:

1. **Entendiendo el Problema**:
   Imagina que tienes una rama principal (por ejemplo, **main**) y has creado una rama secundaria (por ejemplo, **mi_feature**) para trabajar en una nueva función. Mientras trabajas en **mi_feature**, es posible que otros colaboradores hayan estado haciendo cambios en la rama **main**. Cuando terminas tu trabajo en **mi_feature**, deseas incorporar estos cambios de **main** en tu rama de manera que tu historia de commits sea más limpia y no tenga ramificaciones innecesarias.

2. **Pasos para utilizar **git rebase**:
   A continuación, se muestra cómo usar **git rebase** en este escenario:
   - Asegúrate de estar en la rama **mi_feature**: **git checkout mi_feature**
   - Luego, ejecuta el comando de rebase: **git rebase main**

   Lo que hace esto es tomar todos los commits que hiciste en **mi_feature**, los quita temporalmente, lleva tu rama a la punta de **main**, y luego aplica tus commits nuevamente uno por uno en la parte superior de **main**. Esto crea una historia de commits lineal y limpia.

3. **Resolución de Conflictos**:
   Es posible que surjan conflictos durante el proceso de rebase si los cambios en **main** y **mi_feature** afectan las mismas líneas de código. Debes resolver estos conflictos manualmente, y luego continuar el proceso de rebase con **git rebase --continue**.

4. **Ventajas de Git Rebase**:
   - Mantiene una historia de commits más lineal y limpia en comparación con las fusiones, lo que facilita la revisión y la comprensión de la historia del proyecto.
   - Ayuda a evitar commits de fusión innecesarios que pueden ensuciar la historia del repositorio.
   - Facilita la identificación y corrección de conflictos durante el proceso de rebase.

5. **Precauciones**:
   - No debes rebasear ramas que compartes con otros colaboradores, ya que reescribir la historia puede causar problemas en el trabajo de los demás.
   - Es seguro utilizar **git rebase** en ramas privadas o temporales, pero debes ser cauteloso al hacerlo en ramas compartidas.

En resumen, **git rebase** es útil para mantener una historia de commits limpia y lineal al incorporar cambios de una rama en otra. Sin embargo, debes usarlo con cuidado y comprender sus implicaciones, especialmente cuando trabajas en colaboración con otros desarrolladores.