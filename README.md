# Git Avanzado

## Conceptos basicos

- VCS : Version Control System, paradigma que usa git para el trabajo colaborativo

- Repo/Repositorio: Contenedor de proyectos, el cual conserva una historia de los cambios que se han almacenado dentro de un proyecto

- Branch/Rama: Una separacion o fork del repositorio de git, tipicamente usado para trabajar en cambios no relacionados de manera independiente

- Remote/Remoto: Copia remota del repositorio, almacenada en algun sitio de hosting de VCS

- Commit : Conjunto logico de cambios

- Stage/Staged : cambios que estan listos para ser 'commit'eados, pero aun no se han subido el repositorio remoto

- Working directory: El directorio en tu computadora donde estan almacenados tus archivos

- Staging area : Area donde estan los archivos que estan en la fase de 'staging', es decir, que estan listos para ser commiteados

- HEAD : Commit actual

## Notas importantes

- Git esta hecho para trabajar en equipo

- Git no esta hecho para hacer respaldos o backups

- Git nunca olvida

- Git no miente


## Arquitectura de Git

[arquitectura] https://i.stack.imgur.com/NuThL.png


## Comandos basicos

### Status (AKA tu mejor amigo)

Monitorea el estado actual de tu repositorio

```console
hacka@palooza:~$ git status

```

### Status (AKA tu mejor amigo)

Pasa los cambios dentro del staging area a HEAD

Hacer commit con editor de archivos de la consola
```console
hacka@palooza:~$ git commit

```

Hacer commit con un mensaje corto
```console
hacka@palooza:~$ git commit -m "Mensaje de commit"

```

Hacer commit a todos los archivos, stage o unstaged
```console
hacka@palooza:~$ git commit -a

```
```console
hacka@palooza:~$ git status

```

### Push

Sin especificar repositorio remoto o branch, git push empuja la branch actualmente seleccionado al repositorio 'origin'

```console
hacka@palooza:~$ git push 

```

De otra manera, podemos especificar un repositorio remoto y branch de la siguiente manera
```console
hacka@palooza:~$ git push [remote] [branch]

```

### Pull

Sin especificar repositorio remoto o branch, git pull actualiza la branch actualmente seleccionada (Digamosle 'actual'), tomando como base la branch 'origin/{actual}'

```console
hacka@palooza:~$ git pull 

```

De otra manera, podemos especificar un repositorio remoto y branch de la siguiente manera
```console
hacka@palooza:~$ git pull [remote] [branch]

```

### Checkout

NOTA: Para hacer checkout, no debes de tener cambios en el staging area o working directory

Para crear una nueva branch con nombre 'miBranch'

```console
hacka@palooza:~$ git checkout -b 'miBranch'

```

Para cambiar a una branch con nombre 'miBranch'

```console
hacka@palooza:~$ git checkout 'miBranch'

```

### Merge

NOTA: Para hacer merge, no debes de tener cambios en el staging area o working directory

Para mezclar los cambios de la branch 'bar' dentro de la branch 'foo':

```console
hacka@palooza:~$ git merge foo bar
```

Si quieres hacer merge con los cambios de una branch remota, esto tambien es posible. En este caso, a la branch 'foo' le aplicaremos los cambios de la branch 'bar', situada en el remoto 'origin'

```console
hacka@palooza:~$ git merge foo origin/bar
```

### Ver differencias entre branches

```console
hacka@palooza:~$ git diff [branch]
```

## Tips chidos


###Quitar un archivo del tracking de git (con staging)


```console
hacka@palooza:~$  git rm --cached [archivo]
```

###Hacer unstage a los cambios staged de un archivo

```console
hacka@palooza:~$  git reset -- [archivo]
```
###Actualizar repo con nuevo .gitignore
```console
hacka@palooza:~$ git rm -r --cached .
hacka@palooza:~$ git add .
```
###Agregar archivos con patch
```console
hacka@palooza:~$ git add --patch
```
Opciones: 
y - stage this hunk
n - do not stage this hunk
a - stage this and all the remaining hunks in the file
d - do not stage this hunk nor any of the remaining hunks in the file
g - select a hunk to go to
/ - search for a hunk matching the given regex
j - leave this hunk undecided, see next undecided hunk
J - leave this hunk undecided, see next hunk
k - leave this hunk undecided, see previous undecided hunk
K - leave this hunk undecided, see previous hunk
s - split the current hunk into smaller hunks
e - manually edit the current hunk
? - print help

### CRLF - LF

Dentro de tu archivo .gitattributes:

Para mantener CRLF (OSX/Linux-style)
```text
text eol=crlf
```

Para mantener LF (Windows-style)

```text
text eol=crlf
```

### Stash

Para restaurar un repo a su ultimo commit

```console
hacka@palooza:~$ git stash
```

Para devolver los cambios que se habian hecho
```console
hacka@palooza:~$ git stash pop
```

### Revert

Des-aplicar los cambios de un commit

```console
hacka@palooza:~$ git revert [commit]
```


### Cherry-pick

Aplicar los cambios de un commit

```console
hacka@palooza:~$ git cherry-pick [commit]
```

### Arreglar un commit
```console
hacka@palooza:~$ git commit --amend
```

### Deshacer un commit
```console
$ git commit -m "Something terribly misguided"             # (1)
$ git reset HEAD~                                          # (2)
<< edit files as necessary >>                              # (3)
$ git add ...                                              # (4)
$ git commit -c ORIG_HEAD    
```

##COMANDOS PELIGROSOS

### Hard reset
Cambiar HEAD (Cambia tambien el staging y index)
```console
git reset --hard [commit]
```

### Force push
Empuja sin importarle las diferencias entre los repos
```console
git push --force
```

###Borrar historia
```console
rm -rf .git
git init
git add .
git commit -m "Initial commit"
git remote add origin <github-uri>
git push -u --force origin master
```
