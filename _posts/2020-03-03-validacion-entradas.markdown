---
typora-copy-images-to: ../../myassets/img/validacion/
typora-root-url: ../../
layout: post
---

## **XSS (Cross-site-scripting)**

Creamos un formulario en php, (*post.php*), el cual nos permitirá introducir entradas de posts.

![](/PePs/myassets/img/validacion/1003.png)



Comprobamos que se visualiza correctamente:

![](/PePs/myassets/img/validacion/1004.png)



Si se introduce en la caja de texto un script como el siguiente, al mandar el post aparecerá una alerta como la siguiente:

```
<script>alert('hackeado')</script>
```



![](/PePs/myassets/img/validacion/1005.png)



## **Mitigación XSS**

##### En el servidor

Para evitar que esto ocurra, crearemos un nuevo fichero php con el nombre *post_mejorado.php* en el que añadiremos mejoras para escapar los caracteres peligrosos.

![](/PePs/myassets/img/validacion/1006.png)



Ahora si se introduce el script anterior, una vez se manda no interpreta las etiquetas de script y las muestra como texto plano:

![](/PePs/myassets/img/validacion/1007.png)



##### En el cliente

Para evitarlo, se ha de controlar que los datos insertados se traten como string y no como DOM; para ello añadiremos las siguientes lineas:

![](/PePs/myassets/img/validacion/999.png)



Además, conviene habilitar el CSP (Content-Security-Policy). Si se quieren restringir la ejecución de scripts que sean del mismo dominio de origen se añadirá la siguiente linea:

![](/PePs/myassets/img/validacion/1000.png)



Si se quiere permitir el contenido de un dominio de confianza y todos sus subdominios se agregará la siguiente:

![](/PePs/myassets/img/validacion/1001.png)



## **Autenticación con Sesiones**

Creamos un fichero *login.php* para crear un formulario de inicio de sesión. Introducimos en su interior el siguiente código:

![](/PePs/myassets/img/validacion/4.png)



Para poder desconectar el usuario, creamos otro fichero con el nombre *logout.php* con este contenido:

![](/PePs/myassets/img/validacion/3.png)





## **Robo de sesión - Puesta en práctica**

Creamos un contenedor en Docker y en su interior creamos un host virtual en apache para el dominio evil. 

Creamos una página llamada robo-de-sesion.php con este contenido:

![](/PePs/myassets/img/validacion/1008.png)



En otro conetenedor de Docker creamos otro host virtual para el sitio atacado. Creamos la página hackeada.html con este contenido:

![](/PePs/myassets/img/validacion/1009.png)



Para que funcione accedemos a login.php y luego a hackeada.html

![](/PePs/myassets/img/validacion/5.png)



![](/PePs/myassets/img/validacion/6.png)



Modificamos el valor de PHPSESSID y si entramos en la pestaña de Respuesta se puede observar como ha sido suplantada la identidad:

![](/PePs/myassets/img/validacion/7.png)



![](/PePs/myassets/img/validacion/9.png)



## **Evitar el robo de sesión (Session-Hijacking)**

Para evitar que el robo suceda añadimos en *login.php* la siguiente directiva.

![](/PePs/myassets/img/validacion/1010.png)



## **Fijación de sesión (Session Fixation)**

Modificamos el fichero *login.php* para que quede de la siguiente manera:

![](/PePs/myassets/img/validacion/10.png)



Si iniciamos sesión con el valor de la cookie en HOLA y luego desde un navegador en incógnito accedemos de nuevo a la sesión se puede observar como la cookie HOLA se mantiene y por lo tanto la sesión ha sido robada:

![](/PePs/myassets/img/validacion/81.png)



![](/PePs/myassets/img/validacion/82.png)



![](/PePs/myassets/img/validacion/83.png)



## **Control de acceso (Autorización)**

Modificamos el fichero login.php para que cada usuario solo pueda accedera a los recursos que se le especifique:

![](/PePs/myassets/img/validacion/90.png)



Creamos una página *perfil.php* para que el usuario normal pueda aceder:

![](/PePs/myassets/img/validacion/91.png)



Creamos otra página a la cual solo tendrá acceso el administrador. Se llamará *admin.php*

![](/PePs/myassets/img/validacion/92.png)



Y otra página para los accesos no autorizados:

![](/PePs/myassets/img/validacion/93.png)



Si accedemos con el usuario con privilegios de administrador, podermos acceder a *admin.php* pero no a *perfil.php*

![](/PePs/myassets/img/validacion/95.png)

![](/PePs/myassets/img/validacion/94.png)



Si accedemos con el usuario con privilegios normales podremos acceder a *perfil.php* pero no a *admin.php*

![](/PePs/myassets/img/validacion/97.png)



![](/PePs/myassets/img/validacion/98.png)



![](/PePs/myassets/img/validacion/99.png)





## **CSRF (Cross Site Request Forgery)**

Creamos una página con el nombre *transfer.php*

![](/PePs/myassets/img/validacion/100.png)



Y otra página llamada *hackeada-csrf.html*

![](/PePs/myassets/img/validacion/101.png)



Para realizar el ataque, hacemos login con el usuario mario y depués accedemos a *hackeada-csrf.html*

![](/PePs/myassets/img/validacion/102.png)



## **Redirigir a otra web**

Creamos *hackeada-redirect.html* con el siguiente contenido:

![](/PePs/myassets/img/validacion/900.png)



Y creamos otro archivo con el nombre *clon-de-mi-banco.html*

![](/PePs/myassets/img/validacion/800.png)



Si accedemos a *hackeada-redirect.html* nos redirigirá automáticamente a *clon-de-mi-banco.html*

![](/PePs/myassets/img/validacion/902.png)