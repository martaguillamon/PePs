---
typora-copy-images-to: ../../myassets/img/hardening/
typora-root-url: ../../
layout: post

---
---


Creamos un contenedor de Docker con Apache instalado en su interior. Creamos un directorio donde guardaremos el fichero *index.html* y otro directorio donde guardaremos un fichero .txt. Si lanzamos el contenedor y accedemos al directorio donde se ha guardado el fichero .txt obtendremos un resultado similar a el siguiente:

![](/PePs/myassets/img/hardening/Captura de pantalla_2021-03-22_16-01-26.png)

![](/PePs/myassets/img/hardening/5.png)

Como se puede ver, se listan los ficheros que se encuentran dentro del directorio y ademas se muestra la versión de Apache que se encuentra instalada, así como el sistema operativo. 



Para evitar que esto ocurra deshabilitaremos el módulo *autoindex* ejecutendo el siguiente comando:

![](/PePs/myassets/img/hardening/6.png)



Para que no se muestre la versión de Apache y la signatura modificaremos el archivo de configuración de Apache */etc/apache2/apache2.conf* añadiendo las siguientes lineas:

![](/PePs/myassets/img/hardening/9.png)
