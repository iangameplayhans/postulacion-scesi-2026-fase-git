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

1. pornavegador
2. ir a git-scm.com o buscar git download
3. buscar comando de instalación
4. ejecutar en terminal

Para verificarque se instalo correctamente

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

1. ¿Como escribir un buen mensaje de commit?

* debe describir lo que se hizo
* no usar punto final ni puntos suspensivos
* con verbos imperativos
  * add
  * fix
  * change
  * remove

1. ¿Tamaño del commit?

Usa máximo 50 caracteristicas
Directo y consiso

1. Usar un prefijo

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

1. Añade todo el contexto que es necesario

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

## Clase 4

### git remote

Este comando permite gestionar las conexiones con los repositorios remotos.

Indica al git local donde consultar y enviar la información.

#### Comandos

Para ver las url donde apunta el repositorio

```
git remote -v
```

Para vincular el repositorio local en la nube

*generalmente el apodo se coloca como origin

```
git remote add <apodo> "url"
```

Para cambiar la url donde apunta el repositorio

```
git remote set-url <apodo> "url"
```

### Multiples SSH

Si se necesita varias llaves ssh para que distintos usuarios trabajen en una pc con github se puede configurar esto

#### Configurar

Generamos la ssh key con otro nombre

```

ssh-keygen -t ed25519 -C "tuOtroCorreoDeGithub@gmail.com" -f ~/.ssh/id_miOtroName

```

```
```

la flag -f pide el nombre de la key

Ahora creammos el archivo config en /.ssh
para que las keys sepan gestionar

colocamos lo siguiente en el archivo config

```txt
#Cuenta Personal
Host github.com
 HostName github.com
 User git
 IdentityFile ~/.ssh/id_ed25519
# Cuenta del otro correo
Host github-namekey
 HostName github.com
 User git
 IdentityFile ~/.ssh/namekey
```

* Host
  * Apodo o alias
  * la terminal lo colocara como git@Apodo
* HostName
  * Dirección real del servidor a conectarse
* User
  * Es el nombre de usuario del sistema remoto
  * En github siempre es git
* IdentityFile
  * Ruta donde esta la key del host específico

Como ultimo para verificar si funciona

 ```
ssh -T git@github-namekey
```

### Configuraciones locales

Estas configuraciones prevalecen para cada repositorio en el que se le configuraciones

los comandos para cambiar el usuario y el email localmente son:

```
git congif user.name "Nuevo name"
git config user.email "tuOtroCorreoDeGithub@gmail.com"

```

Al hacer esto el clonado del repositorio con ssh cambia

```
git clone git@github-namekey:usuario/repo.git
```

### Git Checkout

Este comando permite desplazar el HEAD
(a que commit se esta apuntando ) hacia un punto del historial o a una rama distintos

Se usa para:

* Inspeccionar
* Restaurar
* Experimentar
* Cambiar de una rama a otra

#### Estado "Detached HEAD"

Cuando hacemos el checkout para movernos entre los commits el estado cambia a un estado desacoplado
En este estado:

* Solo eres espectador
* Puedes ver y escribir notas pero no perteneces a ninguna rama
* Si vuelves al commit mas actual sin guardar los cambios en una rama se perderan ya que no habra forma de acceder a estos commits

#### Como ir y volver de un commit

Para ir un commit

```
git checkout <hash_commit_destino>
```

Para volver al ultimo commit de la rama

```
git checkout <rama>
```

Si hiciste alguna modificación
debes de hacer para guardar.

```
git checkout <hash_commit_creado>
git checkout -b rama_nueva
```

#### Buenas prácticas

* No trabajes mucho tiempo en "Detached HEAD"
  * si vas a modificar mas de dos lineas mejor crea una rama nueva
* Limpia tu directorio de trabajo
  * Antes de moverte entre commits asegurate de hacer commit de los cambios actuales, si no no podras viajar
* Usalo para aprender
  * Hacer el checkout en proyectos grandes es la mejor forma de como fue creandose.

## Clase 5

### Ramas

#### ¿Qué son las ramas?

Es una de las principales utilidades
de git para llevar un mejor control
de codigo.

Se trata de una bifurcación del estado
del código para poder trabajar en paralelo

#### Comandos

##### Git Branch

Para listar las ramas que existen en el proyecto se usa:

```git
git branch
```

Para poder crear una rama

```git
git branch <nombreRama>
```

Para eliminar una rama

```git
git branch <nombreRama>
```

```git
git branch -D <nombreRama>
```

##### Git Checkout

Este comando tambien sirve para
moverse entre ramas.
Pero se requiere no tener nada en stage o
untracked/modify

Para cambiar de rama se usa:

```git
git checkout <rama>
```

Si se quiere crear una rama se usa:

```git
git checkout -b <rama>
```

este comando tambien nos movera a esa rama

##### Git Switch vs Git Checkout

Originalmente git checkout tenia varias funcionalidades

Actualmente git switch esta especializado para moverse entre ramas y
asi evitar errores accidentales que ocurririan con checkout

### Gitflow básico

#### ¿Qué es?

Es un flujo de trabajo para manejar
de manera ordenada las ramas y tenerlas
organizadas

#### ¿Cómo funciona?

Se tienen principalmente 2 ramas

* main
  * Esta rama contendra el código
  que ya estara en producción
* develop
  * Esta rama albergara todas
  las nuevas funcionalidades del proyecto
* Ramas de apoyo
  * Son ramas que permitiran identificar
  el motivo de algun cambio o añadido que
  requiera ser una rama

##### Ramas de apoyo

* feature
  * Esta rama se crea para añadir nuevas
  caracteristicas
  * Ejemplo:
    * feature/*
    * feature/caracteristica
    * feature/add-caracteristicas
    * feature/new-caracteristicas
* release
  * En esta rama se preparan las versiones
  a las que se deben de hacer pruebas
  * Se crea en develop y se fucionan a develop o a main
  * Ejemplo:
    * release/*
    * release/v1.0.0
    * release/v2.2.1-beta
* hotfix
  * Aqui tienen los cambios improvisados
  como parches para bugs o problemas
  en producción
  * Esta rama nace en main pero se fuciona con main o develop
  * Ejemplos
    * hotfix/*
    * hotfix/login-error
    * hotfix/fix-database-conection
    * hotfix/security-patch

## Clase 6

* git merge

  * Este comando permite fusionar una rama a la que estas Actualmente
pero hay que usar el flag --no-ff esta
flag evitara que la fusion se haga sin un commit,
y se podra saber de esta forma que se hizo en este punto

* Qué es git fetch

  * Este comando verifica si existen cambios o no en la rama

* gitit pull
  * Este comando trae los cambios del repositorio
  * Generalmente se usa indicando a donde consultar(origin)
  y de que rama

* git push

  * Sirve para subir los cambios hechos en local hacia el repositorio
  * generalmente se indica a donde(origin) y de que rama
  * si es la primera vez subiendo los cambios se usa
  la flag -u para que no pida permisos para crear las ramas

### Flujo de trabajo

Se mencionara el flujo de trabajo sin hacer pull request
que es el preferido para github.

Los comandos a ejecutar son los siguientes

```git
git checkout develop
git fetch
git pull origin develop
git merge --no-ff rama
#Resolver los conflictos si es que existen
git add .
git commit
git branch -D rama
git push origin develop

```
