#Ejercicios Tema 7


#Nombre: Joaquin Ballesteros Ortega


##Ejercicio 7.1

###�Qu� tama�o de unidad de unidad RAID se obtendr� al
configurar un RAID 0 a partir de dos discos de 100 GB y
100 GB? 

Se obtendr� un tama�o de 200 GB porque el RAID0 aumenta la capacidad del disco final sumandose las dos.

###�Qu� tama�o de unidad de unidad RAID se obtendr� al
configurar un RAID 0 a partir de tres discos de 200 GB
cada uno? 

Seria el mismo caso de antes a diferencia que tenemos tres discos de 200, por lo tanto seria la suma de los tres(200+200+200) dando 600 GB.




##Ejercicio 7.2

###�Qu� tama�o de unidad de unidad RAID se obtendr� al
configurar un RAID 1 a partir de dos discos de 100 GB y
100 GB? 

Como caracter�stica especial del RAID1 es crea una copia exacta (o espejo) de un conjunto de datos en dos o m�s discos por lo tanto el tama�o del RAID ser� de 100GB .

###�Qu� tama�o de unidad de unidad RAID se obtendr� al configurar un RAID 1 a partir de tres discos de 200 GB cada uno?

Siendo el mismo caso que antes el tama�o es 200 GB.




##Ejercicio 7.3

###�Qu� tama�o de unidad de unidad RAID se obtendr� al
configurar un RAID 5 a partir de tres discos de 120 GB
cada uno? 

En el RAID5 divide los datos a nivel de bloques, distribuyendo la
informaci�n de paridad entre los discos del conjunto. 

Cada vez que un bloque de datos se escribe en un RAID 5, se
genera un bloque de paridad dentro de la misma divisi�n.
Si un bloque, o alguna porci�n de
un bloque, es escrita en
una divisi�n, el bloque de paridad
(o una parte del mismo) es
recalculada y vuelta a escribir. 


Por lo tanto unidad RAID ser�a de 240GB quedando un disco de 120GB como disco de paridad.



##Ejercicio T7.4
###Buscar informaci�n sobre los sistemas de ficheros en red m�s utilizados en la actualidad y comparar suscaracter�sticas. Hacer una lista de ventajas e invenientes de todos ellos, as� como grandes
sistemas en los que se utilicen. 


Los sistemas de archivo de red permiten acceder a ficheros remotos como si estuviesen en un medio de almacenamiento local. 
Gracias al sistema de archivos de red un ordenador cliente puede acceder a sistemas de archivos que exporta el servidor, con independencia del sistema 
de archivos de disco que se utiliza en el servidor.


*Algunos sistemas de archivos de red son:*


*SMB/CIFS*:Es el sistema nativo de Windows.Permite navegar por los recursos ofrecidos y est� orientado al funcionamiento en LAN
*NFS*:Es el sistema nativo de Unix.No est� pensado para navegar por los recursos y funciona en WAN
*Coda*:El cliente guarda de forma local los ficheros de trabajo, para asegurar la disponibilidad cuando no existe conexi�n de red
*Intermezzo*:Inspirado en Coda pero dise�ado de nuevo
*Lustre*:Nuevo desarrollo destinado a supercomputaci�n. Para grandes clusters o procesadores masivamente paralelos (MPP).




*NFS - Network File System*

NFS permite que un servidor exporte un sistema de ficheros, y uno o varios clientes, lo monten para utilizarlo como un sistema de ficheros local. La comunicaci�n entre el servidor y el cliente se realiza a trav�s de la red, utilizando el protocolo NFS. El sistema de ficheros de disco que utiliza f�sicamente el servidor es irrelevante para el cliente.

NFS es enrutable, de manera que el servidor y el cliente pueden estar en diferentes redes comunicadas por un conjunto de routers.



*SMB/CIFS - Server Message Block/Common Internet File System*

El protocolo SMB fue dise�ado originalmente por IBM, pero actualmente la versi�n m�s extendida del mismo es la implementada por Microsoft en sus sistemas operativos, hoy en d�a denominada CIFS. En Unix existe el servicio Samba que implementa un servidor y cliente para SMB/CIFS.

Entre las caracter�sticas del protocolo encontramos:

Permite compartir sistemas de archivos e impresoras
Tradicionalmente ha utilizado NetBIOS/NetBEUI aunque las versiones nuevas pueden funcionar encima de TCP/IP. Cuando no se utiliza TCP/IP no existe posibilidad de enrutado, de manera que cliente y servidor deben estar en la misma red
El servicio permite explorar la red para descubrir m�quinas y recursos compartidos
Tradicionalmente se ha utilizado una resoluci�n de nombres WINS, aunque en las versiones nuevas (a partir de Windows 2000) se ha relegado en favor de DNS y Active Directory



*Otras opciones: Coda / Intermezzo / Lustre*

Los sistemas de ficheros en red Coda e InterMezzo intentan dar soporte a dispositivos m�viles que se conectan/desconectan con frecuencia de la red. Para permitir el funcionamiento de los clientes durante las desconexiones de red, estos guardan una copia local (cach�) del sistema de archivos remoto. Cuando se restablece la conexi�n de red, los clientes envian los cambios locales al servidor. En este proceso pueden surgir conflictos (cuando dos o m�s clientes han hecho cambios locales sobre los mismos datos e intentan actualizar el servidor).

El sistema de archivos en red Lustre es el nuevo proyecto en el que participan los desarrolladores de InterMezzo, est� destinado a la supercomputaci�n y 
tiene por objetivo conseguir un gran rendimiento al tiempo que resuelve las necesidades de almacenamieno de grandes clusters o m�quinas masivamente paralelas.




*Fuentes:*

http://elpuig.xeill.net/Members/vcarceler/c1/didactica/apuntes/ud4/na6