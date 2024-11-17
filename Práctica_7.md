# Práctica 7 Laboratorio UNIX
# Jonathan Bautista Parra
## Fail2ban ClamaV Postfix y Logwatch

Lo primero que hice fue ejecutar **sudo apt install aptitude**.

![](Practica7/unix7.1.png)

Luego, ejecuté **sudo aptitude update** para actualizar los índices de los repositorios de paquetes usando aptitude.

![](Practica7/unix7.2.png)

Luego, Instalé el paquete fail2ban usando el gestor de paquetes aptitude.

![](Practica7/unix7.4.png)

Cambié el directorio de trabajo al de configuración de Fail2Ban (/etc/fail2ban) y creé una copia de jail.conf con el nombre jail.local. Este archivo (jail.local) es donde se recomienda hacer modificaciones personalizadas de Fail2Ban.

![](Practica7/unix7.65.png)

Abrí el archivo jail.local en el editor de texto nano con permisos de superusuario para hacer ajustes para hacer las configuraciones pertinentes.

![](Practica7/unix7.5.png)
![](Practica7/unix7.6.png)

Me cambié a mi directorio personal, reinicié el servicio Fail2Ban para aplicar cualquier cambio hecho en el archivo de configuración (jail.local) y verifiqué su estado.

![](Practica7/unix7.7.png)

Consulté el estado del filtro de Fail2Ban para el servicio SSHD, mostrando estadísticas como IPs bloqueadas y tiempo de los bloqueos.

Bloquée una ip, revisé el estado, la desbloqueé y volví a revisar el estado.

 Reinicié el servicio Fail2Ban, asegurando que cualquier cambio o ajuste adicional se haya aplicado correctamente.

![](Practica7/unix7.10.png)

## ClamaV

Instalé el antivirus ClamAV y su servicio clamav-daemon

![](Practica7/unix7.11.png)

Reconfiguré el paquete clamav-daemon aceptando las opciones que traía por defecto.

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





