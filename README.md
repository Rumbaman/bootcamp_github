# Clase 17 - GIT Intro (Continuación)

## 01. Configuración Inicial
* Comando:
```sh
git config --global user.name "Kyu Min Chung"
git config --global user.email "maxcase@outlook.com"
```
* user.name: Nombre con el que se va a guardar cada cambio.
* user.email: Email con el que se va a guardar cada cambio.

## 02. Verificar Configuración
* Comando:
```sh
git config --global --get-regexp user
```
* Output:
```sh
user.name  Kyu Min Chung
user.email maxcase@outlook.com
```

## 03. Crear Un Repositorio (Inicializar un repo)
* Comando:
```sh
git init
```

* Output:
```sh
Initialized empty Git repository in /home/kmc/Documents/Education/03-IT/01-Educacion_IT/05-Full_Stack_Bootcamp/Clase_15/Git_Intro/.git/
```

* Crea un directorio OCULTO en el directorio de trabajo.
* Si se va a copiar el directorio, es importante verificar que también se haya copiado el directorio oculto de GIT. De lo contrario, se pierde el repositorio.


## 04. Areas Del Repositorio De GIT
### 3 Areas:

* Working Directory (WD): Directorio de trabajo, donde se van agregando o quitando los archivos, durante el desarrollo.

* Staging Area (SA): Area de control de cambios.
    Area temporal o intermedia, cuando decidí que voy a guardar los cambios de ese momento.

* Local Repo (LR): Donde voy a tener todas las versiones o "fotos" que vaya sacando.

## 05. Estado De Los Archivos
### 3 Estados:

* Untracked: Archivos que están en el WD, aunque GIT no los está dando siguimiento y desconoce su contenido.

* Unmodified: Archivos que están en el WD y que GIT les está dando seguimiento.
    Los archivos no fueron modificados.

* Modified: Archivos que están en el repositorio, y GIT les está dando seguimiento, aunque difieren con respecto de lo que están en el WD.

* Staged: Archivos que están en el área temporal/intermedia.

## 06. Conocer El Estado Actual De Los Archivos
* Comando:
```sh
git status
```
* Output:
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

* Ejemplo 4:
```sh
On branch main
nothing to commit, working tree clean
```

 ## 07. Comandos De GIT
 1. Comando ADD:
 * Agrega un archivo al área de Staging.
 * Agregar un sólo archivo:
```sh
git add <nombre_del_archivo>
 ```

* Agregar más de un archivo:
 ```sh
git add README.md css/estilos.css
 ```

 * Agregar cambios de un sólo archivo, que ya está en Staging:
 ```sh
git add .
 ```
Output:
```sh
No hay mensaje.
```

2. Comando COMMIT:
* Mueve un archivo del área de Staging al Local Repo.
```sh
git commit -m "Mensaje"
 ```
-m: Mensaje de lo que se está commiteando.

* Output:
```sh
[main (root-commit) c036803] Agrego index.html
 1 file changed, 15 insertions(+)
 create mode 100644 index.html
```

* Una vez que el/los archivos ya están en el repositorio, puedo usar "-am". Con esto, hago un "add" y un "commit" a la vez.
```sh
git commit -am "Subo cambios xxxx."

[main 1a179a5] Agrego comentario del '-am' del commit, en el README.md.
 1 file changed, 6 insertions(+), 1 deletion(-)
```

3. Comando LOG:
* Versión extendida:
```sh
git log
 ```
* Output:
```sh
commit c03680317b1346044bd0cd399f4f4eea8871748f (HEAD -> main)
Author: Kyu Min Chung <maxcase@outlook.com>
Date:   Thu May 4 20:31:47 2023 -0300

    Agrego index.html
```
```sh
commit a8e9ae47d97dd996b0a75f9bbbef216ba89efc76 (HEAD -> main)
Author: Kyu Min Chung <maxcase@outlook.com>
Date:   Thu May 4 21:38:20 2023 -0300

    Agrego H2 en el HTML, color rojo al H2 en el CSS, y notas en el README.md.

commit 0bc3cdc24faf4fe46f92f454443c1489d5af53c9
Author: Kyu Min Chung <maxcase@outlook.com>
Date:   Thu May 4 21:30:50 2023 -0300

    Agrego estilos.css, con un color de fondo para el body.

commit 0d559ece3690e13ef462dd9cf1df30d84c77d806
Author: Kyu Min Chung <maxcase@outlook.com>
Date:   Thu May 4 21:17:11 2023 -0300

    Agrego cambios al README.md

commit d20b5f293b723e2563ffc75a1ca04749d385b6f6
Author: Kyu Min Chung <maxcase@outlook.com>
:
```
* Versión resumida:
```sh
git log --oneline
```
Output:
```sh
c036803 (HEAD -> main) Agrego index.html
```
```sh
a8e9ae4 (HEAD -> main) Agrego H2 en el HTML, color rojo al H2 en el CSS, y notas en el README.md.
0bc3cdc Agrego estilos.css, con un color de fondo para el body.
0d559ec Agrego cambios al README.md
d20b5f2 Agrego README.me y CSS.
c036803 Agrego index.html
```


* Muestra las versiones almacenadas en el Local Repo.

4. Comando DIFF:
* Muestra los cambios hechos entre el WD y el LP.
```sh
git diff
```

* Output:
```sh
diff --git a/css/estilos.css b/css/estilos.css
index e69de29..db7ed19 100644
--- a/css/estilos.css
+++ b/css/estilos.css
@@ -0,0 +1,3 @@
+body {
+    background-color: blueviolet;
+}
\ No newline at end of file
```

```sh
diff --git a/css/estilos.css b/css/estilos.css
index 466d7ae..1efd8d0 100644
--- a/css/estilos.css
+++ b/css/estilos.css
@@ -1,3 +1,7 @@
 body {
     background-color: aquamarine;
+}
+
+h2 {
+    color: red;
 }
\ No newline at end of file
diff --git a/index.html b/index.html
index 3c077fe..5acbcef 100644
--- a/index.html
+++ b/index.html
@@ -11,5 +11,7 @@
     <h1>GIT Intro</h1>
 
:
```

5. Comando RESTORE
* Vuelve atrás el último cambio del Working Directory.
```sh
git restore <nombre_archivo>
```

* Output:
```sh
No hay mensaje.
```
* Vuelve atrás el último cambio del área de Staging.
```sh
git restore --staged <nombre_archivo>
```
* Output:
```sh
No hay mensaje.
```

6. Comando HELP
* Muestra en el navegador la ayuda del comando.
* El archivo de ayuda es local.
* Formato para la ayuda: git <comando> --help

```sh
git commit --help
```


7. Comando AMEND
* Reemplaza el último COMMIT
```sh
git log

commit b1ce3327b383cfe1bc6537176277903094a9b474 (HEAD -> main)
Author: Kyu Min Chung <maxcase@outlook.com>
Date:   Thu May 11 19:34:23 2023 -0300

    Primer commit

/* Primero hay que agregar todos los cambios al área STAGE  */
git .add

On branch main
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   index.html


/* Reemplaza el último COMMIT */
git commit --ammend -m "Primer commit corregido"

d -m "Primer commit corregido"
[main 8dddf18] Primer commit corregido
 Date: Thu May 11 19:34:23 2023 -0300
 2 files changed, 25 insertions(+)
 create mode 100644 css/estilos.css
 create mode 100644 index.html

git log
/* Cambió el hash */
commit 8dddf181dcdb5ec75892b3b41bc7dcfb5e4858c6 (HEAD -> main)
Author: Kyu Min Chung <maxcase@outlook.com>
Date:   Thu May 11 19:34:23 2023 -0300

    Primer commit corregido
```


## 08. .gitignore (GIT IGNORE)
* Sirve para que GIT "ignore" (no le va a dar seguimiento) directorios y archivos, que no deseo que sean parte del repositorio.
* Normalmente, va en la raíz del proyecto.
* Se escribe el nombre del archivo y/o la ruta del directorio.
* Ej: logs/error.log | temp/temp.txt

* Crear el archivo .gitignore desde la consola
```sh
touch .gitignore
```

## 09. Vincular al repositorio en GitHub
01. Loguearse a GitHub
02. En GitHub, crear un repositorio, con el botón "New" o desde "New repository" desde el menú desplegable, que se abre en el botón "+", a la izquierda de ícono del perfil.
03. Dejar el resto de las opciones como está predeterminado.
04. Click en "Create Repository".
05. Para agregar el repositorio remoto al repo local: copiar y pegar en la consola
```sh
git remote add origin https://github.com/Rumbaman/bootcamp_github.git
```
06. Si no muestra ningún mensaje, es porque todo salió bien.
07. Para ver si tengo un repositorio remoto:
```sh
git remote -v /* -v: verbose */
```
08. Subir el local repo al repositorio remoto:
* En caso de que tuviera "master" en vez de "main", cambiar "main" por "master":
```sh
/* Si se va a pushear una rama, reemplazar el 'main' por el nombre de la rama. */
git push -u origin main

git status

On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean

git log --oneline

ce045d8 (HEAD -> main, origin/main) Agrego notas sobre Ramas en README.md.
f4cbea8 Agrego notas sobre vincular el repo remoto al repo local, y commitear al repo remoto.
fc740da Agrego temp.txt a .gitignore y anotaciones sobre Git Ignore en README.md
9abf823 Agrego cambios a README.md
ef92987 Agrego a .gitignore logs/error.log y cambios en README.md
b1be857 Agrego .gitignore + modificaciones a README.md e index.html
4769e53 Agregué ejemplo adicional de STATUS.
d913236 Agregue H3, color al H3 en el CSS, y notas de DIFF y RESTORE en el README.md.
a8e9ae4 Agrego H2 en el HTML, color rojo al H2 en el CSS, y notas en el README.md.
0bc3cdc Agrego estilos.css, con un color de fondo para el body.
0d559ec Agrego cambios al README.md
d20b5f2 Agrego README.me y CSS.
c036803 Agrego index.html
```

* Una vez que ya se hizo el primer push, para los siguientes, sólo es necesario el "push":
```sh
git push
```

### Si hago "commit", sin hacer un "push":
* El local repo está adelantado en 1 commit, respecto del repo remoto:
```sh
git status

On branch main
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean

git log --oneline

622121f (HEAD -> main) * Agregué comentarios adicionales del push. * Y pruebo funcionalidad para agregar comentarios en varias líneas.
ce045d8 (origin/main) Agrego notas sobre Ramas en README.md.
f4cbea8 Agrego notas sobre vincular el repo remoto al repo local, y commitear al repo remoto.
fc740da Agrego temp.txt a .gitignore y anotaciones sobre Git Ignore en README.md
9abf823 Agrego cambios a README.md
ef92987 Agrego a .gitignore logs/error.log y cambios en README.md
b1be857 Agrego .gitignore + modificaciones a README.md e index.html
4769e53 Agregué ejemplo adicional de STATUS.
d913236 Agregue H3, color al H3 en el CSS, y notas de DIFF y RESTORE en el README.md.
a8e9ae4 Agrego H2 en el HTML, color rojo al H2 en el CSS, y notas en el README.md.
0bc3cdc Agrego estilos.css, con un color de fondo para el body.
0d559ec Agrego cambios al README.md
d20b5f2 Agrego README.me y CSS.
c036803 Agrego index.html
```
* Para igualar, hay que hacer:
```sh
git push

git status

On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean

git log --oneline

622121f (HEAD -> main, origin/main) * Agregué comentarios adicionales del push. * Y pruebo funcionalidad para agregar comentarios en varias líneas.
ce045d8 Agrego notas sobre Ramas en README.md.
f4cbea8 Agrego notas sobre vincular el repo remoto al repo local, y commitear al repo remoto.
fc740da Agrego temp.txt a .gitignore y anotaciones sobre Git Ignore en README.md
9abf823 Agrego cambios a README.md
ef92987 Agrego a .gitignore logs/error.log y cambios en README.md
b1be857 Agrego .gitignore + modificaciones a README.md e index.html
4769e53 Agregué ejemplo adicional de STATUS.
d913236 Agregue H3, color al H3 en el CSS, y notas de DIFF y RESTORE en el README.md.
a8e9ae4 Agrego H2 en el HTML, color rojo al H2 en el CSS, y notas en el README.md.
0bc3cdc Agrego estilos.css, con un color de fondo para el body.
0d559ec Agrego cambios al README.md
d20b5f2 Agrego README.me y CSS.
c036803 Agrego index.html 
```
## 10. Ramas en GitHub
* Es una copia exacta del último commit.
* Sirve para realizar cambios tentativos, o crear nuevas funcionalidades, sin afectar lo hecho hasta el momento.

## 11. Crear una rama
01. Commitear y pushear todos los cambios.
02. Creo una nueva rama:
```sh
git branch <nombre_rama>
```
* No muestra ningún mensaje.
03. Para ver las ramas:
```sh
git branch

* main
  ramas

/* Me lista todas las ramas: a--> Muestra todas las ramas | v--> Verbose, con detalles. */
git branch -av
* main
  ramas
  dev
  pepe
  lola
  /remotes/origin/maria
  /remotes/origin/footer
```

04. Para cambiar de rama:
```sh
git switch ramas

Switched to branch 'ramas'

git branch

  main
* ramas
```

* Si quiero cambiar a la rama anterior:
```sh
git switch -
```

### Cuando hago "commit" en la rama
```sh
git status

On branch ramas
Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        modified:   README.md

git add .

git commit -m "Comment"

[ramas 5401a5c] Agrego notas de Intro A Ramas en README.md.
 1 file changed, 83 insertions(+)

git status

On branch ramas
nothing to commit, working tree clean

git log --oneline
5401a5c (HEAD -> ramas) Agrego notas de Intro A Ramas en README.md.
622121f (origin/main, main) * Agregué comentarios adicionales del push. * Y pruebo funcionalidad para agregar comentarios en varias líneas.
ce045d8 Agrego notas sobre Ramas en README.md.
f4cbea8 Agrego notas sobre vincular el repo remoto al repo local, y commitear al repo remoto.
fc740da Agrego temp.txt a .gitignore y anotaciones sobre Git Ignore en README.md
9abf823 Agrego cambios a README.md
ef92987 Agrego a .gitignore logs/error.log y cambios en README.md
b1be857 Agrego .gitignore + modificaciones a README.md e index.html
4769e53 Agregué ejemplo adicional de STATUS.
d913236 Agregue H3, color al H3 en el CSS, y notas de DIFF y RESTORE en el README.md.
a8e9ae4 Agrego H2 en el HTML, color rojo al H2 en el CSS, y notas en el README.md.
0bc3cdc Agrego estilos.css, con un color de fondo para el body.
0d559ec Agrego cambios al README.md
d20b5f2 Agrego README.me y CSS.
c036803 Agrego index.html
```

## 12. Fusionar una rama
* Tengo que estar en la rama a la que quiero traer los cambios de la otra rama.

```sh
git switch main

git branch
  footer
* main
  navbar


/* Traigo los cambios de "navbar" a "main" */
git merge navbar

Updating 8dddf18..dd8dfdd
Fast-forward
 index.html | 10 ++++++++++
 1 file changed, 10 insertions(+)


/* Traigo los cambios de "footer" a "main" */
git merge footer
Auto-merging index.html
Merge made by the 'ort' strategy.
 css/estilos.css | 5 +++++
 index.html      | 4 ++++
 2 files changed, 9 insertions(+)


git log --oneline

638501a (HEAD -> main) Merge branch 'footer'
fde1dfa (footer) Agrego FOOTER
dd8dfdd (navbar) Agrego HEADER y navbar
8dddf18 Primer commit corregido
```
* Fast-forward: Es lo mejor que puede pasar. Significa que no hay solapamiento de líneas de código.
* --abort: En caso de conflicto, se puede suspender el MERGE.
```sh
git merge --abort
```

## 13. Eliminar una rama
* Se tiene que estar posicionado fuera de la rama que se quiere eliminar.
```sh
git branch

  footer
* main
  navbar

git branch -d footer

Deleted branch footer (was fde1dfa).

* main
  navbar

git branch -d navbar

Deleted branch navbar (was dd8dfdd).

git branch

* main
  navbar
```

## 14. CLONE: Descargar un repositorio
* IMPORTANTE: El directorio debe estar vacío.
```sh
git clone "<URL_Repositorio>" .

Cloning into '.'...
remote: Enumerating objects: 27, done.
remote: Counting objects: 100% (27/27), done.
remote: Compressing objects: 100% (15/15), done.
Receiving objects: 100% (27/27), done.
remote: Total 27 (delta 8), reused 27 (delta 8), pack-reused 0
Resolving deltas: 100% (8/8), done.
```

## 15. Actualizar la META-DATA sin actualizar los datos de mi repo local
```sh
git fetch
```

## 16. Actualizar los datos de una rama
* Debo estar parado en la rama que quiero actualizar.
```sh
git pull origin <nombre_rama>
```