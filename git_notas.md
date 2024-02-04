# Notas Git

## Para ver la version de git

`git version`

## Para el nombre de usuario de la cuenta git

`git config --global user.name "mi nombre"`

Para agregar tu correo electronico

`git config --global user.email "myemail@example.com"`

Para mostrarlos en la terminal

```Bash
git config user.name
git config user.email
```

## Obtener ayuda para los comandos

`git help`

## Craer un nuevos repositorio

Para crear un nuevo repositorio se utiliza el comando `git init`, este comando se utiliza solo una vez por proyecto y genera los siguientes cambios:

- Inicia un nuevo repositorio.
- crea la carpeta `.git/` la cual contendra todos los commit del proyecto.

### Primeros pasos al crear un repo

Despues de realizar un `git init` puedes ver el status de los archivos del proyecto usando el comando `git status -s`, el ouput fue el siguiente:

```Bash
?? <Nombre_del_Archivo>
```

El `??` al lado del nombre del archivo el el estatus actual, este estado quiere decir que el archivo no tiene seguimiento, por lo tanto hay que anadir el archivo a revision usando el comando `git add <Nombre_del_Archivo>`, al hacer esto el output va a ser el siguiente:

```Bash
A  <Nombre_del_Archivo>
```

El status `A` quiere decir que el archivo esta en seguimiento, pero al hacer cualquier modificacion al archivo el status cambia a `AM`, eso quiere decir que el archivo esta en sequimiento pero se ha modificado, para solucionar esto se tiene que volver a ejecutar el comando `git add <Nombre_del_Archivo>`

Una vez todos los archivos esten en en seguimientos y su status sea `A` se puede annadir estos cambios a un registro temporal llamado commit, para realizar un commit se utiliza el comando `git commit -m "Mensaje"`, al commit se annadira todos los archivos en seguimiento.

Para regresar los cambios del archivo alo registrado en un commit primero necesitamos saber su identificador, para ellos usamos el comando `git log --oneline` para ver los detalles de cada commit, esto retorna los siguiente:

```Bash
a5bd56b (HEAD -> master) Segundo Commit
b11b1ae Primer Commit
```

En la primera fila se muetra el indentificador del commit, para regresar los cambios a un commit anterior usamos el comando `git reset --hard <Identificador>`.

> ***NOTA:*** *despues de un commit, al momento de realizar un cambio el status del archivo cambiara a `M` que significa modificado, si quieres hacer un commit del archivo modificado primero tendras que annadir nuevamente el archivo al area temponal con `git add <Nombre_del_Archivo>` y luego realizar el commit con `git commit - m "Mensaje"`*
---
> Para ver todos los commit puser usar el comando `git log --oneline`

## Ultimos pasos con GITHUB

Ya sabemos que con `git push` podemos enviar todos nuestro archivos a un repositorio en la nube, pero que pasa si en vez de enviar los cambios a la nube, necesitamos traer los documentos que tenemos en github pero no en nuestro proyecto, para eso existen dos comandos:

- **El Comando `git pull`**: Este comando traer todos los cambios y archivos que estan solo en github a nuestro proyecto.

- **El Comando `git fetch`**: Este comando compara ambos repositorios y los deja a la par.
