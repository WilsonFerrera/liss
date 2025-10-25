# 📚 Comandos de GitHub - Guía de Referencia

Una guía completa de comandos esenciales de GitHub para el desarrollo colaborativo.

## 📋 Tabla de Contenidos

- [🔧 Configuración Inicial](#-configuración-inicial)
- [📁 Gestión de Repositorios](#-gestión-de-repositorios)
- [🌿 Trabajo con Ramas](#-trabajo-con-ramas)
- [📤 Subir Cambios](#-subir-cambios)
- [📥 Obtener Cambios](#-obtener-cambios)
- [🔄 Sincronización](#-sincronización)
- [🔀 Fusionar Cambios](#-fusionar-cambios)
- [📝 Gestión de Commits](#-gestión-de-commits)
- [🏷️ Etiquetas](#️-etiquetas)
- [👥 Colaboración](#-colaboración)
- [🔍 Inspección](#-inspección)

---

## 🔧 Configuración Inicial

### Configurar Git por primera vez
```bash
# Configurar nombre de usuario
git config --global user.name "Tu Nombre"

# Configurar email
git config --global user.email "tu.email@ejemplo.com"

# Verificar configuración
git config --list
```

### Configurar SSH
```bash
# Generar clave SSH
ssh-keygen -t ed25519 -C "tu.email@ejemplo.com"

# Agregar clave al agente SSH
ssh-add ~/.ssh/id_ed25519

# Copiar clave pública (para agregar en GitHub)
cat ~/.ssh/id_ed25519.pub
```

---

## 📁 Gestión de Repositorios

### Crear y clonar repositorios
```bash
# Inicializar repositorio local
git init

# Clonar repositorio existente
git clone https://github.com/usuario/repositorio.git

# Clonar con SSH
git clone git@github.com:usuario/repositorio.git

# Clonar rama específica
git clone -b nombre-rama https://github.com/usuario/repositorio.git
```

### Agregar remotos
```bash
# Ver remotos configurados
git remote -v

# Agregar remoto
git remote add origin https://github.com/usuario/repositorio.git

# Cambiar URL del remoto
git remote set-url origin https://github.com/usuario/nuevo-repo.git

# Eliminar remoto
git remote remove origin
```

---

## 🌿 Trabajo con Ramas

### Crear y cambiar ramas
```bash
# Ver todas las ramas
git branch -a

# Crear nueva rama
git branch nombre-rama

# Cambiar a rama
git checkout nombre-rama

# Crear y cambiar a nueva rama
git checkout -b nueva-rama

# Eliminar rama local
git branch -d nombre-rama

# Eliminar rama forzadamente
git branch -D nombre-rama
```

### Trabajar con ramas remotas
```bash
# Crear rama remota
git push -u origin nombre-rama

# Eliminar rama remota
git push origin --delete nombre-rama

# Obtener todas las ramas remotas
git fetch --all

# Crear rama local desde rama remota
git checkout -b local-rama origin/remota-rama
```

---

## 📤 Subir Cambios

### Flujo básico de trabajo
```bash
# Ver estado del repositorio
git status

# Agregar archivos al staging
git add archivo.txt
git add .                    # Agregar todos los archivos
git add *.js                 # Agregar archivos específicos

# Crear commit
git commit -m "Mensaje descriptivo del cambio"

# Subir cambios
git push origin main
```

### Commits más detallados
```bash
# Commit con descripción extendida
git commit -m "Título del commit

Descripción detallada de los cambios realizados:
- Cambio específico 1
- Cambio específico 2
- Corrección de bug en..."

# Agregar cambios al último commit
git commit --amend -m "Nuevo mensaje"
```

---

## 📥 Obtener Cambios

### Obtener cambios del repositorio remoto
```bash
# Descargar cambios sin fusionar
git fetch origin

# Descargar y fusionar cambios
git pull origin main

# Obtener cambios de todas las ramas
git fetch --all

# Obtener cambios de rama específica
git fetch origin nombre-rama
```

---

## 🔄 Sincronización

### Mantener repositorio actualizado
```bash
# Sincronizar con rama principal
git checkout main
git pull origin main

# Sincronizar rama de trabajo
git checkout mi-rama
git rebase main
# o
git merge main
```

---

## 🔀 Fusionar Cambios

### Merge vs Rebase
```bash
# Fusionar rama (crea merge commit)
git checkout main
git merge nombre-rama

# Rebase (historial lineal)
git checkout nombre-rama
git rebase main

# Rebase interactivo
git rebase -i HEAD~3
```

### Resolver conflictos
```bash
# Ver archivos en conflicto
git status

# Editar archivos para resolver conflictos
# Luego agregar archivos resueltos
git add archivo-resuelto.txt

# Continuar merge/rebase
git commit  # para merge
git rebase --continue  # para rebase
```

---

## 📝 Gestión de Commits

### Historial y logs
```bash
# Ver historial de commits
git log

# Ver historial con gráfico
git log --oneline --graph

# Ver cambios en commit específico
git show commit-hash

# Ver diferencias
git diff
git diff --staged
git diff HEAD~1
```

### Modificar historial
```bash
# Resetear a commit anterior
git reset --soft HEAD~1    # Mantiene cambios en staging
git reset --mixed HEAD~1   # Mantiene cambios en working directory
git reset --hard HEAD~1    # Elimina todos los cambios

# Revertir commit específico
git revert commit-hash
```

---

## 🏷️ Etiquetas

### Crear y gestionar tags
```bash
# Crear tag ligero
git tag v1.0.0

# Crear tag anotado
git tag -a v1.0.0 -m "Versión 1.0.0"

# Ver todos los tags
git tag

# Subir tags al remoto
git push origin v1.0.0
git push origin --tags  # Subir todos los tags

# Eliminar tag
git tag -d v1.0.0
git push origin --delete v1.0.0
```

---

## 👥 Colaboración

### Pull Requests y Issues
```bash
# Crear rama para nueva funcionalidad
git checkout -b feature/nueva-funcionalidad

# Trabajar en la funcionalidad
# ... hacer commits ...

# Subir rama
git push -u origin feature/nueva-funcionalidad

# Crear Pull Request desde GitHub
# O usar GitHub CLI
gh pr create --title "Nueva funcionalidad" --body "Descripción detallada"
```

### Fork y contribución
```bash
# Fork del repositorio en GitHub
# Luego clonar tu fork
git clone https://github.com/tu-usuario/repositorio-fork.git

# Agregar repositorio original como upstream
git remote add upstream https://github.com/original/repositorio.git

# Sincronizar con upstream
git fetch upstream
git checkout main
git merge upstream/main
```

---

## 🔍 Inspección

### Comandos de diagnóstico
```bash
# Ver configuración
git config --list

# Ver información del repositorio
git remote -v
git branch -a

# Ver estado detallado
git status -v

# Ver historial de una rama
git log --oneline nombre-rama

# Ver diferencias entre ramas
git diff main..nombre-rama

# Ver archivos modificados
git diff --name-only
git diff --name-status
```

### Comandos útiles adicionales
```bash
# Limpiar archivos no rastreados
git clean -fd

# Ver qué archivos están siendo ignorados
git status --ignored

# Ver información de un archivo específico
git log --follow archivo.txt

# Buscar en el historial
git log --grep="palabra-clave"
```

---

## 🚀 Comandos Avanzados

### Stash (guardar cambios temporalmente)
```bash
# Guardar cambios temporalmente
git stash

# Ver lista de stashes
git stash list

# Aplicar último stash
git stash pop

# Aplicar stash específico
git stash apply stash@{0}

# Eliminar stash
git stash drop stash@{0}
```

### Cherry-pick
```bash
# Aplicar commit específico a otra rama
git cherry-pick commit-hash

# Cherry-pick múltiples commits
git cherry-pick commit1 commit2 commit3
```

---

## 📚 Recursos Adicionales

- [Documentación oficial de Git](https://git-scm.com/doc)
- [GitHub Docs](https://docs.github.com/)
- [GitHub CLI](https://cli.github.com/)
- [Pro Git Book](https://git-scm.com/book)

---

## 🤝 Contribuciones

¡Las contribuciones son bienvenidas! Si encuentras algún error o quieres agregar más comandos útiles, por favor:

1. Fork el repositorio
2. Crea una rama para tu feature (`git checkout -b feature/nueva-funcionalidad`)
3. Commit tus cambios (`git commit -m 'Agregar nueva funcionalidad'`)
4. Push a la rama (`git push origin feature/nueva-funcionalidad`)
5. Abre un Pull Request

---

<div align="center">

**⭐ Si este README te fue útil, ¡dale una estrella al repositorio! ⭐**

</div>