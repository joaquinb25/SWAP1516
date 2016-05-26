*Carlos Toledano Delgado - Joaqu�n Ballesteros Ortega*

#Pr�ctica 5. Replicaci�n de bases de datos MySQL

El objetivo de esta pr�ctica es configurar las m�quinas virtuales para que la informaci�n contenida en sus bases de datos siempre est� actualizada, tendremos una m�quina virtual con la base de datos principales y 
otra que tendr� la misma base de datos principal replicada completamente.


##1.Crear una BD e insertar datos

Lo primero es crear la base de datos, la seleccionamos y empezamos creando una tabla en su interior (la tabla �datos�).
 Ahora podemos insertar registros en su interior:

mysql -uroot -p

mysql> create database contactos;

mysql> use contactos;

mysql> show tables;

mysql> create table datos(nombre varchar(100),tlf int);

mysql> show tables;

mysql> insert into datos(nombre,tlf) values ("pepe",95834987);

mysql> select * from datos;

Ya tenemos datos (un registro) insertados en nuestra BD llamada �datos�. Podemos haber insertado m�s registros. Veamos c�mo entrar y hacer una consulta:

mysql -uroot -p

mysql> use contactos;

mysql> select * from datos;

mysql> describe datos;

mysql> quit


Imagen*





Replicar una BD MySQL con mysqldump
Vamos a guardar los datos que tenemos en la BD que acabamos de crear en la m�quina 1 con mysqldump. Para ello, vamos primero a bloquear las tablas, ya que antes de hacer la copia de seguridad debemos impedir que la BD se modifique. Despu�s ejecutamos la orden mysqldump contactos -u root -p > /root/contactos.sql, que nos pedir� la contrase�a de la mysql, y una vez hecho esto, tendremos los datos copiados.
 Ahora podemos volver a entrar en la BD y desbloquear las tablas.

Imagen


Vamos a la m�quina 2 y guardamos los datos que acabamos de copiar 
(poniendo la IP de la m�quina 1):

Imagen




Ahora es necesario que creemos la base de datos que hemos creado en la m�quina 1
 para poder copiar los datos en la BD de la m�quina 2. Entramos entonces en mysql y
 una vez tengamos la BD creada ejecutamos mysql -uroot -p contactos < /root/contactos.sql

Imagen


Replicaci�n de BD mediante una configuraci�n maestro-esclavo
Vamos a automatizar el proceso anterior con una configuraci�n maestro-esclavo. Para ello, debemos partir de tener clonadas ambas bases de datos en las dos m�quinas. Comenzamos editando el archivo /etc/mysql/my.cnf y comentamos el par�metro #bind-address 127.0.0.1 y establecemos el identificador del servidor a 1, modificamos las variables log_error y log_bin.

Reiniciamos mysql con /etc/init.d/mysql restart y modificamos el mismo archivo en la m�quina 2 con las mismas modificaciones excepto el id del servidor, que ponemos a 2, y reiniciamos el servicio tambi�n.

Volvemos al maestro (m�quina 1) y ejecutamos las sentencias:

mysql> CREATE USER esclavo IDENTIFIED BY 'esclavo'; mysql> GRANT REPLICATION SLAVE ON . TO 'esclavo'@'%' IDENTIFIED BY 'esclavo'; mysql> FLUSH PRIVILEGES; mysql> FLUSH TABLES; mysql> FLUSH TABLES WITH READ LOCK;

Y ahora hacemos SHOW MASTER STATUS e introducimos los datos en el esclavo para establecer la relaci�n entre ambas m�quinas:

mysql> CHANGE MASTER TO MASTER_HOST='192.168.111.132', MASTER_USER='esclavo', MASTER_PASSWORD='esclavo', MASTER_LOG_FILE='mysql-bin.000001', MASTER_LOG_POS=399, MASTER_PORT=3306;

Por �ltimo, arrancamos el esclavo y ya est� todo listo para que los demonios de MySQL de las dos m�quinas repliquen autom�ticamente los datos que se introduzcan/modifiquen/borren en el servidor maestro: mysql> START SLAVE;

Ahora, podemos hacer pruebas en el maestro y deber�an replicarse en el esclavo autom�ticamente.

Por �ltimo, volvemos al maestro y volvemos a activar las tablas para que puedan meterse nuevos datos en el maestro: mysql> UNLOCK TABLES;

Para comprobar que todo funciona, debemos ir al maestro e introducir nuevos datos a la base de datos. A continuaci�n vamos al esclavo para revisar si la modificaci�n se ha reflejado en la tabla modificada en el maestro:



Imagen servidor1
ImGEN servidor2
