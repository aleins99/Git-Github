# Comandos Git para Github

## git remote add origin main **clave sacada de github https**

## git push origin main

Git envia a Github la rama main. Coloca en github todo lo que tenemos en nuestra rama main.

Si tenemos que enviar otra rama, solo cambiamos en el comando **main** por **nombreRama**.

## git pull origin main

Esto nos trae todo lo que tenemos en github en ese repositorio a la rama main.

Si tenemos que traernos otra rama, solo cambiamos **main** por **nombreRama** que queremos traernos, ej: **git pull origin header** nos trae la rama header a nuestro pc.

## Como crear una llave ssh

**ssh-keygen -t rsa -b 4096 -C "correoelectronicodegithub"**

Esto nos generará dos llaves, una publica y otra privada y lo genera en una carpeta oculta **.ssh** en el directorio donde llamamos al comando.

## .gitignore

Creamos un archivo con este nombre **.gitignore** y este archivo nos sirve para colocar todos los archivos, carpetas etc que no queremos que se agreguen a nuestro repositorio. Por ej: un node modules un archivo con contraseñas, etc.

Una pagina que nos ayuda a saber que hay que ignorar con respecto al lenguaje [Link](https://toptal.com/developers/gitignore).

Ej de como agregar archivos y carpetas en git ignore.

- **.DS_Store** un archivo en especial llamado DS_STORE

- **nombreCarpeta/** las carpetas se agregan con / al final

- **\*.log** archivos con extension .log

- **nombrearchivo.extension** un archivo en especifico

❗Si hacemos un commit estos archivos, carpetas no se van a agregar al repositorio.

## Como trabajar con colaboradores

**Pasos para agregar colaboradores a nuestro proyecto**

1. **_Settings_**

![settings](imagenes/settings.png)

2. **_Collaborators_**

![collaborators](imagenes/collaborators.png)

3. **_Y finalmente, add people_**

![add people](imagenes/addPeople.png)

Ponemos su correo o su usuario de github para agregarlo.

## Pull request

Es una funcionalidad de github (en gitlab llamada merge request y en bitbucket push request), en la que un colaborador pide que revisen sus cambios antes de hacer merge a una rama, normalmente main.

Al hacer un pull request se genera una conversación que pueden seguir los demás usuarios del repositorio, así como autorizar y rechazar los cambios.

El flujo del pull request es el siguiente

1. Se trabaja en una rama paralela los cambios que se desean **(git checkout -b nombreRama)**
1. Se hace un commit a la rama **(git commit -am "")**
1. Se suben al remoto los cambios **(git push origin <rama>)**
1. En GitHub se hace el pull request comparando la rama main con la rama del fix.
1. Uno, o varios colaboradores revisan que el código sea correcto y dan feedback (en el chat del pull request)
1. El colaborador hace los cambios que desea en la rama y lo vuelve a subir al remoto (automáticamente jala la historia de los cambios que se hagan en la rama, en remoto)
1. Se aceptan los cambios en GitHub
1. Se hace merge a main desde GitHub

❗**Importante**: Cuando se modifica una rama, también se modifica el pull request.

## Fork

Hace una copia de un repositorio de alguien mas y lo agrega a nuestros repositorios en nuestra cuenta de Github.

## git clone linkRepo

Clonamos un repo a nuestro ordenador. Esto nos descarga una carpeta con el nombre del repo con todo su contenido y ya con el .git. Y lo crea en la ruta de nuestra linea de comandos donde hicimos el git clone.

❗Para poder clonarlo, ese repositorio tiene que estar en nuestros repositorios de github. Si no lo tenemos hay que hacerle un fork a ese repositorio y luego ya podremos clonarlo.

## Como traer nuevos cambios del repo original.

Si forkeamos un repo de alguien mas y luego de hacer fork y clonar ese repo, esa persona ya hizo nuevos cambios, no podemos directamente hacer un **git pull origin main** porque solo traeremos los cambios de nuestro repo y no del original.

Para solucionar esto, creamos una nueva rama y lo hacemos con **git remote add upstream linkRepoOriginal** esto no trae al repo original guardado en **upstream** y podemos verificar que se agregó con **git remote -v**,veremos que tenemos dos ramas, una que sería **origin** que es de nuestro repo y otra que sería **upstream** que es del repo original. Ya teniendo esa rama podemos traer los nuevos cambios con **git pull upstream main**.

Obs: puede ser upstream o cualquier nombre para el repo original pero conmunmente se usa upstream.

Ahora ya que tenemos una rama del repo original siempre que haiga cambios en ella podemos traernos directamente esos cambios con **git pull upstream main**
