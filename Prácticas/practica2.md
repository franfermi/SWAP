#Práctica 2

##Crear un tar con ficheros locales en un equipo remoto

tar czf - directorio | ssh equipodestino 'cat > ~/tar.tgz'

![imagen](imagenesP2/EjecuciónComandoTar.png)

Ahora comprobamos que se ha creado en la máquina principal.

![imagen](imagenesP2/CarpetaRemotaTar.png)

##Instalar la herramienta rsync

rsync -avz -e ssh root@maquina1:/var/www/ /var/www/

![imagen](imagenesP2/CopiaConRsync.png)

Comprobamos que el contenido en /var/www/ de la máquina 1 y la máquina 2 es el mismo.

Máquina 1:

![imagen](imagenesP2/ContenidoWWWUbuntu01.png)

Máquina 2:

![imagen](imagenesP2/ContenidoWWWUbuntu02.png)

##Acceso sin contraseña para ssh

ssh-keygen -t dsa

![imagen](imagenesP2/GenerarClavePublicaUbuntu02.png)

Copiamos la clave pública a la máquina principal y comprobamos que podemos acceder a la máquina principal 
sin necesidad de introducir la contraseña.

![imagen](imagenesP2/sshUbuntu01SinKey.png)

##Programar tareas con crontab

Añadimos la tarea editando el fichero /etc/crontab.

![imagen](imagenesP2/TareasCrontab.png)

Comprobamos las tareas a realizar por el usuario root.

![imagen](imagenesP2/ContenidoCrontabRoot.png)
