# Práctica 5 Laboratorio UNIX
# Jonathan Bautista Parra
## Actualizar el Kernel de linux

Lo primero que hice fue instalar las dependencias necesarias. Para ello ejecuté **sudo apt update** y **sudo apt install build-essential libncurses-dev bison flex libssl-dev libelf-dev bc dwarves -y**

![](Practica5/unix5.21.png)
![](Practica5/unix5.20.png)

Después, creé una carpeta para guardar el kernel. Descargué la versión **6.11.3** usando **wget** y lo descomprimí usando **tar**.

![](Practica5/unix5.19.png)
![](Practica5/unix5.18.png)
![](Practica5/unix5.17.png)

Me fui a la carpeta generada al descomprimir el archivo.

![](Practica5/unix5.16.png)

Para la configuración del kernel, primero copie el archivo de configuración **/boot/config-$(uname -r)** a la carpeta y le asigné el nombre de **.config**.
Esto para simplificar el proceso de compilación, ya que es el archivo de configuración del kernel actual.

![](Practica5/unix5.11.png)


Ejecuté **make menuconfig** para la configuración del nuevo kernel.

![](Practica5/unix5.21.png)
![](Practica5/unix5.12.png)
![](Practica5/unix5.13.png)
![](Practica5/unix5.14.png)


Cargué y guardé los cambios.

![](Practica5/unix5.15.png)
![](Practica5/unix5.8.png)
![](Practica5/unix5.7.png)

Compilé el kernel utilizando todos los núcleos de CPU disponibles usando el comando **make -j$(nproc)**

![](Practica5/unix5.6.png)


Una vez compilado el kernel sin errores,ejecuté **sudo make modules_install** para instalar los módulos seleccionados en la configuración para  usar como módulos extra por el kernel. 

![](Practica5/unix5.5.png)

Instalé el kernel usando el comando **sudo make install**

![](Practica5/unix5.4.png)

Actualicé el cargador de arranque y reinicié la máquina virtual. Para ello ejecuté **sudo update-brub** y **sudo reboot**-

![](Practica5/unix5.3.png)
![](Practica5/unix5.2.png)

Finalmente, ejecuté **uname -r** para mostrar la neuva versión del kernel.

![](Practica5/unix5.1.png)
