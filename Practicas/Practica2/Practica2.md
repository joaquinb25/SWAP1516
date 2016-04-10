Carlos Toledano Delgado - Joaqu�n Ballesteros Ortega

Pr�ctica 2. Clonar la informaci�n de un sitio web
Los objetivos concretos de esta segunda pr�ctica son: � aprender a copiar archivos mediante ssh � clonar contenido entre m�quinas � configurar el ssh para acceder a m�quinas remotas sin contrase�a � establecer tareas en cron

Instalaci�n de rsync
Ejecutamos el comando apt-get install rsync.

Una vez instalado vamos a comprobar que funciona. De la primera pr�ctica, ya ten�amos el fichero hola.html en las dos m�quinas, as� que vamos a comprobar con la herramienta curl el contenido que tiene dicho archivo en la m�quina 2.
Imagen
(mirar esta parte)


piar archivos mediante ssh
Lo primero que vamos a probar es copiar archivos mediante ssh de una m�quina a otra,
 como prueba vamos a copiar un directorio, para ello primero lo comprimiremos con tar,
 y lo pasamos mediante �ssh� al otro ordenador, redirigiendo adem�s la salida a un archivo 
que en este caso vamos a llamar �tar.tgz�. Vemos como el archivo se ha creado en la segunda m�quina.

Imagen
Imagen


Clonar contenido entre m�quinas
Ya hemos visto como copiar un archivo desde un ordenador a otro, pero cuando la dimensi�n de los archivos es considerable en tama�o o n�mero, es mejor usar otras herramientas como rsync, que nos permitir� copiar una estructura de directorios completa, adem�s controlando que la informaci�n que contiene la copia siempre es id�ntica a la original. Para evitar contratiempos, activaremos las cuentas de usuario �root� en ambos sistemas para realizar esta operaci�n, esto se hace d�ndolo una contrase�a a dicho usuario, por lo que introduciremos sudo passwd root para realizar dicha acci�n. Una vez hecho esto, ejecutamos rsync, y finalmente comprobamos que los archivos copiados son exactos a los originales.

rsync -avz -e ssh root@192.168.1.10:/var/www/ /var/www/

Imagen

Imagen


Acceso sin contrase�a para ssh
Para no tener que introducir la contrase�a del usuario cada vez que queramos hacer una copia de seguridad usaremos autentificaci�n mediante par de claves p�blica-privada. Primero generamos la clave en el ordenador desde el que realizaremos la conexi�n, para generar dicha clave usamos ssh-keygen �t dsa, que nos generar� una clave DSA. No introducimos ninguna contrase�a cuando nos la solicite ya que ese es el objetivo, no tener que introducir contrase�a.

Imagen

Para hacer la copia de la clave, lo que haremos es copiarla a la m�quina principal:

ssh-copy-id -i /root/.ssh/id_dsa.pub root@192.168.1.10

Imagen

Podremos comprobar el funcionamiento de lo que acabamos de hacer si nos conectamos mediante ssh al ordenador principal desde el ordenador secundario y ejecutamos una orden cualquiera, como puede ser uname �a en este caso.

Imagen




Programar tareas con crontab
Por tanto, ya tenemos la orden para actualizar los archivos en nuestro servidor 
web y el acceso para poder hacerlo autom�ticamente, con lo que s�lo tenemos que modificar
 el archivo /etc/crontab y a�adir una nueva l�nea con la instrucci�n que queremos realizar en
 cada hora en punto, esto es, el rsync, siguiendo el formato adecuado:

Imagen