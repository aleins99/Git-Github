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
