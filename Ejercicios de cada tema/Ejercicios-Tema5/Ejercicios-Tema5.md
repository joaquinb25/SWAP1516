#EJERCICIOS TEMA 5

##Nombre : Joaquin Ballesteros Ortega

###Ejercicio 5.1: Buscar información sobre cómo calcular el número de conexiones por segundo.

Podemos saber en un momento dado cuantas peticiones esta sirviendo apache ejecutando:

*apache2ctl status |grep request*

###Ejercicio 5.3: Buscar información sobre herramientas para monitorizar las prestaciones de un servidor.

**Vmstat** es un comando que nos permite obtener un detalle general de los procesos, E/S, uso de memoria/swap, estado del sistema y actividad del CPU. Es esencial para entender que esta pasando en tu sistema, detectar cuellos de botella, etc..

Para usarlo, podemos correrlo sin parámetros, y obtendremos algo similar a esto:

![vmstat](https://github.com/joaquinb25/SWAP1516/blob/master/Ejercicios%20de%20cada%20tema/Ejercicios-Tema7/vmstat.jpg)

La primera línea es simple, se divide en seis categorías: procesos, memoria, swap, E/S, sistema y CPU.
La segunda un detalle abierto de cada categoria superior.


**Netstat** muestra  conexiones  de  red,  tablas  de  encaminamiento,estadísticas de interfaces, 
conexiones enmascaradas y mensajes del tipo netlink.


Con top podemos tener una vista dinámica de un sistema en funcionamiento. 
Puede mostrar un resumen y una lista de procesos manejados por el kernel Linux. 
Tiene una limitada interfaz interactiva y una interfaz más amplia para la configuración personal.

###FUENTES

https://storm.malditainternet.com/wp/2011/05/usando-y-entendiendo-vmstat/
http://manpages.ubuntu.com/manpages/precise/es/man8/vmstat.8.html
http://manpages.ubuntu.com/manpages/precise/es/man8/netstat.8.html
