# Git Avanzado

## Comandos basicos

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
