# Trabajo Individual

Ian Hans Escobar Urey

## Clase 1
### ¿Qué es git?

Sistema de control de versiones distribuido

* Permite guardar archivos y las versiones de estos a lo largo del tiempo de manera local

### ¿Cómo nació?

Linus Torvalds lo creó por necesidad ya que se enojo jsjsjs

### ¿Cómo instalar git?

#### Windows

descargar e instalar el ejecutable proporcionado por git

#### Linux
1. por navegador
2. ir a git-scm.com o buscar git download
3. buscar comando de instalación
4. ejecutar en terminal


Para verificar que se instalo correctamente

``` 
git --version
```

### Configuración basica

```

git config --global user.name "Nombre"
git config --global user.email "email.github@gmail"

git config --list

```

### Archivos que todo repo debe tener

* README.md
    * El formato de los .md es markdown
    * Indica de que es el proyecto

* .gitignore

### Como inicializar

Para crear el repositorio es el siguiente comando 
```
git init
```

#### Comandos básicos
* git status 
    * muestra el estado actual del proyecto
* git add
    * añade los archivos al arbol de seguimiento de git
* git commit
    * esto confirma los cambios 
    * para añadir descripción usar la flag -m

---

## Clase 2

### States y Commits

Los estados de git

* Directorio de trabajo ( Modificado )
    * Las modificaciones que se hizo en el proyecto sin asegurarlos

* Stage Area ( Preparado )


* Repositorio Local ( Confirmado )

### Diagrama del flujo de trabajo

el flujo de trabajo es

![flujo de trabajo git](/Imagenes/clase_2_imagenes/flujo_trabajo_git.png)

#### Directorio de Trabajo

Git cataloga los archivos en:
* **untracked**
    * que son archivos nuevos que git no tieneen su historial
* **modified**
    * cuando git detecta un cambio en los archivos que ya tiene en su historial


Esto solo ocurre si los archivos no fueron ignorados por el .gitignore


#### .gitignore

ignora todos los archivos que se mencionen dentro de este archivo

soporta extensiones
se puede incluir que no se suba directorios



### BUENAS PRACTICAS

1. ¿Cada cuanto debo hacer un commit?

* commits atómicos
    * hacer un cambio cuando se modifica la funcionalidad
    * commits cortos

2. ¿Como escribir un buen mensaje de commit?   
* debe describir lo que se hizo
* no usar punto final ni puntos suspensivos
* con verbos imperativos
    * add
    * fix
    * change
    * remove
3. ¿Tamaño del commit?

Usa máximo 50 caracteristicas
Directo y consiso



4. Usar un prefijo

feat: feature( nueva característica)
fix: (arreglar un bug)
perf:(cambios que mejorar el rendimiento)
build:(cambios en el sistema de build)
ci:(cambios en la integración continua)
    * deployear algo 
docs: (para cambios en la documentación)
refactor: (refactorización de codigo)
style: (cambios de formato)
test: para test


5. Añade todo el contexto que es necesario 

```
git commit

```
escribiendo este comando se abrira el editor de texto
```
titulo del commit

- descripcion
- mas descripcion
```
---

### Comandos

para ver el estado actual de todos los archivos 
```
    git status

```

indica si existe modificación de algún archivo, nuevos archivos o archivos 
eliminados.


para restaurar a un estado antiguo 

```

git restore [archivo]

```
**Cuidado**
borra fisicamente los cambios realizados que estan despues del git add

se puede recuperar los archivos eliminados antes de subirlo al stage 


para indicar a git que suba al stage los archivos 

```

git add [archivo]

```

en caso de querer volver en este punto se usa

```

git restore --staged [archivo]

```

Quita el archivo del estado del staged, el flag indica que debe buscar
en los archivos en stage


Para confirmar los cambios se usa:

```
git commit -m "descripción del cambio"

```
confirma todos los cambios que se encuentran en stage

**PELIGRO**
Para volver a una confirmación se usa
Se borra todo el progreso de los cambios

```

git reset --soft HEAD~1

```
HEAD indica la ultima confirmación que hicimos
y el ~1 indica 1 confirmación atras



Para ver las confirmaciones en una sola linea cada confirmación
```

git log --oneline

```
---

