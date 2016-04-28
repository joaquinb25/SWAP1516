#Ejercicios Tema 4

#Nombre : Joaquín Ballesteros Ortega


##Ejercicio T4.1:
###Buscar información sobre cuánto costaría en la actualidad un mainframe. Comparar precio y potencia entre esa máquina y una granja web de unas prestaciones similares. 

El ultimo mainframe conocido es el IBM z13, es un chip fabricado por IBM para sus z13 ordenadores centrales. 
Fabricado en GlobalFoundries  planta de fabricación (anteriormente propia planta de IBM). 
IBM ha destacado que es microprocesador más rápido del mundo y es un 10% más rápido que su predecesor, el zEC12 en la computación de un único subproceso 
en general, pero significativamente más al hacer tareas especializadas. 

El precio es mayor que para una granja web, aunque el gasto en electricidad y el espacio ocupado será menor pero es más difícilmente escalable y un fallo 
en la máquina nos dejaría sin poder servir a los clientes.


##Ejercicio T4.2:
###Buscar información sobre precio y características de balanceadores hardware específicos. Compara las prestaciones que ofrecen unos y otros. 

**Rendimiento frente Costo: Alto Rendimiento de carga virtual del equilibrador**

Al comparar el rendimiento de los equilibradores de carga de alto rendimiento virtuales (5 Gb +) de KEMP, F5 y Citrix, la KEMP VLM- 5000 y 10G ofrece el mismo rendimiento 5/10 Gbps como Big-IP de F5 VE-10G a un costo significativamente menor.


**Rendimiento frente Costo: Alto Rendimiento del equilibrador de carga de hardware**

El equilibrador de carga de alto rendimiento KEMP LoadMaster-8000 proporciona más rendimiento por $ 1 que en los 7000s F5 BIG-IP LTM y Citrix MPX y en una fracción del costo.


**Rendimiento frente Costo: medio rango de hardware equilibrador de carga**

La comparación de los equilibradores de carga de gama media - aquellos con rendimientos que van desde 3-6Gbps - la KEMP LoadMaster-4000 proporciona cerca del mismo rendimiento y la misma funcionalidad básica en comparación con LTM de F5-2x (Mejor Licencia) y Citrix NetScaler MPX-8005 al 1 / 3 el precio y más rendimiento por $ 1.


**Rendimiento frente Costo: Categoría estándar virtual del equilibrador de carga**

El KEMP VLM-2000 proporciona un rendimiento similar al de VE-1G / 5G y Citrix NetScaler VPX-1000/3000 F5 BIG-IP LTM durante al menos 1/3 del costo.

**Rendimiento frente Costo: entrada virtual del equilibrador de carga**

Al comparar la KEMP VLM-200 a la F5 BIG-IP LTM VE-200M y Citrix NetScaler VPX 200, el KEMP VLM-200 ofrece el mismo rendimiento como F5 y Citrix en ½ y ¼ cuarta parte del costo, respectivamente.

Las transacciones SSL equilibrador de carga de hardware.

El KEMP LoadMaster-8000 es compatible con más de TPS SSL (transacciones por segundo) que el 4000 (licencia Mejor Edición) F5 BIG-IP LTM al 60% del coste y un coste similar por transacción SSL como Citrix MPX 8015, pero a un $ 30.000 menor Precio de lista.

Las transacciones de equilibrador de carga SSL virtual

El KEMP VLM-10G soporta SSL TPS 3 veces más que el F5 BIG-IP LTM VE-10G a un costo 66% inferior y 4.5x el TPS SSL de Citrix NetScaler VPX-3000 de $ 11.000 menos.


##Ejercicio T4.5:
###Probar las diferentes maneras de redirección HTTP.¿Cuál es adecuada y cuál no lo es para hacer balanceo de carga global? ¿Por qué?

Principalmente hay 2 tipos de redirecciones que debes conocer:

**Redireccionamiento 301**: Se puede definir este tipo de redireccion como “PERMANENTE”. Esto indica que todo contenido de una URL
 antigua se mueva de forma permanente a la URL nueva. De esta manera los buscadores dejarán de tener en cuenta la antigua URL y 
le traspasarán “aproximadamente” el 90% de la fuerza SEO a la nueva Web.

**Redireccionamiento 302**: Se puede definir este tipo de redirección como “TEMPORAL”. Esto indica que todo el contenido de una URL 
antigua se mueva de forma temporal a la URL nueva. De esta manera redirigimos a los buscadores y usuarios de la antigua URL a la 
nueva pero no traspasamos la fuerza del SEO de una a otra.




##Ejercicio T4.6:
###Buscar información sobre los bloques de IP para los distintos países o continentes. Implementar en JavaScript o PHP la detección de la zona desde donde se conecta un usuario

Existen 4 organizaciones continentales que tienen la misión de asignar y controlar el uso de direcciones IP por parte de los países.
 Estas son APNIC (www.apnic.net) para Asia y el Pacífico, ARIN (www.arin.net) para Norteamérica, LACNIC (www.lacnic.net) para Latinoamérica y el Caribe, 
y RIPE (www.ripe.net) para Europa, Africa del norte y Rusia).
Cada una de estas organizaciones mantiene un registro detallado de los grupos o bloques de direcciones IP que se han asignado a los distintos 
Si juntamos la información de estas cuatro entidades, podemos construir una gran base de datos conteniendo todos los bloques de direcciones IP del 
mundo asignados a sus respectivos países.

1-VENTAJAS: Al tratarse de una base de datos local los sistemas basados en esta técnica obtienen la información en menos de una milésima del tiempo que 
insumiría una consulta DNS. Esta técnica permite identificar sin problemas el origen geográfico real de máquinas con las extensiones .com .net .edu y .org 
(que los sistemas basados en DNS son incapaces de resolver).

2- DESVENTAJAS: Las entidades reguladoras asignan nuevas direcciones cada pocos meses, por lo cual la base de datos debe ser actualizada. Por lo tanto un 
mecanismo de geotargeting basado en base de datos de IPs requiere un cierto mantenimiento si queremos evitar que quede desactualizado y nos brinde 
resultados erróneos.





##Ejercicio T4.7:
###Buscar información sobre métodos y herramientas para implementar GSLB. 

El Global Server Load Balancing (GLSB) es popular por su función de recuperación de desastres y, también por la dirección inteligente de 
tráfico para la selección optimizada del lugar. La funcionalidad de GSLB de A10 está disponible en todos los Application Delivery Controller
 y productos de balanceo de carga de Serie AX

**Modos de implantación del GSLB**

La funcionalidad del GSLB de A10 extiende el balanceo de carga a una escala geográfica global, ofreciendo una elección entre los métodos 
DNS Proxy y DNS Server. El GSLB de A10 adiciona otro nivel de disponibilidad y desempeño para aplicaciones, con el mínimo de impacto existente
 en la arquitectura DNS, mientras se escoge el método que mejor se encaja en su ambiente.


**Fuentes**

http://www.monografias.com/trabajos28/geotargeting-mostrar-contenidos-pais-visitante/geotargeting-mostrar-contenidos-pais-visitante.shtml#a4
http://www.clm.com.pe/productos/a10/ax-global-server-load-balancing.htm
https://kemptechnologies.com/load-balancer-kemp-f5-netscaler-comparison/?ktok=iu9pkFDxjt8gVD85VCJwj3ZbGEtaTuVdjY==
https://en.wikipedia.org/wiki/IBM_z13_(microprocessor)
