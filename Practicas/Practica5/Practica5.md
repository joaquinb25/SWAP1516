**Carlos Toledano Delgado - Joaquín Ballesteros Ortega**

#Práctica 5. Replicación de bases de datos MySQL

El objetivo de esta práctica es configurar las máquinas virtuales para que la información contenida en sus bases de datos siempre esté actualizada, tendremos una máquina virtual con la base de datos principales y 
otra que tendrá la misma base de datos principal replicada completamente.


##1.Crear una BD e insertar datos

Lo primero es crear la base de datos, la seleccionamos y empezamos creando una tabla en su interior (la tabla “datos”).
 Ahora podemos insertar registros en su interior:

mysql -uroot -p

mysql> create database contactos;

mysql> use contactos;

mysql> show tables;

mysql> create table datos(nombre varchar(100),tlf int);

mysql> show tables;

mysql> insert into datos(nombre,tlf) values ("pepe",95834987);

mysql> select * from datos;

Ya tenemos datos (un registro) insertados en nuestra BD llamada “datos”. Podemos haber insertado más registros. Veamos cómo entrar y hacer una consulta:

mysql -uroot -p

mysql> use contactos;

mysql> select * from datos;

mysql> describe datos;

mysql> quit


![M1](https://github.com/joaquinb25/SWAP1516/blob/master/Practicas/Practica5/IMG/1.png)





Replicar una BD MySQL con mysqldump
Vamos a guardar los datos que tenemos en la BD que acabamos de crear en la máquina 1 con mysqldump. Para ello, vamos primero a bloquear las tablas, ya que antes de hacer la copia de seguridad debemos impedir que la BD se modifique. Después ejecutamos la orden mysqldump contactos -u root -p > /root/contactos.sql, que nos pedirá la contraseña de la mysql, y una vez hecho esto, tendremos los datos copiados.
 Ahora podemos volver a entrar en la BD y desbloquear las tablas.

![](https://github.com/joaquinb25/SWAP1516/blob/master/Practicas/Practica5/IMG/2.png)


Vamos a la máquina 2 y guardamos los datos que acabamos de copiar 
(poniendo la IP de la máquina 1):

![](https://github.com/joaquinb25/SWAP1516/blob/master/Practicas/Practica5/IMG/3.png)




Ahora es necesario que creemos la base de datos que hemos creado en la máquina 1
 para poder copiar los datos en la BD de la máquina 2. Entramos entonces en mysql y
 una vez tengamos la BD creada ejecutamos mysql -uroot -p contactos < /root/contactos.sql

![](https://github.com/joaquinb25/SWAP1516/blob/master/Practicas/Practica5/IMG/4.png)


Replicación de BD mediante una configuración maestro-esclavo
Vamos a automatizar el proceso anterior con una configuración maestro-esclavo. Para ello, debemos partir de tener clonadas ambas bases de datos en las dos máquinas. Comenzamos editando el archivo /etc/mysql/my.cnf y comentamos el parámetro #bind-address 127.0.0.1 y establecemos el identificador del servidor a 1, modificamos las variables log_error y log_bin.

Reiniciamos mysql con /etc/init.d/mysql restart y modificamos el mismo archivo en la máquina 2 con las mismas modificaciones excepto el id del servidor, que ponemos a 2, y reiniciamos el servicio también.

Volvemos al maestro (máquina 1) y ejecutamos las sentencias:

mysql> CREATE USER esclavo IDENTIFIED BY 'esclavo'; mysql> GRANT REPLICATION SLAVE ON . TO 'esclavo'@'%' IDENTIFIED BY 'esclavo'; mysql> FLUSH PRIVILEGES; mysql> FLUSH TABLES; mysql> FLUSH TABLES WITH READ LOCK;

Y ahora hacemos SHOW MASTER STATUS e introducimos los datos en el esclavo para establecer la relación entre ambas máquinas:

mysql> CHANGE MASTER TO MASTER_HOST='192.168.111.132', MASTER_USER='esclavo', MASTER_PASSWORD='esclavo', MASTER_LOG_FILE='mysql-bin.000001', MASTER_LOG_POS=399, MASTER_PORT=3306;

Por último, arrancamos el esclavo y ya está todo listo para que los demonios de MySQL de las dos máquinas repliquen automáticamente los datos que se introduzcan/modifiquen/borren en el servidor maestro: mysql> START SLAVE;

Ahora, podemos hacer pruebas en el maestro y deberían replicarse en el esclavo automáticamente.

Por último, volvemos al maestro y volvemos a activar las tablas para que puedan meterse nuevos datos en el maestro: mysql> UNLOCK TABLES;

Para comprobar que todo funciona, debemos ir al maestro e introducir nuevos datos a la base de datos. A continuación vamos al esclavo para revisar si la modificación se ha reflejado en la tabla modificada en el maestro:


![servidor1](https://github.com/joaquinb25/SWAP1516/blob/master/Practicas/Practica5/IMG/5.png)
![servidor2](https://github.com/joaquinb25/SWAP1516/blob/master/Practicas/Practica5/IMG/6.png)
