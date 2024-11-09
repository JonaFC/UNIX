# Práctica 2 Laboratorio UNIX
# Jonathan Bautista Parra

## GParted

Lo primero que hice fue ir al siguiente link: https://gparted.org/livecd.php.

![](Practica2/unix2.1.png)

Di clic en **Downloads** y luego di clic en **Download gparted-live-1.6.0-10-amd64.iso**.

![](Practica2/unix2.2.png)

Me mandó a esta página y procedio la descarga.

![](Practica2/unix2.3.png)

Luego, encendí mi máquina virutal istalada en la práctica 1 sin LVM. Ejecuté los comandos **df -h** y **lsblk**.

![](Practica2/unix2.4.png)

Apagué la máquina y doy clic en **Devices**.

![](Practica2/unix2.5.png)

Me fui a **CD/DVD (IDE)** y seleccioné el iso correspondiente a **gparted**.

![](Practica2/unix2.6.png)

Guardé los cambios e incié la máquina virtual. 

![](Practica2/unix2.7.png)

Presioné **F2** para irme al SETUP.

![](Practica2/unix2.8.png)

Me fui a la opción **Boot** y puse **CD-ROM Drive** como primera opción.

![](Practica2/unix2.13.png)

Confirmé los cambios.

![](Practica2/unix2.14.png)

Una vez iniciado el instalador, seleccioné la primer opción.

![](Practica2/unix2.15.png)

Después, seleccioné **Don't touch keymap**.

![](Practica2/unix2.16.png)

Acepté las opciones por default de la instalación 

![](Practica2/unix2.18.png)

Ya inciado **Gparted** pude ver la información del disco.

![](Practica2/unix2.19.png)

La primera configuración que hice fue a **/dev/sda8**

![](Practica2/unix2.20.png)

La imagen muestra la ventana de "Resize/Move" (Redimensionar/Mover) en GParted para la partición /dev/sda8. En este cuadro de diálogo, se está ajustando el tamaño de la partición y la cantidad de espacio libre antes de ella.

Free space preceding (MiB): Se está configurando 5987 MiB de espacio libre antes de la partición /dev/sda8. Esto implica que la partición se moverá hacia la derecha, dejando espacio no asignado delante de ella.
New size (MiB): El nuevo tamaño de la partición se ha establecido en 7201 MiB. Esto indica que la partición se reducirá de su tamaño original para liberar espacio adicional.
Free space following (MiB): El valor es 0, lo que significa que no se dejará espacio libre después de la partición.

![](Practica2/unix2.21.png)
![](Practica2/unix2.22.png)

La configuración quedó de la siguiente manera: 


![](Practica2/unix2.23.png)

Una vez creado el nuevo espacio, modifiqué las particiones /dev/sda5, /dev/sda6, /dev/sda7 siguiendo los mismos pasos.

![](Practica2/unix2.24.png)
![](Practica2/unix2.25.png)
![](Practica2/unix2.27.png)
![](Practica2/unix2.28.png)
![](Practica2/unix2.30.png)

Luego modifiqué **/dev/sda2**

![](Practica2/unix2.31.png)
![](Practica2/unix2.34.png)


Asigné la cantidad de la barra azul correspondiente a /dev/sda2 al mismo nivel que la barra amarilla correspondiente a /dev/sda5.

![](Practica2/unix2.35.png)

Después de aplicar los cambios, asigné el espacio a /dev/sda1

![](Practica2/unix2.36.png)
![](Practica2/unix2.37.png)
![](Practica2/unix2.38.png)

Al aplicar los cambios, /dev/sda1 implementará el espacio libre al suyo. Pasando de pesar 4.12 GiB, a pesar 9.96 GiB.

![](Practica2/unix2.40.png)

Después de haber aplicado todos los cambios correspondientes, guardé todo dando clic en la palomita verde.

![](Practica2/unix2.41.png)
![](Practica2/unix2.42.png)
![](Practica2/unix2.43.png)

Cerré la ventana de GParted y me salí de la herramienta dando clic en el ícono de Exit. Seleccioné **shutdown**.

![](Practica2/unix2.44.png)
![](Practica2/unix2.45.png)

Volví a configurar los dispositivos en el BOOT.

![](Practica2/unix2.46.png)
![](Practica2/unix2.47.png)

Inicié la máquina y volví a ejecutar los comandos **df -h** y **lsblk**

![](Practica2/unix2.48.png)


## Configuración de discos con LVM (solo para VMs con LVM)

Primero me fui a las configuraciones de la MV Debian con LVM creada en la práctica pasada.

![](Practica2/unix2.49.png)

Expandí el disco a **30GB**.

![](Practica2/unix2.50.png)

Inicié la máquina virtual y ejecuté los comandos **df -h** y **lsblk**.

![](Practica2/unix2.51.png)

Ingresé como **root** e instalé **gparted**.

![](Practica2/unix2.53.png)

Ejecuté **apt update**

![](Practica2/unix2.55.png)

Instalé **e2fsprogs**

![](Practica2/unix2.57.png)

Ejecuté el comando **ls /sys/class/scsi_device/** para listar los dispositivos SCSI disponibles en el sistema.

![](Practica2/unix2.58.png)

Ejecuté el comando **echo 1 > /sys/class/scsi_device/2\\\:0\\\:0\\\:0/device/block/sda/device/rescan**. Esto le indica al sistema operativo que realice un "rescan" del dispositivo SCSI identificado por 32:0:0:0 y específicamente del disco sda. Esto es útil cuando has realizado cambios en la configuración del disco (por ejemplo, agregado espacio adicional a un disco virtual en un entorno como VMware) y quieres que el sistema detecte esos cambios sin reiniciar.


![](Practica2/unix2.59.png)

Ejecuté **/usr/sbin/gparted /dev/sda**.

![](Practica2/unix2.60.png)

Una vez dentro, esjecuté el comando **print** para mostrar la tabla de particiones actual del disco.

![](Practica2/unix2.62.png)

Ejecuté el comando resizepart 2 100% para intentar redimensionar la partición 2 (la extendida) para que ocupe el 100% del espacio disponible en el disco.

![](Practica2/unix2.63.png)

Volví a ejecutar **print** para ver los cambios.

![](Practica2/unix2.64.png)

  Ejecuté el comando **/usr/sbin/lvextend -l +100%FREE /dev/mapper/debian--vg-root** El comando está intentando expandir un volumen lógico (LV). Específicamente, busca aumentar el tamaño del LV denominado /dev/mapper/debian--vg-root hasta ocupar todo el espacio libre (100%FREE) disponible en el grupo de volúmenes (VG).

![](Practica2/unix2.65.png)

Finalmente ejecuto **/usr/sbin/resize2fs /dev/mapper/debian--vg-root**: Este es el comando principal. Se está intentando redimensionar el sistema de archivos ubicado en el dispositivo de bloque /dev/mapper/debian--vg-root. Este dispositivo, como vimos antes, es un volumen lógico (LV) manejado por LVM.

resize2fs 1.47.0 (5-Feb-2023): Esta línea muestra la versión de la herramienta resize2fs que se está utilizando.

The filesystem is already 1056768 (4k) blocks long. Nothing to do!: Este mensaje es el resultado de ejecutar el comando. Indica que el sistema de archivos ya tiene el tamaño máximo posible, por lo que no se realizaron cambios.

![](Practica2/unix2.66.png)

