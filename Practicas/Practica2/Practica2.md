**Carlos Toledano Delgado - Joaquín Ballesteros Ortega**

#**Práctica 2. Clonar la información de un sitio web**

Los objetivos concretos de esta segunda práctica son:
• aprender a copiar archivos mediante ssh
• clonar contenido entre máquinas
• configurar el ssh para acceder a máquinas remotas sin contraseña
• establecer tareas en cron

#**Instalación de rsync**
Ejecutamos el comando apt-get install rsync. 


#**Instalación de rsync**

Lo primero que vamos a probar es copiar archivos mediante ssh de una máquina a otra, como prueba vamos a copiar un directorio, para ello primero lo comprimiremos con tar, y lo pasamos mediante “ssh” al otro ordenador, redirigiendo además la salida a un archivo que en este caso vamos a llamar “tar.tgz”. Vemos como el archivo se ha creado en la segunda máquina.

![M2](https://github.com/joaquinb25/SWAP1516/blob/master/Practicas/Practica2/IMG/tarm2.png?raw=true)

![M1](https://github.com/joaquinb25/SWAP1516/blob/master/Practicas/Practica2/IMG/tar%20m1.png?raw=true)


Ya hemos visto como copiar un archivo desde un ordenador a otro, pero cuando la dimensión de los archivos es considerable en tamaño o número, es mejor usar otras herramientas como rsync, que nos permitirá copiar una estructura de directorios completa, además controlando que la información que contiene la copia siempre es idéntica a la original. Para evitar contratiempos, activaremos las cuentas de usuario “root” en ambos sistemas para realizar esta operación, esto se hace dándolo una contraseña a dicho usuario, por lo que introduciremos sudo passwd root para realizar dicha acción. Una vez hecho esto, ejecutamos rsync, y finalmente comprobamos que los archivos copiados son exactos a los originales.

rsync -avz -e ssh root@192.168.1.10:/var/www/ /var/www/ 

foto rsync m2
foto rsyn 1

#**Acceso sin contraseña para ssh**

Para no tener que introducir la contraseña del usuario cada vez que queramos hacer una copia de seguridad usaremos autentificación mediante par de claves pública-privada. Primero generamos la clave en el ordenador desde el que realizaremos la conexión, para generar dicha clave usamos ssh-keygen –t dsa, que nos generará una clave DSA. No introducimos ninguna contraseña cuando nos la solicite ya que ese es el objetivo, no tener que introducir contraseña.

foto key m2

Para hacer la copia de la clave, lo que haremos es copiarla a la máquina principal:

ssh-copy-id -i /root/.ssh/id_dsa.pub root@192.168.1.10
 
 foto keym2 a m1

 Podremos comprobar el funcionamiento de lo que acabamos de hacer si nos conectamos mediante ssh al ordenador principal desde el ordenador secundario y ejecutamos una orden cualquiera, como puede ser uname –a en este caso.

 foto ssh a m1 desde m2

#**Programar tareas con crontab**

Por tanto, ya tenemos la orden para actualizar los archivos en nuestro servidor web y el acceso para poder hacerlo automáticamente, con lo que sólo tenemos que modificar el archivo /etc/crontab y añadir una nueva línea con la instrucción que queremos realizar en cada hora en punto, esto es, el rsync, siguiendo el formato adecuado:

foto crontab
