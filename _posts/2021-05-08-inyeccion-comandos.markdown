---
typora-copy-images-to: ../../myassets/img/mutillidae/
typora-root-url: ../../
layout: post

---

Vamos a realizar un *reverse shell* mediante inyección de comandos desde un campo de texto de un formulario.



Para ello nos vamos a descargar una plantilla de [esta dirección](https://raw.githubusercontent.com/pentestmonkey/php-reverse-shell/master/php-reverse-shell.php) y la gurardaremos como *shell.php*

Lo editamos y cambiamos la dirección IP por la que tenemos en el equipo.

![](/PePs/myassets/img/mutillidae/5.png)



Después vamos a codificarlo en https://www.base64encode.org/

Con este código vamos a crear un fichero  dentro de la máquina a la que vamos a atacar con el contenido con el que hemos codificado.

Para ello utlizaremos la siguiente instrucción:



```bash
127.0.0.1; echo "codigo_que_hemos_codificado" > shell.txt


```

![](/PePs/myassets/img/mutillidae/1.png)



Una vez creado lo descodificamos y lo guardamos como fichero .php con la siguiente instrucción:

```bash
127.0.0.1; cat shell.txt | base64 -d > shell.php


```

![](/PePs/myassets/img/mutillidae/2.png)



Realizamos al conexión mediante netcad

![](/PePs/myassets/img/mutillidae/4.png)





