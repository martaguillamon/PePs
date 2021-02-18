---
typora-copy-images-to: ../../myassets/img/google_cloud/
typora-root-url: ../../
layout: post

---

#### Crear un proyecto de Cloud

Para crear un nuevo proyecto, accedemos al panel de Cloud Console. Introducimos un nombre identificativo para el proyecto y lo creamos.

![](/PePs/myassets/img/google_cloud/4.png)

El siguiente paso es habilitar App Engine para el proyecto Cloud. Para ello accedemos al panel de App Engine y clicamos en "Descargar el SDK de Google Cloud" lo que nos dará un comado para ejecutarlo en el terminal.

![](/PePs/myassets/img/google_cloud/6.png)

Pegamos el comando en nuestro terminal para descargarlo.

![](/PePs/myassets/img/google_cloud/8.png)



Descomprimimos el tar.gz que hemos descargado y accedemos al directorio. Dentro se encuentra un script llamado install.sh el cual ejecutaremos:

![](/PePs/myassets/img/google_cloud/11.png)



Una vez se ha instalado, procedemos a iniciarlo ejecutando el siguiente comando:

![]()![12](/PePs/myassets/img/google_cloud/12.png)



Al inicialrlo no pedirá si queremos seleccionar un proyecto ya creado o crear uno nuevo. Seleccionamos el proyecto que hemos generado anteriormente y ya tenenos preparado Google Cloud SDK:

![](/PePs/myassets/img/google_cloud/13.png)





#### Escribe tu servicio web con Node.js

Antes de nada tenemos que instalar Node.js. Ejecutamos el comando de instalación:

![](/PePs/myassets/img/google_cloud/7.png)



Vamos a crear una carpeta para guardar en su interior nuestro servicio web

![](/PePs/myassets/img/google_cloud/14.png)



Instalamos npm, que nos permitirá descargar las dependencias necesarias para el proyecto.

![](/PePs/myassets/img/google_cloud/15.png)



El siguiente paso es crear el archivo package,json, para ello ejecutamos el comando npm init:

![](/PePs/myassets/img/google_cloud/16.png)



Instalamos la dependencia express:

![](/PePs/myassets/img/google_cloud/18.png)



Dentro del archivo package.json añadimos dentro de la categoria de "scripts" la siguiente linea:

![](/PePs/myassets/img/google_cloud/19.png)



Dentro del directorio de nuestro proyecto creamos un archivo llamado server.js y le agregamos el siguiente código:

![](/PePs/myassets/img/google_cloud/21.png)

En este código le pedimos que muestre por pantalla el mensaje "Hello from App Engine" y que el servidor se encuentre en escucha en el puerto 8080.



Para comprobar que funciona bien, lo ejecutamos mediante el comando npm start:

![](/PePs/myassets/img/google_cloud/22.png)



Y accedemos a localhost:8080

![](/PePs/myassets/img/google_cloud/23.png)



#### Creación del archivo app.yaml

En este archivo se especifica la configuración para el entorno de ejecución del servicio App Engine.

Dentro del directorio de nuestro proyecto creamos un archivo con el nombre app.yaml y añadimos el siguiente contenido:

![](/PePs/myassets/img/google_cloud/25.png)



#### Implementación del servicio web

Dentro del directorio de nuestro proyecto ejecutamos el siguiente comando en el terminal:

![](/PePs/myassets/img/google_cloud/27.png)



#### Como ver el servicio

Para iniciar el navegador y acceder al servicio web con rapicez usamos este comando:

![](/PePs/myassets/img/google_cloud/29.png)



Y accedemos al navegador con la URL que proporciona:

![](/PePs/myassets/img/google_cloud/30.png)



#### Actualizar el servicio web

Vamos a crear un formulario para que un usuario pueda enviar datos a nuestro servidor. Para ello dentro de la carpeta del proyecto creamos otra carpeta llamda views, en la cual almacenaremos los archivos HTML. 

Creamos un formulario llamado form.html con el siguiente código:

![](/PePs/myassets/img/google_cloud/32.png)



Mediante este formulario, el usuario podrá enviar su nombre y un mensaje al servidor.



Instalamos la dependencia body-parser para poder leer los datos que se envian en la solicitud

![](/PePs/myassets/img/google_cloud/34.png)

Modificamos el archivo server.js para que muestre el formulario cuando el usuario navegue y añadimos la dependecia que hemos instalado en el paso anterior: 

![](/PePs/myassets/img/google_cloud/35.png)



#### Realizar pruebas del formulario de manera local

Iniciamos el servidor Node.js:

![](/PePs/myassets/img/google_cloud/22.png)



Y comprobamos que funciona accediendo a http://localhost:8080/submit

![](/PePs/myassets/img/google_cloud/36.png)



#### Implemetar cambios

Desde la carpeta principal del proyecto ejecutamos el siguiente comando:

![](/PePs/myassets/img/google_cloud/28.png)