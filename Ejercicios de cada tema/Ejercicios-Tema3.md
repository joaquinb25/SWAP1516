#Ejercicios Tema 3

#Nombre : Joaqu�n Ballesteros Ortega


##Ejercicio T3.1

###Buscar con qu� �rdenes de terminal o herramientas gr�ficas podemos configurar bajo Windows y bajo Linux 
el enrutamiento del tr�fico de un servidor para pasar el tr�fico desde una subred a otra.###

Windows tiene un Servicio de enrutamiento y acceso remoto que se puede agregar al servidor mediante un simple asistente.

En Linux, la configuraci�n de red est� en */etc/network/interfaces*, 
se trata de un archivo en el cual se pueden establecer las configuraciones de red. 
Si lo que queremos es crear una ruta pues se utiliza el comando *route* y a�adirla o borrarla con *add* o *del* respectivamente. 
Si lo que queremos es mantener estas rutas tras reiniciar el servidor, a�adimos la ruta al archivo */etc/network/interfaces mediante la l�nea *up route add -net ...*.

##Ejercicio T3.2

###Buscar con qu� �rdenes de terminal o herramientas gr�ficas podemos configurar bajo Windows y bajo Linux el 
filtrado y bloqueo de paquetes.


En Windows se usa el servicio Enrutamiento y acceso remoto admite el filtrado de paquetes IP, que especifica qu� tipo de tr�fico se permite entrar y salir del enrutador.
La caracter�stica de filtrado de paquetes se basa en excepciones. Puede establecer filtros de paquetes por interfaz y configurarlos para
dejar pasar todo el tr�fico excepto los paquetes prohibidos por filtros o descartar todo el tr�fico excepto los paquetes permitidos por filtros. 

En Linux la principal orden es  iptables permite crear reglas que analizar�n los paquetes de datos que entran,
salen o pasan por nuestra m�quina, y en funci�n de las condiciones que establezcamos, tomaremos una decisi�n que
normalmente ser� permitir o denegar que dicho paquete siga su curso.



###Referencia
http://www.ite.educacion.es/formacion/materiales/85/cd/linux/m6/cortafuegos_iptables.html
https://msdn.microsoft.com/es-es/library/cc736596(v=ws.10).aspx