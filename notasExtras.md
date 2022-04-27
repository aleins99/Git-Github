ojo -> Guardar archivos binarios en el repositorio de git es una mala práctica, únicamente deberían guardarse archivos pequeños (como logos) que no sufran casi modificaciones durante la vida del proyecto. Los binarios deben guardarse en un CDN”.

Si a un archivo sufre modificaciones y no se hace git add el archivo esta en estado untracked, cuando se hace git add entra en estado tracked y entra en el staging area, luego de hacer commit recien se agrega al repositorio.

## **Comandos utilizados en cada área**

![](https://static.platzi.com/media/user_upload/estados-git-0acb84f7-5080-4098-99d9-59012a3b8e86.jpg)

Ojo 👀❗: Si hicimos cambios en una rama y no hicimos commit y nos cambiamos a otra rama, vamos a perder todos los cambios en esa rama. Por lo tanto siempre hacer un commit antes de cambiar de rama.

---

Si en la rama secundaria modificamos algo de la rama main, esto nos daría error de conflicto luego de hacer merge a la rama main y nos saltará un error de con cual nos quedamos, si el cambio de la rama main o la modificacion de esa linea en la rama secundaria. Esto es tan simple de solucionar con eliminar la que no queremos y hacemos commit.
