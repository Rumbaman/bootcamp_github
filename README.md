# Clase 15 - GIT Intro

## 01. Configuración Inicial
Comando:
```sh
git config --global user.name "Kyu Min Chung"
git config --global user.email "maxcase@outlook.com"
```
* user.name: Nombre con el que se va a guardar cada cambio.
* user.email: Email con el que se va a guardar cada cambio.

## 02. Verificar Configuración
Comando:
```sh
git config --global --get-regexp user
```
Output:
```sh
user.name  Kyu Min Chung
user.email maxcase@outlook.com
```

## 03. Crear Un Repositorio (Inicializar un repo)
Comando:
```sh
git init
```

Output:
```sh
Initialized empty Git repository in /home/kmc/Documents/Education/03-IT/01-Educacion_IT/05-Full_Stack_Bootcamp/Clase_15/Git_Intro/.git/
```

* Crea un directorio OCULTO en el directorio de trabajo.
* Si se va a copiar el directorio, es importante verificar que también se haya copiado el directorio oculto de GIT. De lo contrario, se pierde el repositorio.


## 04. Areas Del Repositorio De GIT
3 Areas:

* Working Directory (WD): Directorio de trabajo, donde se van agregando o quitando los archivos, durante el desarrollo.

* Staging Area (SA): Area de control de cambios.
    Area temporal o intermedia, cuando decidí que voy a guardar los cambios de ese momento.

* Local Repo (LR): Donde voy a tener todas las versiones o "fotos" que vaya sacando.

## 05. Estado De Los Archivos
3 Estados:

* Untracked: Archivos que están en el WD, aunque GIT no los está dando siguimiento y desconoce su contenido.

* Unmodified: Archivos que están en el WD y que GIT les está dando seguimiento.
    Los archivos no fueron modificados.

* Modified: Archivos que están en el repositorio, y GIT les está dando seguimiento, aunque difieren con respecto de lo que están en el WD.

* Staged: Archivos que están en el área temporal/intermedia.

## 06. Conocer El Estado Actual De Los Archivos
Comando:
```sh
git status
```
Output:
* Ejemplo 1:
```sh
On branch main

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        README.md
        css/
        index.html

nothing added to commit but untracked files present (use "git add" to track)
```

* Ejemplo 2:
```sh
On branch main

No commits yet

Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   index.html

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        README.md
        css/
```

* Ejemplo 3:
```sh
On branch main
Untracked files:
  (use "git add <file>..." to include in what will be committed)
        README.md
        css/

nothing added to commit but untracked files present (use "git add" to track)
```

 ## 07. Comandos De GIT
 1. Comando ADD:
```sh
git add <nombre_del_archivo>
 ```
Output:
No hay mensaje.
 
 *  Agrega un archivo al área de Staging.

2. Comando COMMIT:
```sh
git commit -m "Mensaje"
 ```
-m: Mensaje de lo que se está commiteando.

Output:
```sh
[main (root-commit) c036803] Agrego index.html
 1 file changed, 15 insertions(+)
 create mode 100644 index.html
```

* Mueve un archivo del área de Staging al Local Repo.

3. Comando LOG:
* Versión extendida:
```sh
git log
 ```
Output:
```sh
commit c03680317b1346044bd0cd399f4f4eea8871748f (HEAD -> main)
Author: Kyu Min Chung <maxcase@outlook.com>
Date:   Thu May 4 20:31:47 2023 -0300

    Agrego index.html
```

* Versión resumida:
```sh
git log --oneline
```
Output:
```sh
c036803 (HEAD -> main) Agrego index.html
```

* Muestra las versiones almacenadas en el Local Repo.
