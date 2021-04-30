---
typora-copy-images-to: ../../myassets/img/zap/
typora-root-url: ../../
layout: post

---

Para realizar esta actividad utilizaremos al herramienta OWASP ZAP. 

Introducimos al URL que queremos monitorizar y accedemos a la página. En nuestro caso utilizamos DVWA.

Navegamos por las diversas pestañas para que se registre en ZAP. Accedemos a la pestaña de XSS DOM Baseed Cross Site Scripting.

En la herramienta ZAP accedemos a la cabezera GET y seleccionamos el parametro que queremos modificar. En nuestro caso el campo English.

![1](/PePs/myassets/img/zap/1.png)



Seleccionamos ingresar. Vamos a agregar un fuzzer de archivo, concretamente uno de XSS y procedemos a iniciar el *fuzzering*.

![2](/PePs/myassets/img/zap/2.png)



Una vez ha finalizado comprobamos si ha habido alguna coincidencia. En nuestro caso parece que todas las pruebas que se han lanzado són válidas.

![3](/PePs/myassets/img/zap/3.png)



Vamos a probarlo introduciendo uno de estos scripts, por ejemplo:

```java
<script>alert(document.domain)</script>
```

![20](/PePs/myassets/img/zap/20.png)