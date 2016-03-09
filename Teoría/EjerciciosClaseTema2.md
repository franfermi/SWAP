#Ejercicios Tema 2

##Calcular la disponibilidad del sistema si tenemos dos réplicas de cada elemento (en total 3 elementos en cada subsistema).

            |  Normal  |  Duplicado  |  Triplicado  |
:-----------|:--------:|:-----------:|:------------:|
Web         |85%       |97.75%       |99.66%        |
Application |90%       |99%          |99.9          |
Database    |99.9%     |99.9999%     |99.9999999%   |
DNS         |98%       |99.96%       |99.9992%      |
Firewall    |85%       |97.75%       |99.66%        |
Switch      |99%       |99.99%       |99.9999%      |
Data Center |99.99%    |99.99%       |99.99%        |
ISP         |95%       |99.75%       |99.2035%      |


##Buscar frameworks y librerías para diferentes lenguajes que permitan hacer aplicaciones altamente disponibles con relativa facilidad.

-***Rails***, framework desarrollado en Ruby, también se puede encontrar como Ruby on Rails, que incluye todo lo necesario para crear aplicaciones web respaldadas por BD.

-***JavaServer Faces***, orientado a desarrollos Java.

-***AngularJS***, framework de JavaScript que permite el desarrollo de aplicaciones web en el lado del cliente.

-***ASP.NET***, es un framework de C# para el desarrollo gratuito de sitios webs, aplicaciones y servicios que utilizan HTML, CSS y JavaScript.

-***Django***, es un framework de alto nivel desarrollado en Python, con el objetivo de mejorar el desarrollo de aplicaciones optimizándolas.


##¿Cómo analizar el nivel de carga de cada uno de los subsistemas en el servidor? Buscar herramientas y aprender a usarlas.

 Comando    |  Definición                                                                            |
:-----------|:---------------------------------------------------------------------------------------|
top         |Resumen de la informacion del sistema en tiempo real, así como el listado de tareas.    |
mpstat      |Muestra las actividades del o los procesadores, contando desde 0 para el primer nucleo. |
sar         |Muestra el uso de discos, red y procesos de entrada y salida.                           |
uptime      |Nos muestra la hora actual, el tiempo que el sistema lleva en marcha, nº de usuarios    |       
            |conectados, y la carga promedio del sistema para los últimos 1, 5 y 15 minutos.         |
free        |Muestra la infromación relativa al uso de la memoria.                                   |
vmstat      |Proporciona información sobre el uso de la memoria virtual por las hebras del núcleo,   |
            |el disco y la actividad del procesador.                                                 |
iostat      |Muestra estadísticas sobre la lectura/escritura de los dispositivos.                    |


##Buscar ejemplos de balanceadores software y hardware (productos comerciales).

###Balanceadores software
**HAProxy**, es un software libre que actúa como balanceador de carga (load balancer) ofreciendo alta disponibilidad, balanceo de carga y proxy para comunicaciones TCP y HTTP.

**IPVS**, implementa la capa de transporte de carga balanceadora en el interior del núcleo de Linux. IPVS se ejecuta en un host que actúa como un balanceador de carga en la parte delantera de un grupo de servidores reales, se pueden dirigir las solicitudes de servicios basados en TCP / UDP para los servidores reales, y hace que los servicios de los servidores reales que aparecen como un servicio virtual en una única dirección IP.

###Balanceadores hardware



