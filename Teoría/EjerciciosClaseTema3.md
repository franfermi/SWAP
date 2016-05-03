#Ejercicios Tema 3

##Buscar con qué órdenes de terminal o herramientas gráficas podemos configurar bajo Windows y bajo Linux el enrutamiento del tráfico de un servidor para pasar el tráfico desde una subred a otra.

**-Windows**

Usamos el comando **route** que se encarga de mostrar o modificar la tabla de enrrutamiento y se usa
de la siguiente forma:

>ROUTE [-f] [comando [destino] [MASK mascara de red] [puerto de enlace]

Opciones del comando **route**.

-f Borra de las tablas de enrutamiento todas las entradas de las puertas de enlace. Utilizada conjuntamente con otro comando, las tablas son borradas antes de la ejecución del comando.

-p Vuelve persistente la entrada en la tabla después de reiniciar el equipo.

**"comando"** especifica uno de los cuatro comandos siguientes:

DELETE: borra una ruta.

PRINT: Muestra una ruta.

ADD: Agrega una ruta.

CHANGE: Modifica una ruta existente.

**"destino"** especifica el host.

MASK: Si la clave MASK está presente, el parámetro que sigue es interpretado como el parámetro de la máscara de red.

**"máscara de red"** especifica el valor de máscara de subred asociado con esta ruta. Si no es así, éste toma el valor por defecto de 255.255.255.255.

**"puerta de enlace"** especifica la puerta de enlace.

METRIC: Especifica el coste métrico para el destino.

**-Linux**

Para linux podemos usar también el comando **route**, con distinta sintaxis.

Opciones:

-n	Muestra la tabla de enrutamiento en formato numérico [dirección IP]

-e	Muestra la tabla de enrutamiento en formato hostname

add	Añade una nueva ruta a la tabla de enrutamiento

del	Elimina una ruta de la tabla de enrutamiento

Para las opciones **add** y **del** tenemos estas opciones:

  -net	Indica que el objetivo es una red
  
  -host	Indica que el objetivo es un host
  
  gw	Especifica el puerta de enlace del host o red objetivo
  
  netmask	Usado para especificar la máscara de subred del host o red de destino
  
  dev	Especifica el dispositivo o interfaz donde se enviarán los paquetes
  
  reject	Rechaza los paquetes enviados a una ruta o host particular

Un ejemplo de estos dos últimos sería:

>route add -net 192.168.1.0 netmask 255.255.255.0 gw 192.168.1.1 dev eth0

>route del -net 192.168.1.0 netmask 255.255.255.0 gw 192.168.1.1 dev eth0

##Buscar con qué órdenes de terminal o herramientas gráficas podemos configurar bajo Windows y bajo Linux el filtrado y bloqueo de paquetes.

**-Windows**

Para Windows se puede usar el propio **cortafuegos** (firewall) que posee un filtrado de paquetes, consiste en bloquear selectivamente el tráfico de red.

Los sistemas de filtrado de paquetes enrutan los paquetes entre las máquinas de la red interna y externa, pero, de forma selectiva dependiendo de las políticas que se tengan en el sistema. A este tipo de enrutadores que realizan filtrado de paquetes se les llama "screening router".

Un firewall de filtrado de paquetes trabaja a nivel de paquetes. Estos firewalls son diseñados para controlar el flujo de paquetes basándose en la dirección IP de origen y destino, los puertos de origen y destino e información del tipo del paquete.

**-Linux**

Para Linux utilizamos la herramienta **iptables** que permite crear reglas que analizarán los paquetes de datos que entran, salen o pasan por nuestra máquina, y en función de las condiciones que establezcamos, tomaremos una decisión que normalmente será permitir o denegar que dicho paquete siga su curso.

Ejemplos de filtrado de paquetes en función de:

Tipo de paquete de datos:

-Tipo INPUT: paquetes que llegan a nuestra máquina

-Tipo OUTPUT: paquetes que salen de nuestra máquina

-Tipo FORWARD: paquetes que pasan por nuestra máquina

IP origen de los paquetes (-s = source)

-IP concreta, ej: 10.0.1.3

-Rango de red, ej: 10.0.1.0/8

IP destino de los paquetes (-d = destination)

-IP concreta, ej: 10.0.1.3

-Rango de red, ej: 10.0.1.0/8
