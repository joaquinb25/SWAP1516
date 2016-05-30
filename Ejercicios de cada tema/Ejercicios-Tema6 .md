#Ejercicios Tema 6

#Nombre:Joaquin Ballesteros Ortega





##Ejercicio T6.1: Aplicar con iptables una pol�tica de denegar todo el tr�fico en una de las m�quinas de pr�cticas. Comprobar el funcionamiento. Aplicar con iptables una pol�tica de permitir todo el tr�fico en una de las m�quinas de pr�cticas. Comprobar el funcionamiento.

**Para denegar todo el trafico, utilizamos el comando:** 

*iptables -A INPUT -j DROP* El fichero prueba.html ubicado en /var/www no se descarga.

**Para aceptar todo el trafico, utilizamos el comando:**

*iptables -A INPUT -j ACCEPT* El fichero prueba.html ubicado en /var/www se descarga.



##Ejercicio 6.2

###*Comprobar qu� puertos tienen abiertos nuestras m�quinas, su estado, y qu� programa o demonio lo ocupa.*

Con *cat /etc/services* podemos ver el listado con los servicios de red del sistema.

Para comprobar qu� servicios est�n activos y a la escucha en nuestro sistema Linux, utilizaremos netstat
 -a o con la opci�n -ap para mostrar qu� programas est�n asociados a las conexiones activas.



###*Buscar informaci�n acerca de los tipos de ataques m�s comunes en servidores web,
 en qu� consisten, y c�mo se pueden evitar.*

#####**Ataques mas comunes:**

**Ataque Por Injection**:es una t�cnica para modificar una cadena de consulta de base de datos mediante la inyecci�n de c�digo en la consulta.
 El SQLI explota una posible vulnerabilidad donde las consultas se pueden ejecutar con los datos validados.

**DDoS**: es una las formas m�s comunes para congelar el funcionamiento de un sitio web. Estos son los intentos de inundar un sitio con solicitudes externas, por lo que ese sitio no podr�a estar disponible para los usuarios reales. Los ataques de denegaci�n de servicio por lo general se dirigen a puertos espec�ficos, rangos de IP o redes completas, 
pero se pueden dirigir a cualquier dispositivo o servicio conectado.

**Fuerza Bruta**: Estos son b�sicamente intenta �romper� todas las combinaciones posibles de nombre de usuario + contrase�a en una p�gina web. Los ataques de fuerza bruta buscan contrase�as d�biles para ser descifradas y tener acceso de forma facil. 

**Cross Site Scripting**: Los atacantes utilizan Cross-site Scripting (XSS) para inyectar scripts maliciosos en lo que ser�an sitios web inofensivos. Debido a que estos scripts parecen provenir de sitios web de confianza, el navegador de los usuarios finales casi siempre ejecuta la secuencia de comandos, la concesi�n de los piratas inform�ticos el acceso a la
 informaci�n contenida en las cookies o tokens de sesi�n utilizados con ese sitio.




#####**Metodos de defensa:**

	Se debe revisar la configuraci�n de Routers y Firewalls para detener  IPs inv�lidas as� como 
tambi�n el filtrado de protocolos que no sean necesarios. Algunos firewalls y routers proveen la opci�n
 de prevenir inundaciones (floods) en los protocolos TCP/UDP. Adem�s es aconsejable habilitar la opci�n 
de logging (logs) para llevar un control adecuado de las conexiones que existen con dichos routers.


C�mo medida de respuesta es muy importante contar con un plan de respuesta a incidentes. Si ocurre alg�n hecho de este tipo, cada persona dentro de la organizaci�n deber�a saber cu�l es su funci�n espec�fica.

Otras de las alternativas que se deben tener en cuenta es la solicitud ayuda al Proveedor de Servicios de Internet (ISP). Esto puede ayudar a bloquear el tr�fico m�s cercano a su origen sin necesidad de que alcance a la organizaci�n.
En caso de contar con IDS/IPS (intrusi�n-detection/prevention system), estos pueden detectar el mal uso de protocolos v�lidos como posibles vectores de ataque. Se debe tener en cuenta, adem�s, la configuraci�n de estas herramientas.


En el caso de DDos existe el DDoS Kona Site Defender mitiga los ataques DDoS por medio de la absorci�n del tr�fico DDoS 
dirigido al nivel de aplicaci�n, el desv�o de todo el tr�fico DDoS dirigido al nivel de red, como inundaciones SYN o inundaciones UDP, y la autenticaci�n del tr�fico v�lido en el extremo de la red. Esta soluci�n de protecci�n integrada est� "siempre activada" y �nicamente se permite tr�fico en el puerto 80 (HTTP) o el puerto 443 (HTTPS).



*Fuentes:*

http://blog.hostdime.com.co/tipos-de-ataques-mas-comunes-a-sitios-web-y-servidores/
http://www.humanlevel.com/articulos/desarrollo-web/como-evitar-ataques-de-hackers-en-una-pagina-web.html
https://www.akamai.com/es/es/resources/protect-against-ddos-attacks.jsp
http://www.welivesecurity.com/la-es/2012/03/28/consejos-ataque-denegacion-servicio/