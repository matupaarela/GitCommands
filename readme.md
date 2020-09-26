# **Comandos GIT**

    Correo: sistemas@procontbusiness.com
    Pass: 5cd?Sb97

## **Configuración inicial (git config)**

### **git config --help**
Nos permite obtener ayuda del comando anterior --help

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

### **git commit -am ""**
Agregar commits de cambios reañizados solo en archivos modificados (los nuevos no serán tomados en cuenta).

    git commit -am "mensaje aquí"

### **git log**
Muestra los mensajes o (commits) realizados en el proyecto (repositorio)

    git log