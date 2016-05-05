#*Carlos Toledano Delgado - Joaquín Ballesteros Ortega*

#Práctica 3. Balanceo de carga

El objetivo de esta práctica es configurar una red entre varias máquinas de forma que tengamos un balanceador que reparta la carga entre varios servidores finales.

El problema a solucionar es la sobrecarga de los servidores. Se puede balancear cualquier protocolo, pero dado que esta asignatura se centra en las tecnologías web, balancearemos los servidores HTTP que tenemos configurados.

De esta forma conseguiremos una infraestructura redundante y de alta disponibilidad.

##Configurar una máquina e instalarle el nginx como balanceador de carga

1- El proceso de instalación en Ubuntu se basa en el uso de apt-get. Lo primero quedebemos hacer es importar la clave del repositorio de software: cd /tmp/ wget http://nginx.org/keys/nginx_signing.key apt-key add /tmp/nginx_signing.key rm -f /tmp/nginx_signing.key

A continuación, debemos añadir el repositorio al fichero /etc/apt/sources.list Para ello, podemos ejecutar las siguientes órdenes en el terminal: echo "deb http://nginx.org/packages/ubuntu/ lucid nginx" >> /etc/apt/sources.list echo "deb-src http://nginx.org/packages/ubuntu/ lucid nginx" >> /etc/apt/sources.list

Ahora ya podemos instalar el paquete del nginx: apt-get update apt-get install nginx

2- Una vez instalado, podemos proceder a su configuración como balanceador de carga.

La configuración de NginX se realiza en el archivo “/etc/nginx/conf.d/default.conf”, la configuración realizada nos permitirá redirigir
 el tráfico a un grupo de servidores que hemos llamado apaches con la directiva upstream, en dicho grupo de servidores hemos configurado 
que el primer servidor (server 192.168.111.128 weight=2) reciba el doble de carga que el servidor segundo (server 192.168.111.129 weight=1), 
el algoritmo para repartir la carga no es necesario que lo indiquemos porque se toma “round robin” por defecto al usar la directiva upstream. 
Dentro de la directiva location, deberemos indicar con la directiva proxy_pass hacia donde vamos a redirigir el tráfico entrante, en nuestro 
caso la dirección de acceso a nuestro grupo de servidores (http://apaches). Por último, debemos indicar que en los backends la versión de HTTP 
es 1.1 (proxy_http_version 1.1), y que se elimine la cabecera Connection (proxy_set_header Connextion “”).



![curl](https://github.com/joaquinb25/SWAP1516/blob/master/Practicas/Practica3/img/2016-05-05%2011_08_01-Balanceador%20-%20VMware%20Workstation.png?raw=true
)


Una vez completada la configuración, vamos a comprobar que las peticiones al servidor están sindiendo balanceadas según el criterio indicado, para ello mediante el navegador curl accederemos al balanceador mediante su dirección IP.

curl

##Configurar una máquina e instalarle el haproxy como balanceador de carga
Instalamos HAProxy sin ninguna complicación usando apt-get. Y procedemos a realizar su configuración en el archivo “/etc/haproxy/haproxy.cfg”. En la directiva frontend http-in, indicamos que se debe escuchar el tráfico del puerto 80 y redirigirlo hacia los servidores finales (default_backend servers). El grupo de servidores servers al que redirigimos el tráfico necesitaremos especificarlo con la directiva backend servers añadiéndole las líneas que representan cada uno de los servidores el primer servidor con el doble de carga (servidor1 192.168.111.128:80 maxconn 32 ) y el segundo servidor con la mitad de carga (servidor2 192.168.111.129:80 maxconn 32 weight 34).

curl

Una vez hecha la configuración, ya podemos comprobar el funcionamiento con curl http://"direccionIP"

curl
