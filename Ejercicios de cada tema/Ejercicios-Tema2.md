
#EJERCICIOS TEMA 1

#Nombre : Joaquin Ballesteros Ortega



##Ejercicio T2.1

###Calcular la disponibilidad del sistema si tenemos dos réplicas de cada elemento (en total 3 elementos en cada subsistema)


En cualquier sistema con N componentes para calcular la disponibilidad del sistema se calcula como:

As = Ac1 * Ac2 * Ac3 * ... * Acn

En este caso seria :  As = Ac1 + (1-Ac1) * Ac2

**Web**

Web_2= 0.85+(1-0.85)*0.85 = 0.9775 (97.75%)
Web_3= 0.9775+(1-0.9775)*0.85 = 0.9966

**Application**

App_2= 0.9+(1-0.9)*0.9 = 0.99
App_3= 0.99+(1-0.99)*0.9 = 0.999

**Database**

Db_2=0.999+(1-0.999)*0.999 = 0.99999
Db_3=0.99999+(1-0.99999)*0.999 = 0.9999999

**Domain Name System**

DNS_2= 0.98+(1-0.98)*0.98 = 0.9996
DNS_3 0.9996+(1-0.9996)*0.98 = 0.9999

**Firewall**

Firewall_2= 0.85+(1-0.85)*0.85 = 0.9775
Firewall_3= 0.9775+(1-0.9775)*0.85 = 0.9966

**Switch**
Switch_2= 0.99+(1-0.99)*0.99= 0.9999
Switch_3= 0.9999+(1-0.9999)*0.99= 0.999999


**Data Center**

DC_2= 0.9999+(1-0.9999)*0.9999 = 0.99999999
DC_3= 0.99999999+(1-0.99999999)*0.9999 = 0.999999999999

**Internet Service Provider**

ISP_2= 0.95+(1-0.95)*0.95 = 0.9975
ISP_3= 0.9975+(1-0.9975)*0.95 = 0.999875

As = Web_3*App_3*Db_3*DNS_3*Firewall_3*Switch_3*DC_3*ISP_3 = 0.9908 

**Solucion = 99.08%**



##Ejercicio T2.2

###Buscar frameworks y librerías para diferentes lenguajes que permitan hacer aplicaciones altamente disponibles con relativa facilidad. 

Ruby: Lotus, Nyny, Grape, Pakyow, Celluloid.
PHP : Medoo, Flight, Phpixie, Yii, Codeigniter, Laravel, Phalcon, Kohana.
Python: Django, Web2py, TurboGears, Webapp2, CubicWeb, Grok, Giotto.
Javascript: Dojo, EachJS, Echo3, Ember.js, Kendo UI , Pyjamas, Qooxdoo.



##Ejercicio T2.3

###¿Cómo analizar el nivel de carga de cada uno de los subsistemas en el servidor?
Buscar herramientas y aprender a usarlas....¡o recordar cómo usarlas!

Algunas son:

* Pingdom Tools.
* GTmetrix.
* WebPageTest.
* Google Page Speed.
* YSlow.

Entre las mas importantes:

Google PageSpeed Insights es una poderosa herramienta de análisis que aumenta el rendimiento de tu sitio web.
que ofrece Google para optimizar los sitios web. 
Basta introducir la URL del sitio para que genere un reporte personalizado con un listado de sugerencias (bastante técnicas) para mejorar
el tiempo de carga en navegadores de escritorio y en dispositivos móviles. Dispone de extensiones para Firefox y Chrome.


##Ejercicio T2.4

####Buscar ejemplos de balanceadores software y hardwareV(productos comerciales). 

Balanceadores software :

+HAProxy
+Zen Load Balancer
+nginx
+Octopus Load Balancer
+Apache: mod_proxy_balancer
+varnish
+Servitux

Balanceadores hardware

+Barracuado Load Balancer ADC
+CoyotePoint Equalizer Appliances
+Radware AppDirector OnDemand Switch Series
+Serie BIG-IP de f5.
+Cisco 
+AppDirector OnDemand de la compañía Radware.
LoadMaster 2600

####Buscar productos comerciales para servidores de aplicaciones.

+Servidor de aplicaciones Microsoft
+JBoss
+JOnAS
+Oracle WebLogic Server
+WebSphere Application Server
+GlassFish Server

####Buscar productos comerciales para servidores de almacenamiento.

+Servidor almacenamiento DELL
+Dell Compellent FS8600
+HP ConvergedSystem 200-HC StoreVirtual System
+IBM EXP2500 Storage Enclosure 



##Referencias 

T2.1 Diapositivas tema 2 de clase

T2.2 https://en.wikipedia.org/wiki/Comparison_of_JavaScript_frameworks
     https://wiki.python.org/moin/WebFrameworks/
     http://webdesignmoo.com/web-design/10-best-ruby-frameworks-for-developers

T2.3 https://topalternatives.com/testing-your-websites-speed-and-performance/
     https://es.wordpress.org/plugins/google-pagespeed-insights/

T2.4 https://es.wikipedia.org/wiki/Balanceador_de_carga
