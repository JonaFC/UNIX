# Práctica 1 Laboratorio UNIX
# Jonathan Bautista Parra

## Instalar VMware
El vmware ya lo tenía instalado, por lo que no hubo necesidad de hacer la instalación. 

## Instalación de Debian sin LVM y particiones ad-hoc

Lo primero que hice fue ir a la página oficial de Debian
![](Practica1/unix1.1.png)

Di clic en descargar para descargar el iso. Una vez descargado el .iso, abrí el VMWare, me fui a **File** y luego a **New Virtual Machine**

![](Practica1/unix1.2.png)

Di clic en next

![](Practica1/unix1.3.png)

Seleccioné la opción **Installer disc image file(iso)** y busqué el iso de debian que descargué. Di clic en next.

![](Practica1/unix1.4.png)

Seleccióne el sistema operativo **Linux** y la verisón más reciente de Debian que aparecía en VMWare. Di clic en next.

![](Practica1/unix1.5.png)

Le asigné el nombre de **Debian12**. Di clic en next.

![](Practica1/unix1.6.png)

Le asigné un espacio de disco de 20GB y seleccioné la opción **Split virtual disk in multiple files**. Di clic en next.

![](Practica1/unix1.7.png)

Di clic en finish.

![](Practica1/unix1.8.png)

Una vez lista la máquina, di clic en **Power on this virtual machine**

![](Practica1/unix1.9.png)

Una vez iniciado el instalador, seleccioné la opción de **installar**.

![](Practica1/unix1.10.png)

Seleccioné el idioma inglés.

![](Practica1/unix1.11.png)

Seleccioné la opción **other**

![](Practica1/unix1.12.png)

Seleccioné la opción **México**

![](Practica1/unix1.14.png)

Seleccioné **United States** para el idioma

![](Practica1/unix1.15.png)

Seleccioné **American English** como Keymap

![](Practica1/unix1.16.png)

Le asigné el nombre de **debian** al host y seleccioné la opción **Continue**.

![](Practica1/unix1.18.png)

Dejé vació el campo de **Domain name** y seleccioné **Continue**.

![](Practica1/unix1.19.png)

Ingresé y verifiqué la contraseña para el usuario **root**. Seleccioné **Continue** en ambos casos.

![](Practica1/unix1.20.png)
![](Practica1/unix1.21.png)

Hice las configuraciones pertinentes para la creación de usuario no root. 

![](Practica1/unix1.23.png)
![](Practica1/unix1.24.png)
![](Practica1/unix1.25.png)
![](Practica1/unix1.26.png)

Seleccioné la zona horaria **central**

![](Practica1/unix1.27.png)

Seleccioné el método de partición **Guided - use entire disk**

![](Practica1/unix1.28.png)

Seleccioné la única opción disponible.

![](Practica1/unix1.29.png)

Como esquema de partición seleccioné **separate /home, /var, and /etc partitions**.

![](Practica1/unix1.30.png)

Escribí los cambios en el disco

![](Practica1/unix1.31.png)
![](Practica1/unix1.32.png)

Puse que no quería escanear otros medios de instalación

![](Practica1/unix1.34.png)

**Relalicé las configuaciones para el manejador de paquetes.**

![](Practica1/unix1.35.png)
![](Practica1/unix1.36.png)
![](Practica1/unix1.37.png)
![](Practica1/unix1.38.png)

Seleccioné el software para web server, ssh y utilerias del sistema estándar

![](Practica1/unix1.39.png)

Realicé las configuraciónes del grub-pc

![](Practica1/unix1.40.png)
![](Practica1/unix1.41.png)

Finalicé la instalación

![](Practica1/unix1.42.png)

Comprobé que el sistema se instaló correctamente iniciando sesión con el usuario creado.

![](Practica1/unix1.43.png)

## Instalar Linux con LVM y particiones ad-hoc
Le asigné el nombre de **Debian12LVM**

![](Practica1/unix1.44.png)

Seguí casi los mismos pasos hasta antes de las configuraciones de partición.

Para el método de partición seleccioné **Guided - use entire disk and set up LVM**

![](Practica1/unix1.45.png)

Realicé las siguientes configuraciónes para la partición del disco

![](Practica1/unix1.46.png)
![](Practica1/unix1.47.png)
![](Practica1/unix1.48.png)
![](Practica1/unix1.49.png)
![](Practica1/unix1.50.png)

Para las configuraciones del **package manager** hice lo siguiente: 

![](Practica1/unix1.51.png)
![](Practica1/unix1.52.png)
![](Practica1/unix1.53.png)
![](Practica1/unix1.54.png)
![](Practica1/unix1.55.png)

Seleccioné ssh y utilidades estándar de sistema.

![](Practica1/unix1.57.png)

Para el **grub-pc** elegí las siguientes opciones:

![](Practica1/unix1.58.png)
![](Practica1/unix1.59.png)

Finalicé la instalación y comprobé que se haya instalado correctamente iniciando sesión con el usuario creado.

![](Practica1/unix1.60.png)
![](Practica1/unix1.61.png)
