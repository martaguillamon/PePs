---



typora-copy-images-to: ../../myassets/img/seguridad_docker/
typora-root-url: ../../
layout: post

---

# **Seguridad host**

Para lograrlo uno de los factores a controlar són los permisos que se conceden a los usuarios. Sólo deben acceder a Docker aquellos usuarios con permiso *root*. 

Crearemos un grupo de docker donde se irán añadiendo los usuarios a los que les queramos dar permisos para ejecutar contenedores. En nuestro caso añadiremos a nuestro usuario:

![](/PePs/myassets/img/seguridad_docker/1.png)



Y recargamos los permisos para que se apliquen los cambios:

![](/PePs/myassets/img/seguridad_docker/2.png)





# **Seguridad en el demonio**

El daemon de Docker se ejecuta como superusuario, por lo que debemos impedir que los usuarios puedan tocar la configuración .

El archivo a modificar es */etc/docker/daemon.json* (si no existe, se tiene que crear) y añadimos las siguientes lineas:

![](/PePs/myassets/img/seguridad_docker/5.png)



Otro fichero que no debe ser accesible a ningún usuario que sea *root* es *key.json*, ya que en su interior se almacena la key para conectarse pot TLS.





# **Seguridad en contenedores**

Se le puede asignar a un contenedor un *ulimit* para fijar límites de tiempo de ejecución

![](/PePs/myassets/img/seguridad_docker/6.png)



También se pueden fijar límites al gasto de la cpu:

![](/PePs/myassets/img/seguridad_docker/7.png)



O que se reinicie el contenedor en caso de fallo:

![](/PePs/myassets/img/seguridad_docker/8.png)





# **Privilegios**

Por defecto el usuario al utlizar un contenedor es root.  Si forzamos a cambiar el usuario con el flag *-u* nos devolverá que no tenemos permisos suficientes.

![](/PePs/myassets/img/seguridad_docker/9.png)



Con la opción --privileged nos permitirá rea lizar cambios, como por ejemplo, montar unidades:



![](/PePs/myassets/img/seguridad_docker/10.png)

![](/PePs/myassets/img/seguridad_docker/11.png)

![12](/PePs/myassets/img/seguridad_docker/12.png)



Si realizamos la misma operación sin la opción mencionada anteriormente, no nos dejará montarlo.

![13](/PePs/myassets/img/seguridad_docker/13.png)



Otro ejemplo sería crear un contenedor dentro de otro contenedor:

![](/PePs/myassets/img/seguridad_docker/14.png)



# **Seguridad en imágenes**

Se recomienda utilizar imágenes oficiales, o en el defecto de querer usar otras, que se tenga acceso al Dockerfile para poder inspeccionarlo previamente.





# **Escaneo pasivo de vulnerabilidades**



Vamos a realizar un escaneo de vulnerabilidades de una imágen de wordpress. Para ello usaremos *trivy*:

![](/PePs/myassets/img/seguridad_docker/20.png)



![](/PePs/myassets/img/seguridad_docker/trivy-1.png)