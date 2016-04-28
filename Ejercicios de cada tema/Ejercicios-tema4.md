#Ejercicios Tema 4

#Nombre : Joaqu�n Ballesteros Ortega


##Ejercicio T4.1:
###Buscar informaci�n sobre cu�nto costar�a en la actualidad un mainframe. Comparar precio y potencia entre esa m�quina y una granja web de unas prestaciones similares. 

El ultimo mainframe conocido es el IBM z13, es un chip fabricado por IBM para sus z13 ordenadores centrales. 
Fabricado en GlobalFoundries  planta de fabricaci�n (anteriormente propia planta de IBM). 
IBM ha destacado que es microprocesador m�s r�pido del mundo y es un 10% m�s r�pido que su predecesor, el zEC12 en la computaci�n de un �nico subproceso 
en general, pero significativamente m�s al hacer tareas especializadas. 

El precio es mayor que para una granja web, aunque el gasto en electricidad y el espacio ocupado ser� menor pero es m�s dif�cilmente escalable y un fallo 
en la m�quina nos dejar�a sin poder servir a los clientes.


##Ejercicio T4.2:
###Buscar informaci�n sobre precio y caracter�sticas de balanceadores hardware espec�ficos. Compara las prestaciones que ofrecen unos y otros. 

*Rendimiento frente Costo: Alto Rendimiento de carga virtual del equilibrador*

Al comparar el rendimiento de los equilibradores de carga de alto rendimiento virtuales (5 Gb +) de KEMP, F5 y Citrix, la KEMP VLM- 5000 y 10G ofrece el mismo rendimiento 5/10 Gbps como Big-IP de F5 VE-10G a un costo significativamente menor.


*Rendimiento frente Costo: Alto Rendimiento del equilibrador de carga de hardware*

El equilibrador de carga de alto rendimiento KEMP LoadMaster-8000 proporciona m�s rendimiento por $ 1 que en los 7000s F5 BIG-IP LTM y Citrix MPX y en una fracci�n del costo.


*Rendimiento frente Costo: medio rango de hardware equilibrador de carga*

La comparaci�n de los equilibradores de carga de gama media - aquellos con rendimientos que van desde 3-6Gbps - la KEMP LoadMaster-4000 proporciona cerca del mismo rendimiento y la misma funcionalidad b�sica en comparaci�n con LTM de F5-2x (Mejor Licencia) y Citrix NetScaler MPX-8005 al 1 / 3 el precio y m�s rendimiento por $ 1.


*Rendimiento frente Costo: Categor�a est�ndar virtual del equilibrador de carga*

El KEMP VLM-2000 proporciona un rendimiento similar al de VE-1G / 5G y Citrix NetScaler VPX-1000/3000 F5 BIG-IP LTM durante al menos 1/3 del costo.

*Rendimiento frente Costo: entrada virtual del equilibrador de carga*

Al comparar la KEMP VLM-200 a la F5 BIG-IP LTM VE-200M y Citrix NetScaler VPX 200, el KEMP VLM-200 ofrece el mismo rendimiento como F5 y Citrix en � y � cuarta parte del costo, respectivamente.

Las transacciones SSL equilibrador de carga de hardware.

El KEMP LoadMaster-8000 es compatible con m�s de TPS SSL (transacciones por segundo) que el 4000 (licencia Mejor Edici�n) F5 BIG-IP LTM al 60% del coste y un coste similar por transacci�n SSL como Citrix MPX 8015, pero a un $ 30.000 menor Precio de lista.

Las transacciones de equilibrador de carga SSL virtual

El KEMP VLM-10G soporta SSL TPS 3 veces m�s que el F5 BIG-IP LTM VE-10G a un costo 66% inferior y 4.5x el TPS SSL de Citrix NetScaler VPX-3000 de $ 11.000 menos.


##Ejercicio T4.5:
###Probar las diferentes maneras de redirecci�n HTTP.�Cu�l es adecuada y cu�l no lo es para hacer balanceo de carga global? �Por qu�?

Principalmente hay 2 tipos de redirecciones que debes conocer:

*Redireccionamiento 301*: Se puede definir este tipo de redireccion como �PERMANENTE�. Esto indica que todo contenido de una URL
 antigua se mueva de forma permanente a la URL nueva. De esta manera los buscadores dejar�n de tener en cuenta la antigua URL y 
le traspasar�n �aproximadamente� el 90% de la fuerza SEO a la nueva Web.

*Redireccionamiento 302*: Se puede definir este tipo de redirecci�n como �TEMPORAL�. Esto indica que todo el contenido de una URL 
antigua se mueva de forma temporal a la URL nueva. De esta manera redirigimos a los buscadores y usuarios de la antigua URL a la 
nueva pero no traspasamos la fuerza del SEO de una a otra.




##Ejercicio T4.6:
###Buscar informaci�n sobre los bloques de IP para los distintos pa�ses o continentes. Implementar en JavaScript o PHP la detecci�n de la zona desde donde se conecta un usuario

Existen 4 organizaciones continentales que tienen la misi�n de asignar y controlar el uso de direcciones IP por parte de los pa�ses.
 Estas son APNIC (www.apnic.net) para Asia y el Pac�fico, ARIN (www.arin.net) para Norteam�rica, LACNIC (www.lacnic.net) para Latinoam�rica y el Caribe, 
y RIPE (www.ripe.net) para Europa, Africa del norte y Rusia).
Cada una de estas organizaciones mantiene un registro detallado de los grupos o bloques de direcciones IP que se han asignado a los distintos 
Si juntamos la informaci�n de estas cuatro entidades, podemos construir una gran base de datos conteniendo todos los bloques de direcciones IP del 
mundo asignados a sus respectivos pa�ses.
VENTAJAS: Al tratarse de una base de datos local los sistemas basados en esta t�cnica obtienen la informaci�n en menos de una mil�sima del tiempo que 
insumir�a una consulta DNS. Esta t�cnica permite identificar sin problemas el origen geogr�fico real de m�quinas con las extensiones .com .net .edu y .org 
(que los sistemas basados en DNS son incapaces de resolver).
DESVENTAJAS: Las entidades reguladoras asignan nuevas direcciones cada pocos meses, por lo cual la base de datos debe ser actualizada. Por lo tanto un 
mecanismo de geotargeting basado en base de datos de IPs requiere un cierto mantenimiento si queremos evitar que quede desactualizado y nos brinde 
resultados err�neos.





##Ejercicio T4.7:
###Buscar informaci�n sobre m�todos y herramientas para implementar GSLB. 

El Global Server Load Balancing (GLSB) es popular por su funci�n de recuperaci�n de desastres y, tambi�n por la direcci�n inteligente de 
tr�fico para la selecci�n optimizada del lugar. La funcionalidad de GSLB de A10 est� disponible en todos los Application Delivery Controller
 y productos de balanceo de carga de Serie AX

*Modos de implantaci�n del GSLB*

La funcionalidad del GSLB de A10 extiende el balanceo de carga a una escala geogr�fica global, ofreciendo una elecci�n entre los m�todos 
DNS Proxy y DNS Server. El GSLB de A10 adiciona otro nivel de disponibilidad y desempe�o para aplicaciones, con el m�nimo de impacto existente
 en la arquitectura DNS, mientras se escoge el m�todo que mejor se encaja en su ambiente.

*Fuentes*

http://www.monografias.com/trabajos28/geotargeting-mostrar-contenidos-pais-visitante/geotargeting-mostrar-contenidos-pais-visitante.shtml#a4
http://www.clm.com.pe/productos/a10/ax-global-server-load-balancing.htm
https://kemptechnologies.com/load-balancer-kemp-f5-netscaler-comparison/?ktok=iu9pkFDxjt8gVD85VCJwj3ZbGEtaTuVdjY==