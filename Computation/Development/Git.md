# Git

## Repositorios
- Crear repositorio local `git init`
- Comprobar si hay algún remoto `git remote -v`
- Clonar `git clone https://github.com/JuanGo500/nombrerepository.git`
- Añadir un repositorio remoto `git remote add origin https://github.com/USERNAME/REPOSITORY.git`
- Quitar repositorio remoto `git remote rm origin`
- Cambiar la url (se debe añadir primero algún repositorio) `git remote set-url origin https://github.com/USERNAME/REPOSITORY.git`
- Establecer la rama upstream `git push --set-upstream origin master`
- forzar push: `git push -f origin branchname`
  
## Ramas
- Crear una rama `git branch nombrerama`
- Comprobar ramas `git branch`
- Borrar rama `git branch -d nombrerama`
- Cambiar de rama `git checkout`
- Cambiar de nombre `git branch -m master main`
- Borrar rama en remoto `git push origin --delete master`
- Cargar rama en working directory `git checkout nombrerama`
- Volver a un commit anterior
`git checkout <hashcommit>`

## Aprobación
- Añadir ficheros a stash: 
  - `git add -A`
  - `git add --all`
  - `git add .`
- Hacer commit: `git commit -m 'mensaje para este commit'`
- Hacer merge: `git merge <ramaOrigen> previamente se hace git checkout <ramaDestino>`

## Rectificar
- Si se ha subido a remoto: `git revert HEAD`
- Dar un paso atrás y dejar ficheros en staged: `git reset --soft HEAD^`

### Etiquetar
- Etiquetar: `git tag v0.0.2 -m "Segunda versión, cambios menores"`
- Ver etiquetas: `git tag`
- Etiquetar a posteriori `git tag -a v1.2 9fceb02`
