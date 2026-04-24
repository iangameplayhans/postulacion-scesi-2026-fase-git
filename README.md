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


## Clase 3

### Github

¿Qué es github?

Es una plataforma en la nube donde los desarrolladores pueden alojar, gestionar y colaborar en proyectos utilizando git

Git vs Github

* Git
    * Es el sistema de control de versiones de
versiones

* Github
    * Es el servidor donde las versiones se almacenan
    * Github usa git
    * Git != Github

### SSH vs HTTPS

* HTTPS
    * Al clonar un repositorio siempre nos pedira autenticarnos
cada vez
* SSH
    1. Configuramos nuestr PC ssh para comunicarse con github mediante una key.
    2. La key creada se pone en github para que no pida las credenciales.

### Configuración SSH

* En windows abre git bash
* En linux abre la terminal

ejecutamos el siguiente comando

```

ssh-keygen -t ed25519 -C "tuCorreoDeGithub@email.com"

cat ~/.ssh/id_ed25519.pub

/* Copias el resultado del comando

dirigete a github
perfil>setting>SSH y GPG keys

aquí darle click a "New SSH Key"
pegas la key que copiaste
le das un nombre para identificar la pc
click en "add ssh key"
*/

ssh -T git@github.com
/* para verificar la conexión */


```

### Crear un repositorio en github

1. Ve a tu apartado de repositorios
2. Click en "New"
3. Ponle un nombre 
4. Click en "Create Repository"


### Conectar un repositorio local con github

```

git remote add origin git@github.com:TuUser/TuRepo.git

/* remote es la url que apunta al servidor externo, el repositorio en github
origin es el apodo que le da al url*/

git branch -M main

git push -u origin main

/* Minimamente debiste hacer un commit*/

```

### Clonar un repositorio

```
git clone "git@github.com:TuUser/TuRepo.git"

/*Si el repo se hizo con  HTTPS */

git clone "https://github.com/TuUser/TuRepo.git"

/* Comando para cambiar el puntero de github
y no pida autenticación 
Sirve para cambiar la conección remota al cual el repo esta conectado*/

git remote set-url origin "git@github.com:TuUser/TuRepo.git"

/* para ver a que repositorio remoto esta conectado

git remote -v

```

### Cambios

#### Subir cambios

```
git push origin <rama>

```

* git push: Empuja los commits locales
* origin: a donde
* rama: la rama que se subira los cambios


#### Bajar los cambios

```
git pull origin <rama>
```

git pull: Trae los commits del servidor
origin: de que servidor traera los cambios
rama: de que rama se traera los commits
