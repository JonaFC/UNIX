# Laboratorio Práctica 3
# Jonathan Bautista Parra

## Shell de root desde el bootloader

Primero inicié la máquina virtual Debian12 y cuando apareció el GRUB, presioné la tecla *e* para ingresar al menú de edición de las entradas del GRUB.

![](Practica3/unix3.1.png)

Una vez dentro, ingreso **init=/bin/sh** para especificar qué programa debe ejecutarse como proceso de inicialización (PID 1) durante el arranque. 

![](Practica3/unix3.2.png)

Presioné **Ctrl+x**

![](Practica3/unix3.3.png)

Ingresé el comando **mount** para mostrar una lista de todos los sistemas de archivos montados en ese momento.

![](Practica3/unix3.4.png)

Ejecuté el comando **mount -o remount,rw :/** para volver a montar el sistema de archivos raíz / con permisos de lectura y escritura. Después ejecuté el comando **mount**.

![](Practica3/unix3.5.png)

Luego, ejecuté el comando **passwd** para tener una nueva contraseña.

![](Practica3/unix3.6.png)

Reinicié el sistema y abrí el archivo **/etc/grub.d/10_linux** usando **nano** y siendo usuario root.

![](Practica3/unix3.7.png)
![](Practica3/unix3.8.png)

Me fui a la línea 132 y agregué **--unrestricted** antes de la etiqueta ${CLASS} para hacerla accesible sin restricciones.

![](Practica3/unix3.9.png)

Despues de haber guardado los cambios, ejecuté el comando  **pdate-grub**.

![](Practica3/unix3.11.png)

## Protección con Contraseña de GRUB

Ingresé como usuario root. Luego ejecuté el comando **grub-mkpasswd-pbkdf2** para generar una contraseña cifrada para usar en la configuración de GRUB.

![](Practica3/unix3.12.png)

Posteriormente, ingresé al archivo **/etc/grub.d/40_custom** usando nano.

![](Practica3/unix3.14.png)

Agregué el usuario **root** y la contraseña cifrada generada anteriormente. Una vez guardados los cambios, volví a ejecutar **update-grub**.

![](Practica3/unix3.15.png)

Reinicié el sistema para asegurarme que, al momento de que inicie el sistema, será de forma normal, pidiendo nuestro usuario y contraseña.

![](Practica3/unix3.16.png)

Finalmente, volví a reiniciar al sistema para intentar ingresar al menú de edición de las entradas del GRUB y verificar que ahora se piden las credenciales configuradas anteriormente.

![](Practica3/unix3.17.png)



