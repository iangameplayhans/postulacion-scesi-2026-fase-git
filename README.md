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



