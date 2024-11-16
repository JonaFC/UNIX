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



