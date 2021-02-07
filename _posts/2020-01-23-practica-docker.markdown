---
typora-copy-images-to: ../../myassets/img/docker/
typora-root-url: ../../
layout: post
---

# 						                                           **Práctica Docker**

1. ####  **Comprobaciones antes de realizar la práctica**

   Comprobamos que Docker está instalado correctamente, para ello ejecutemos el comando *docker ps:*

   ![](/PePs/myassets/img/docker/1.png)

2. #### **Primer contenedor en Docker**

   Primero ejecutemos el script *build.sh* para construir el contenedor

   ![](/PePs/myassets/img/docker/2.png)

   

3. #### **Ejecutar el contenedor**

   Una vez construido, lanzamos el script *debug.sh* para lanzar el contenedor

   ![](/PePs/myassets/img/docker/3.png)

​		Accedemos a https://localhost:8086/public_html/. Si se visita varias veces, el contador aumentará. 

![](/PePs/myassets/img/docker/4.png)

​		Comprobamos que el contenedor se está ejecutando con el comando *docker ps*:

![](/PePs/myassets/img/docker/5.png)

​		El siguiente paso es evitar que el contador empiece de 1 cada vez que se pare o se reinicie el contenedor. Para ello ejecutaremos el script *persisit.sh*:

![](/PePs/myassets/img/docker/6.png)

​		Paramos el contenedor y lo volvemos a iniciar para comprobar que se ha aplicado correctamente:

![](/PePs/myassets/img/docker/7.png)

​		Finalmente, ejecutamos el script *shell.sh* para iniciar el shell Bash para usar la linea de comandos:

![](/PePs/myassets/img/docker/8.png)





​	
