# **Comandos GIT**

*Estos comandos fueron ejecutado y probados en git version 2.28.0.windows.1, por tanto si se está utilizando otras versiones se podría tener algunas diferencias.*

## **Configuración inicial (git config)**

### **git config --help**
Muestra documentacion o manual de GIT

    git config --help

### **git config --global**
Asigna una configuración de manera global

    git config --global user.name "Marco Antonio T.A."
    git config --global user.email "matupaarela@outlook.com"

Listar opciones o la cofiguración que tiene git

    git config --list
    git config -l

## **Primer repositorio**

### **git init**
Puede iniciar o crear un repositorio en cualquier carpeta así tenga contenido o no
    
    git init

Los estados de Git:

    Espacio de trabajo -> Área de preparación -> Repositorio

Mostrar estado actual del repostorio

    git status

## **Primeros pasos (git add y commit)**

### **git add**
Agrega archivos al area de preparación, si el nombre del archivos tiene espacios, colocar el nombre dentro de comillas:

    git add readme.md
    git add 'procesa datos.php'

para agregar todo el contenido de una carpta especifica utilizamo el comando

    git add .

Nota: el punto (.) agregar todos los archivos de una carpta por tanto si nos ubicamos en la carpeta raíz del proyecto, agregará todo el proyecto.

### **git commit**
Confirma la entrega del área de preparación al repositorio

    git commit

El comando anterior abrirá un editor VIM en el que podemos agregar una descripción del trabajo realizado. Además de mostrar como comentario los cambios efectuados.

para comenzar a editar dentro del editor presionar la tecla i (latina), nos mostrará un mensaje por debajo

    --INSERT-- o --INSERTAR--

una vez terminado de escribir la descripción del trabajo realizado presionar la tecla esc (escape) para salir del editor y para volver a la consola de git digitar

    :wq

**:wq** proviene de *Write and Quit*

### **git commit -m ""**
Es un atajo al git commit, permite realizar un commit sin necesidad de usar el editor vim.

    git commit -m "mensaje aquí"

### **git log**
Muestra los mensajes o (commits) realizados en el proyecto (repositorio)

    git log

### **git commit -am ""**
Agregar commits de cambios reañizados solo en archivos modificados (los nuevos no serán tomados en cuenta).

    git commit -am "mensaje aquí"

## **Resetear cambios realizados en el espacio de trabajo**

### **git checkout**
Permite resetear cambios en caso de regresar al estado anterior:

    git chekout index.html
    git chekout style.css
    ...

Para resetear varios archivos cambiado a la vez: *-f* permite forzar aplicar los cambios, este caso forzará el reseteo.

    git checkout -f

## **Resetear cambios del área de preparación**

### **git restore --staged [nombre archivo]**
Permite regresar un archivo al espacio de trabajo: es decir cambia de estado (de área de preparación a espacio de trabajo)

    git restore --staged index.html
    git restore --staged style.css

## **Diferencia de cambios en un archivo**

### **git diff [nombre archivo]**
Permite ver la diferecia entre lo que estamos realizado y lo que ya tenemos en el repositorio

    git diff index.html

El comando anterior mostrarás las líneas de código modificadas con el simbolo (+) si se agrego o (-) si se elimino alguna línea.

### **git diff --stat [nombre archivo]**
Permite mostrar los cambios de forma resumida.

    git diff --stat index.html

## **Ramas locales y el historial**

### **git checkout [hash]**
En este caso lo usaremos para nevegar entre commits (viajar en el tiempo)

    git checkout 73328748211792f61fe2fbdf33dd959c4df79e91
    git checkout 7332874

para volver al commit actual (presente)

    git checkout master

### **git log**
Documentacion oficial: https://git-scm.com/docs/git-log

#### **git log --raw**
Proporciona informacion extra al commit realizado

    git log --raw

#### **git log --summary**
Proporciona una infomación resumida

    git log --summary

#### **git log --oneline**
Proporciona informacion de commits de manera super resumida en una solo línea por commit

    git log --oneline

El comando anterior mostrará todos los commits posibles según la pantalla o la consola, si deseamos visualizar solo un numero exacto de commits podemos utilizar la siguiente variación:

    git log --oneline n 5

Donde 5 es el número de commits a mostrar.

#### **git log --pretty=format:"format here"**
Permite imprimir los resultados en un formato personalizado: https://git-scm.com/docs/git-log

     git log --pretty=format:"El autor del commit %h fue %an"

## **Ramas Locales**
La línea de tiempo o rama principal siempre es ***master*** en git podemos trabajar con varias ramas y cada una es independiente (cada rama puede tener sus propios log, commits, etc.) de master y en futuro también pueden llegar a unirse mediante una sincronización.

Creación de una nueva rama a partir de la rama actual (master) y tambie a partir del commit actual:

    git checkout -b development

Donde ` -b ` que proviene de `-branch` (rama) y development es el nombre de la nueva rama.
para ver todas las ramas del repositio podemos ejecutar:

    git branch

Nos devolverá como resultado las ramas creadas en el repositorio y con asterisco por delante en la rama que estemos utilizando.

Después de realizar algunos commits dentro de la rama *development* podemos hacer un `git log` para ver lo commits realizados y obtendremos los commits de todas las ramas, cabe mensionar que si los commits son bastantes giot intentará ocultar algunos commits:

    git log

Para mostrar todos los commits podemos usar el siguiente comando:

    git log --all

Para ver los commits en una solo línea cada una ya sabemos que podemos agregar `--oneline`

    git log --oneline
    git log --oneline --all

Podemos visualizar información más precisa con `--graph` y `--decorate`

    git log --online --all --graph
    git log --online --all --graph --decorate

*Este comando nos servirá para ver la línea de tiempo de cada rama, por tanto: si tenemos una sola rama no encontraremos sentido a usarla.*

## **Cambio de rama**
Para cambiar de rama en versiones inferiores a v2.23 podemos usar: `git checkout [nombre rama]`:

    git checkout master

para versiones superiores podemos usar: `git switch [nombre rama]`

    git switch develpment

***Nota:** Antes de cambiar de una rama a otra se tiene que hacer commit a todos los cambios realizados en la rama que estemos, de otro modo git no nos permitirá el cambio*

hasta este punto los cambios realizados en una rama diferente a master son independientes, por lo tanto desde master no tendremos los cambios realizados en otras ramas.

para sincronizar o fusionar los cambios de development a la rama master, para eso tenemos que estar dentro de la rama master:

    git merge development

**Importante:* tener en cuenta los cambios realizados en el mismo archivo: si la modificación es es en archivos diferentes la gusión se realizará sin problemas.*

Para eliminar una rama debemos estar en la rama que queremos eliminar y ejecutamos el comando:

    git branch -D development

**Importante:* si la rama a eliminar no se a fusionado con la rama actual, los cambios realizados dentro de la rama a eliminar se perderán, a demás debemos de estar en una rama diferente a eliminar*

## **Ramas remotas y trabajo colaborativo**

### **Conflictos al fusionar ramas que modifican el mismo archivo**
El conficto sucede cuando se modifica exactamente las mismas líneas de codigo.

Si sucede un conficto git pedirá que se modifique los cambios o (solucionar los conflictos) de manera manual en cada archivo.

### **Ignorar archivos**
Existen algunos archivos que tienes que ser ignorados, es decir que no se deben almacenar dentro del repositorio, para eso crearemos el archivo `.gitignore`

Contenido de dicho archivo:

    # Este es el listado de archivos a ignorar
    ignorado.txt

    #para ignorar todos los archivos de una carpeta
    ./carpeta

### **Github: trabajo colaborativo**
Para realzar un trabajo colaborativo necesitamos crear un repositorio en github un vez creado el repositorio podemos clonarlo en nuestro pc con el comando:

    git clone https://github.com/matupaarela/GitCommands.git

**Importante:* para ejecutar este comando se tiene que estar posiicionado dentro de nuestra carpeta de proyectos y ahpi abrir la consola de git bash*

Podemos trabajar directamente dentro de este repositorio ya que está en blanco.

#### **git push origin [nombre rama]**
Nos permite subir los commits realizados a la plataforma github

    git push origin master

Al ejecutar este comando es probable que tengamos que ingresar nuestras credenciales de github si es que no tenemos configurado nuestras credenciales en nuestro equipo (PC).

Ahora si ejecutamos un comando `git log` podremos observar que tenemos un commit `origin/master` el cual es la rama de la nube (remoto).

#### **git fetch origin**
Permite obtener la informacion desde el repositorio remoto al local

    git fetch origin

#### **git pull origin [nombre rama]**
Permite jalar informacion desde el repositorio remoto a local desde una rama especifica.

    git pull origin master

### **Enviar ramas locales a remoto**
Para realizar este proceso se tiene que crear una nueva rama en local:
    
    git checkout -b test

Luego ejecutamos en siguiente comando para subir la rama ``test``:

    git push origin test

Con eso tendremos la rama `test` en la nube (remoto)

**Nota:* Estas ramas son útiles en caso de trabajar en equipo, o nosotros mismos desde otro computador.*

### **Eliminar ramas remotas**
Este comando permite eliminar ramas remotas desde local:

    git push --delete origin test

## **Herramientas Gráficas**
Podemos realizar las mismas acciones desde github, vscode, etc.


## **Subir un proyecto a github**
Para subir un proyecto a github tenemos que crear un reposiorio en la pagina de git y compiar la url(https o ssh) del repositorio creado, luego de tener todos los commits en local tenemos que agregar una url remota a nuestro repositorio local:

    git remote add origin https://github.com/matupaarela/GitCommands.git

Después ejecutamos el comando siguiente, que no permitirá agregar una rama al repositorio en este caso la rama master (origin\master)

    git branch -M master

Finalmente empujamos los cambios (nuestro repositorio local a remoto):

    git push origin master

Hasta este punto hemos conocido los comando básicos de GIT.