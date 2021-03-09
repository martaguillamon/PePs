---
typora-copy-images-to: ../../myassets/img/protegido/
typora-root-url: ../../
layout: post

---

Vamos a crear un nuevo directorio con el nombre protected donde guardaremos el *index.html* de la página. Preferiblemente se creará en */var/www/html*.

![](/PePs/myassets/img/protegido/37.png)



Creamos y habilitamos un nuevo fichero de configuración de Apache, en el que se especificará el método de autenticación para poder acceder a la página:

![](/PePs/myassets/img/protegido/31.png)



Creamso los usuarios y guardamos sus contraseñas en el fichero *.htpasswd*

![](/PePs/myassets/img/protegido/30.png)



Si intentamos acceder al directorio protected, mediante 127.0.0.1/protected nos saltará una ventana pidiendo las credenciales del usuario.

Al introducirlas correctamente, accederemos al index.html que hemos generado anteriormente:

![](/PePs/myassets/img/protegido/33.png)



![](/PePs/myassets/img/protegido/34.png)



Si por el contrario, se introduce o el usuario o la contraseña de forma errónea no aparecerá un mensaje de *Unauthorized*

![](/PePs/myassets/img/protegido/36.png)