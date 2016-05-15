#Práctica 5. Replicación de bases de datos MySQL

##Crear una BD e insertar datos

Para el desarrollo de la práctica me he creado una base de datos propia y he insertado algunos valores.

Accedemos a MySQL para crear la BD.

>mysql -uroot -p

Mi BD ha sido creada de la siguiente forma.

![imagen](imagenesP5/P5-2.png)

Mi BD se llama Practica5MySQL y mi tabla HabitantesCiudades, compuesta por las columnas Ciudad y Habitantes.

![imagen](imagenesP5/P5-3.png)

##Replicar una BD MySQL con mysqldump

Antes de realizar una copia de seguridad en el archivo .SQL debemos evitar que durante el proceso se acceda a la BD, para ello bloqueamos la tabla creada.

![imagen](imagenesP5/P5-4.png)

Ahora ya podemos usar mysqldump para realizar la copia de seguridad, la orden la realizamos en la maquina 1 (maestro) en mi caso es ubuntu01.

>mysqldump ejemplodb -u root -p > /root/ejemplodb.sql

![imagen](imagenesP5/P5-5.png)

Una vez realizada desbloqueamos la tabla anteriormente bloqueada.

![imagen](imagenesP5/P5-6.png)

Cambiamos a la máquina 2 (esclavo) en mi caso ubuntu02 para copiar el archivo .SQL con los datos guardados del maestro.

>scp root@maquina1:/root/ejemplodb.sql /root/

![imagen](imagenesP5/P5-7.png)

Ahora ya tenemos el archivo en la máquina esclavo pero con texto plano, es decir, con las sentencias necesarias para la creación de nuestra BD, un ejemplo del archivo
es el siguiente:

![imagen](imagenesP5/P5-8.png)

Mysqldump no crea la BD para ello tenemos que crear nuestra BD y asignarle el archivo .SQL.

![imagen](imagenesP5/P5-9.png)

Ahora ya podemos restaurar a la BD creada el contenido del archivo .SQL.

![imagen](imagenesP5/P5-10.png)

Una vez restaurada la BD en la máquina esclavo, comprobamos que el contenido de la BD es el mismo que es de la máquina maestro.

![imagen](imagenesP5/P5-11.png)

##Replicación de BD mediante una configuración maestro-esclavo.

La replicación anterior funciona perfectamente, pero necesitamos de una persona que esté realizando las operaciones anteriores de forma
continuada y manual, para evitar eso se realiza una configuración maestro-esclavo para que dichas operaciones se realicen de forma automática.

Lo primero es comprobar que en ambas máquinas tenemos instalada la misma versión de mysql.

Una vez comprobada la versión procedemos a configurar el archivo de configuración /etc/mysql/my.cnf de la máquina maestro.

La configuración es la siguiente:

![imagen](imagenesP5/P5-12.png)
![imagen](imagenesP5/P5-12.2.png)

Por último después de guardar los cambios, reiniciamos el servicio:

![imagen](imagenesP5/P5-13.png)

Ahora procedemos a configurar la máquina esclavo, con los cambios similares al maestro con la diferencia de server-id=2.

![imagen](imagenesP5/P5-14.png)
![imagen](imagenesP5/P5-15.png)

Guardamos cambios y reiniciamos el servicio.

![imagen](imagenesP5/P5-16.png)

Ahora volvemos a la máquina maestro para crear un usuario y darle permisos de acceso para la replicación.
Por último, obtenemos los datos de la BD que vamos a replicar para posteriormente usarlos en la configuración del esclavo.

![imagen](imagenesP5/P5-17.png)

Volvemos a la máquina esclavo, entramos en mysql y la damos los datos del maestro.
Por último arrancamos el esclavo. 

![imagen](imagenesP5/P5-18.png)

En el maestro, volvemos a activar las tablas que anteriormente bloqueamos.
Y para asegurarnos que funciona correctamente, realizamos los siguiente en mysql:

>mysql> SHOW SLAVE STATUS\G

Y nos fijamos en que “Seconds_Behind_Master” es distinto de “null”.

![imagen](imagenesP5/P5-19.png)

Para acabar, comprobamos que insertando una nueva fila a la tabla en la máquina maestro, automáticamente aparece en la máquina esclavo.

-Maestro

![imagen](imagenesP5/P5-20.png)

-Esclavo

![imagen](imagenesP5/P5-21.png)




