---
typora-copy-images-to: ../../myassets/img/hardening/
typora-root-url: ../../
layout: post

---



Creamos un contenedor de Docker con Apache instalado en su interior. Creamos un directorio donde guardaremos el fichero *index.html* y otro directorio donde guardaremos un fichero .txt. Si lanzamos el contenedor y accedemos al directorio donde se ha guardado el fichero .txt obtendremos un resultado similar a el siguiente:

![](/PePs/myassets/img/hardening/Captura de pantalla_2021-03-22_16-01-26.png)

![](/PePs/myassets/img/hardening/5.png)

Como se puede ver, se listan los ficheros que se encuentran dentro del directorio y ademas se muestra la versión de Apache que se encuentra instalada, así como el sistema operativo. 



Para evitar que esto ocurra deshabilitaremos el módulo *autoindex* ejecutendo el siguiente comando:

![](/PePs/myassets/img/hardening/6.png)



Para que no se muestre la versión de Apache y la signatura modificaremos el archivo de configuración de Apache */etc/apache2/apache2.conf* añadiendo las siguientes lineas:

![](/PePs/myassets/img/hardening/9.png)





# **CSP**

CSP (*Content Security Policy*), ayuda a prevenir y mitigar ciertos tipos de ataques como el XSS o de inyección de datos. Para poder aplicarlo basta con añadir en el host virtual la siguiente cabecera:

| Header alway set Content-Security-Policy "default-src 'self' ; img-src *; media-src media1.com media2.com; script-src userscripts.example.com" |
| :----------------------------------------------------------: |
|                                                              |

![](/PePs/myassets/img/hardening/1.png)

Con esta linea podremos descargar imágenes desde cualquier lugar, los archivos multimedia solo serán permitidos desde *media1.com* y *media2.com* y los scripts ejecutables solo serán permitidos desde *userscripts.example.com*





# **HSTS**

HSTS (*HTTP Strict Transport Security*), es una política de seguridad web establecidad para evitar ataques. Vamos a definir una cabecera para que solo se admitan peticiones mediante HTTPS en el servidor. 

Para configurarlo, se debe añadir la siguiente linea en la configuración del host virtual:

| Headeralways set Strict-Transport-Security "max-age=63072000; includeSubDomains" |
| :----------------------------------------------------------: |
|           ![](/PePs/myassets/img/hardening/12.png)           |

Con esto le indicamos al navegador que sólo debe acceder a la versión segura del sitio durante aproximadamente 2 años.



- Configuración de Docker

  Dockerfile

![](/PePs/myassets/img/hardening/10.png)

debug.sh

![](/PePs/myassets/img/hardening/11.png)



El resultado debería ser similar al siguiente:

![](/PePs/myassets/img/hardening/14.png)





# **WAF**

WAF (Web Application Firewall) es un tipo de firewall que filtra o bloquea el tráfico HTTP de entrada y de salida de la página web. Antes de configurar el Dockerfile, primero instalaremos la libreria de *mod-security*.

![](/PePs/myassets/img/hardening/16.PNG)



Renombramos el fichero de configuración:

![](/PePs/myassets/img/hardening/17.PNG)

Ponemos el fichero de configuración en el directorio donde vamos a crear el Dockerfile. A continuación vamos a crearlo:

![](/PePs/myassets/img/hardening/18.PNG)



Si introducimos una entrada en el formulario que está bloqueada nos saltará un status code 403

![](/PePs/myassets/img/hardening/19.PNG)



![](/PePs/myassets/img/hardening/20.PNG)



