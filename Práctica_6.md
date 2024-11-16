# Práctica 5 Laboratorio UNIX
# Jonathan Bautista Parra
## phpMyAdmin

Lo primero que hice fue ejecutar **apt update** para actualizar la caché del gestor de paquetes.

![](Practica6/unix6.1.png)

Luego, ejecuté **apt install apache2** para intentar instalar apache, aunque ya lo tenía instalado.

![](Practica6/unix6.2.png)

Instalé el servidor de base de datos MariaDB, el cual es un sistema de gestión de bases de datos derivado de MySQL.

![](Practica6/unix6.3.png)

Después, ejecuté **mysql_secure_installation** para configurar la seguridad del servidor MariaDB.

![](Practica6/unix6.4.png)
![](Practica6/unix6.5.png)

Inicé una sesión en la consola de MariaDB para corroborar que se instaló correctamente.

![](Practica6/unix6.7.png)

Ejecuté **apt install php libapache2-mod-php php-mysql** para instalar PHP y las bibliotecas necesarias para que PHP funcione con Apache y MariaDB.

![](Practica6/unix6.8.png)

Ejecuté **nano /etc/apache2/mods-enabled/dir.conf** para abrir  el archivo de configuración de Apache relacionado con los módulos habilitados, específicamente para la directiva de orden de indexación de directorios.
Moví el archivo index.php a la primera posición después de la especificación DirectoryIndex.

![](Practica6/unix6.11.png)
![](Practica6/unix6.10.png)

Guardé los cambios. Luego, recargué la configuración de Apache sin detener el servidor usando **systemctl reload apache2** y mostré el estado de apache ejecutando **systemctl status apache2**.

![](Practica6/unix6.12.png)


## Instalación de phpMyAdmin y paquetes recomendados

Para esta parte, primero instalé las extensiones adicionales de PHP necesarias para el funcionamiento de phpMyAdmin. Para esto ejecuté **apt install php-mbstring php-zip php-gd**.

![](Practica6/unix6.13.png)


Unas instaladas las extensiones, descargué el código fuente de la versión  más reciente de **phpmyadmin.**

![](Practica6/unix6.14.png)

Una vez descargado el código fuente, lo descomprimí usando **tar -xvf phpMyAdmin-5.2.1-all-languages.tar.gz**

![](Practica6/unix6.15.png)

Ejecuté el comando **mv phpMyAdmin-4.9.7-all-languages/ /usr/share/phpmyadmin** para mover el directorio phpMyAdmin-4.9.7-all-languages y todos sus subdirectorios al directorio /usr/share/.

![](Practica6/unix6.17.png)

Ejecué **sudo mkdir -p /var/lib/phpmyadmin/tmp** para crear un directorio temporal para phpMyAdmin. Este directorio es necesario para almacenar archivos temporales que phpMyAdmin pueda necesitar.

![](Practica6/unix6.18.png)

Después ejecuté **chown -R www-data:www-data /var/lib/phpmyadmin** para cambiar el propietario del directorio temporal a www-data, el usuario con el que corre Apache y así garantizar que phpMyAdmin pueda acceder y manipular los archivos en el directorio.

Copié el archivo de configuración de ejemplo de phpMyAdmin a un archivo de configuración real

![](Practica6/unix6.19.png)

Instalé la herramienta pwgen,utilizada para generar contraseñas aleatorias.

![](Practica6/unix6.20.png)

Ejecuté **pwgen -s 32 1** para generar una cadena segura de 32 caracteres para ser utilizada como valor para blowfish_secret.

![](Practica6/unix6.22.png)

