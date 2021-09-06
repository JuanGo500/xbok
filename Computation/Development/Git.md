# Git

## Comandos

Crear repositorio local `git init`

## Repositorio remoto
- Comprobar si hay algún remoto `git remote -v`
- Clonar `git clone https://github.com/JuanGo500/nombrerepository.git`
- Añadir un repositorio remoto `git remote add origin https://github.com/USERNAME/REPOSITORY.git`
- Quitar repositorio remoto `git remote rm origin`
- Cambiar la url (se debe añadir primero algún repositorio) `git remote set-url origin https://github.com/USERNAME/REPOSITORY.git`
- Establecer la rama upstream `git push --set-upstream origin master`

### Ramas
- Crear una rama `git branch nombrerama`
- Comprobar ramas `git branch`
- Borrar rama `git branch -d nombrerama`
- Cambiar de rama `git checkout`
- Cambiar de nombre `git branch -m master main`
- Borrar rama en remoto `git push origin --delete master`
- Cargar rama en working directory `git checkout nombrerama`
- Volver a un commit anterior
`git checkout hashcommit`

### Aprobación
- Añadir ficheros a stash: 
  - git add -A
  - git add --all
  - git add .
- Hacer commit
  - git commit -m 'mensaje para este commit'
### Etiguetar
- Etiquetar: git tag v0.0.2 -m "Segunda versión, cambios menores"
- Ver etiquetas: git tag

