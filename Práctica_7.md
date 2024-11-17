# Práctica 7 Laboratorio UNIX
# Jonathan Bautista Parra
## Fail2ban ClamaV Postfix y Logwatch

Lo primero que hice fue ejecutar **sudo apt install aptitude**.

![](Practica7/unix7.1.png)

Luego, ejecuté **sudo aptitude update** para actualizar los índices de los repositorios de paquetes usando aptitude.

![](Practica7/unix7.2.png)

Luego, Instalé el paquete fail2ban usando el gestor de paquetes aptitude. Para ello ejecuté **sudo aptitude install fail2ban**.

![](Practica7/unix7.4.png)

Cambié el directorio de trabajo al de configuración de Fail2Ban (/etc/fail2ban) y creé una copia de jail.conf con el nombre jail.local. Este archivo (jail.local) es donde se recomienda hacer modificaciones personalizadas de Fail2Ban. Para esto ejecuté **cd /etc/fail2ban** y **sudo cp jail.conf jail.local**.

![](Practica7/unix7.65.png)

Abrí el archivo jail.local en el editor de texto nano con permisos de superusuario para hacer ajustes para hacer las configuraciones pertinentes.

![](Practica7/unix7.5.png)
![](Practica7/unix7.6.png)

Me cambié a mi directorio personal, reinicié el servicio Fail2Ban para aplicar cualquier cambio hecho en el archivo de configuración (jail.local) y verifiqué su estado.
**cd** , **sudo systemctl restart fail2ban** y **sudo systemctl status fail2ban**.

![](Practica7/unix7.7.png)

Consulté el estado del filtro de Fail2Ban para el servicio SSHD, mostrando estadísticas como IPs bloqueadas y tiempo de los bloqueos.

Bloquée una ip, revisé el estado, la desbloqueé y volví a revisar el estado.

 Reinicié el servicio Fail2Ban, asegurando que cualquier cambio o ajuste adicional se haya aplicado correctamente.

![](Practica7/unix7.10.png)

## ClamaV

Instalé el antivirus ClamAV y su servicio clamav-daemon **( sudo aptitude install clamav clamav-daemon )**

![](Practica7/unix7.11.png)

Reconfiguré el paquete clamav-daemon aceptando las opciones que traía por defecto. **( sudo dpkg-reconfigure clamav-daemon )**.

![](Practica7/unix7.12.png)
![](Practica7/unix7.13.png)
![](Practica7/unix7.14.png)
![](Practica7/unix7.15.png)
![](Practica7/unix7.16.png)
![](Practica7/unix7.17.png)
![](Practica7/unix7.18.png)
![](Practica7/unix7.19.png)
![](Practica7/unix7.20.png)
![](Practica7/unix7.21.png)
![](Practica7/unix7.22.png)
![](Practica7/unix7.23.png)
![](Practica7/unix7.24.png)
![](Practica7/unix7.25.png)
![](Practica7/unix7.26.png)
![](Practica7/unix7.27.png)
![](Practica7/unix7.28.png)
![](Practica7/unix7.29.png)
![](Practica7/unix7.30.png)
![](Practica7/unix7.31.png)
![](Practica7/unix7.32.png)
![](Practica7/unix7.33.png)
![](Practica7/unix7.34.png)
![](Practica7/unix7.35.png)

Verifiqué el estado del servicio clamav-freshclam ejecutando **sudo systemctl status clamav-freshclam.service**.

![](Practica7/unix7.36.png)

Ejecuté **sudo systemctl enable clamav-freshclam.service** para activar el servicio clamav-freshclam para que se inicie automáticamente al arrancar el sistema e inicié el servicio clamav-freshclam.

![](Practica7/unix7.38.png)

Creaé el archivo de script clamavscan.sh en el directorio de tareas diarias. Para ello ejecuté **sudo nano /etc/cron.daily/clamavscan.sh**.

![](Practica7/unix7.39.png)

Ejecuté el comando clamscan sobre el directorio /home/

![](Practica7/unix7.40.png)

Ejecuté **sudo chmod +x /etc/cron.daily/clamavscan.sh** para asignar permisos de ejecución al script clamavscan.sh para que el sistema pueda ejecutarlo automáticamente cada día. Luego ejecuté dicho script.

![](Practica7/unix7.42.png)

## Postfix y Logwatch

Ejecuté **sudo aptitude install mailutils postfix logwatch** para instalar algunos paquetes necesarios.

![](Practica7/unix7.43.png)

Después, ejecuté **sudo dpkg-reconfigure postfix** para reconfigurar postfix (usé los valores por defecto).

![](Practica7/unix7.46.png)
![](Practica7/unix7.44.png)
![](Practica7/unix7.45.png)
![](Practica7/unix7.47.png)
![](Practica7/unix7.48.png)
![](Practica7/unix7.49.png)
![](Practica7/unix7.50.png)
![](Practica7/unix7.51.png)
![](Practica7/unix7.52.png)
![](Practica7/unix7.53.png)
![](Practica7/unix7.54.png)

Ejecuté **sudo nano /etc/aliases** para configurar alias de correo, que redirigen correos enviados a cuentas del sistema (por ejemplo, root) a direcciones de correo reales.

![](Practica7/unix7.55.png)

Actualicé la base de datos de alias ejecutando **sudo newaliases**.

![](Practica7/unix7.56.png)

Ejecuté **sudo mkdir /var/cache/logwatch** para crear un directorio de caché para Logwatch.

Luego, ejecuté **sudo cp /usr/share/logwatch/default.conf/logwatch.conf /etc/logwatch/conf/** para copiar el archivo de configuración principal de Logwatch (logwatch.conf) al directorio de configuración en /etc/logwatch.

![](Practica7/unix7.57.png)

Ejecuté **sudo nano /etc/logwatch/conf/logwatch.conf** para abrir el archivo logwatch.conf y ajustar las siguientes configuraciones.

![](Practica7/unix7.58.png)

Ejecuté Logwatch manualmente para generar un informe de baja profundidad (--detail Low) sobre la actividad de hoy (--range today).

![](Practica7/unix7.59.png)

con **sudo cat /var/mail/root | head -n 30** mostré las primeras 30 líneas del contenido del buzón de correo de root.

![](Practica7/unix7.60.png)

Abrí el archivo de tareas diarias 00logwatch con **sudo nano /etc/cron.daily/00logwatch**. 

![](Practica7/unix7.61.png)

Para las tareas semanales, copié el archivo entrior a **/etc/cron.weekly/00logwatch** con **sudo cp /etc/cron.daily/00logwatch /etc/cron.weekly/00logwatch**.

![](Practica7/unix7.62.png)

Finalmente, en el archivo **/etc/logwatch/conf/logwatch.conf** cambié el rango para hacerlo semanal. Para ello, a la variable **Range** le asigné el valor **between -7 days and -1 days**.

![](Practica7/unix7.64.png)
![](Practica7/unix7.63.png)











