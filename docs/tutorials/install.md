# Tutorial de Instalación de Material

El objetivo de este tutorial es dejar preparado el material que necesitarán para los laboratorios y proyectos.

## La mejor opción: Máquina virtual

Descarguen la siguiente máquina virtual y ábranla con VMware. Recuerde que usando [VMware Player](https://www.vmware.com/products/workstation-player.html) (gratuito, sin necesidad de licencia) puede abrir y utilizar máquinas virtuales ya hechas.

[Descargar máquina virtual desde Google Drive](https://drive.google.com/file/d/1r9uVabP9MC7fflk8q76j2ThJIw2U7ZhX/view?usp=sharing)

### Credenciales

- **Usuario**: student
- **Password**: student

La máquina virtual ya trae todo lo necesario para el semestre.

## Instalación Nativa

Para trabajar nativo necesitarán Ubuntu 16 o 18 en inglés, se recomienda 18. En Ubuntu 20 no podrán utilizar Jupiter.

Si su Ubuntu no se encuentra en inglés, tendra problemas en el lab 2 (cgdb). Puede cambiar su idioma, o buscar la solución al problema en Google.

Si todavía no tiene Ubuntu instalado aquí hay un [tutorial para dual boot](https://www.youtube.com/watch?v=h9cPABYSJSI). Ponga mucha atención, sea muy cuidadoso y sobre todo haga un backup de su información importante.

Wow... parece que son bastantes instrucciones, ¡Sería más fácil usar la máquina virtual!

### Instalar git

    sudo apt update
    sudo apt install git

### Instalar Java

    sudo apt update
    sudo apt install default-jdk

### Instalar Python 3

    sudo apt update
    sudo apt install software-properties-common
    sudo add-apt-repository ppa:deadsnakes/ppa
    sudo apt update
    sudo apt install python3.7

### Instalar pip

    sudo apt update
    sudo apt install python3-pip

Las versiones recientes de Python suelen incluir todo lo que necesitamos (en la maquina virtual ya revisamos y esta todo lo que necesita! en serio, use la máquina virtual!), verifiquémoslo abriendo la terminal de Python con el comando `python3`, luego en la terminal escribiremos los siguientes comandos

    import os
    import sys
    import requests
    import zipfile

Si ninguno nos dio problema, Python esta listo; si alguno fallo, lo instalaremos con pip

    pip3 install nombreDelPaqueteQueDioError

### cURL

Finalmente instalamos curl

    sudo apt update
    sudo apt install curl

### CGDB

Y terminamos instalando cgdb

    sudo apt update
    sudo apt install cgdb

Casi listo! Cuando lleguemos al lab 3 y al lab 5 alli le aparecerán las instrucciones para instalar el software faltante.

## Mi computadora no es muy potente, ¿Qué puedo hacer?

Puede probar con algun IDE en línea como [repl.it](https://repl.it/). Aquí podrá trabajar un poco de C y entregar su lab 0 y lab 1, pero al llegar al lab 2 comienzan los problemas. Estamos tratando de buscar herramientas para trabajar en línea, pero haga todo lo posible por trabajar ya sea en máquina virtual o en Ubuntu nativo.

## Soy demasiado fanático de Windows 10, ¿hay alguna opción para mí?

Puede [instalar WSL](https://docs.microsoft.com/en-us/windows/wsl/install-win10#manual-installation-steps) en su máquina. Luego de ese montón de pasos, tendrá que instalar todo el material de arriba. No haga esto, mejor use la máquina virtual.

Esta es una opción que no aconsejamos para nada. Si esta en Windows, no le podremos ayudar con sus problemas, solo le sugeriremos que... ¡adivinó! use la máquina virtual.
