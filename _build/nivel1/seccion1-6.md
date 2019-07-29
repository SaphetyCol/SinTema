---
title: 'Definición de funciones'
prev_page:
  url: /nivel1/seccion1-5
  title: 'Funciones'
next_page:
  url: /nivel1/seccion1-7
  title: 'Lógica vs. Interacción'
comment: "***PROGRAMMATICALLY GENERATED, DO NOT EDIT. SEE ORIGINAL FILES IN /content***"
---
Versión borrador / preliminar |
-------------------|
Este documento es una versión preliminar para uso interno. Si encuentra algún problema o error, o si tiene algún comentario por favor repórtelo a los autores|


# Definición de funciones

En la sección anterior definimos el concepto de función y lo ilustramos con varias funciones básicas del lenguaje Python. Como parte de esto, también se mostraron varios ejemplos de invocaciones a estas funciones y se presentaron las principales reglas para la evaluación de funciones. Esta sección completa la discusión sobre funciones en Python explicando cómo se pueden definir nuevas funciones.

Para empezar, presentamos un programa completo que al final de esta sección usted debería ser capaz de explicar y reconstruir. Léalo con cuidado, teniendo en que cuenta que cuando se habla de "una casa" se hace referencia a un dibujo como el siguiente:

![](./images/casita.png)

```python
def area_cuadrado(lado: int)-> int:
    """
       Calcula el área de un cuadrado dada la medida de su lado
    """
    return lado * lado


def area_triangulo(base: int, altura: int)-> float:
    """
        Calcula el área de un triángulo dada la medida de la base y de la altura.
    """   
    return (base * altura) / 2


def area_casa(frente: int, techo: int)-> float:
    """
        Calcula el área del dibujo de una casa que se forma con un cuadrado
        y un triángulo encima (el techo).
        El frente de la casa será igual al lado del cuadrado y a la base del triángulo.
        La altura del techo será la altura del triángulo.
    """
    cuadrado = area_cuadrado(frente)
    triangulo = area_triangulo(frente, techo)
    return cuadrado + triangulo
    
medida_frente = 7
medida_techo = 5
resultado = area_casa(medida_frente, medida_techo)
print("El área de una casa con", medida_frente, "metros de frente y un techo de",
       medida_techo, "metros de alto es ", round(resultado, 2), "metros")
```

Como siempre, no se preocupe si hay cosas en el programa anterior que no haya entendido: todo se irá aclarando a lo largo de la sección.


## Definición de funciones en Python

En la sección anterior vimos que Python incluye varias funciones que nosotros podemos utilizar aunque no sepamos cuáles sean exactamente las instrucciones que ejecuta cada una. Lo que conocemos nosotros de esas funciones es lo que llamamos *signatura*, la cual incluye el nombre, los parámetros que espera y su retorno. Lo que desconocemos es el *cuerpo* o *implementación* de las funciones, es decir las instrucciones que hacen que la función cumpla con lo que se espera de ella.

### La signatura de una función

La signatura de una función puede verse como la especificación de las reglas para utilizar la función y está compuesta por tres cosas:

1. **El nombre**. Este debería ser un nombre claro y fácil de recordar. Además no debería estar repetido para que no haya ambigüedad cuando se quiera invocar a la función.

2. **Los parámetros**. Estos son los valores que se le tienen que pasar a la función cuando se quiera invocar. Pueden verse como la información que tiene que proporcionar quien llame a la función para que se pueda cumplir con su objetivo. Una función puede tener uno o varios parámetros.

3. **El resultado**. En tercer lugar tenemos información sobre el resultado de la función que nos dice si será un número, una cadena de caracteres o cualquier otra cosa.

Volvamos ahora al ejemplo para identificar estos elementos:

```python
def area_cuadrado(lado: int)-> int:
    """
       Calcula el área de un cuadrado dada la medida de su lado
    """
    return lado * lado
```

En este ejemplo, se está definiendo una función y se ha incluido tanto la signatura como el cuerpo. Por ahora vamos a analizar sólo la signatura, que en este caso corresponde a la primera línea del ejemplo. 

Lo primero que nos encontramos es la palabra reservada[^reservada] de Python ```def``` que nos marca el inicio de la definición de una función. La signatura de la función va hasta los dos puntos (```:```) que se encuentran al final de la línea.

Después de la palabra ```def```, viene el nombre que le queremos dar a la función. En este caso escogimos ```area_cuadrado``` para expresar claramente su objetivo: será una función para calcular el área de un cuadrado. Como los nombres de las funciones no pueden tener espacios, hemos separado las dos palabras usando el símbolo ```_```[^estilo]. 

El siguiente punto es la definición de los parámetros de la función, así que deberíamos hacernos la pregunta: ¿si queremos calcular el área de un cuadrado, qué información requerimos para poder hacer el cálculo? En este caso la respuesta es que sólo necesitamos la medida del lado del cuadrado. Es decir que necesitamos un parámetro en la función y que ese parámetro debería representar la longitud del lado del cuadrado. 

En nuestro ejemplo, el parámetro está especificado en la parte que dice ```lado: int```. Esto significa que la función esperará un solo parámetro, que nos vamos a referir a ese parámetro como ```lado```, y que ese parámetro debería ser un número entero (```int```). Los parámetros siempre se especifican dentro de un par de paréntesis.

Finalmente encontramos la especificación del resultado de la función. En nuestro ejemplo, la signatura especifica que su resultado será un número entero con el fragmento que dice ```-> int```.

En resumen: la signatura de una función especifica cómo se debería invocar la funcón y qué se debería esperar como resultado. En nuestro caso de ejemplo, la función se invocará con el nombre ```area_cuadrado```, requerirá que se use un parámetro de tipo ```int``` y generará como resultado otro número entero (```int```).

[^reservada]: Una palabra reservada significa que es una palabra que nosotros no podemos usar en nuestros programas para nuestros identificadores. Por ejemplo, no podemos tener ni una función ni una variable que se llamen ```def```. Python tiene varias palabras reservadas que iremos descubriendo, como return, del, import, pass, y raise, entre otras.

[^estilo]: La regla que acabamos de ilustrar (separar palabras usando el símbolo ```_```) no es una regla sintáctica del lenguaje, sino es una regla de *estilo*. Es decir, nosotros podríamos haber llamado a la función ```areaCuadrado``` y el programa habría funcionado igual, pero no habría respetado las reglas de estilo que sirven para hacer los programas más legibles y consistentes. Si usted ha utilizado algún otro lenguaje de programación, es posible que el estilo al que esté acostumbrado le sugiera usar nombres como ```areaCuadrado``` o ```AreaCuadrado```.

#### Un segundo ejemplo

Analizemos ahora la segunda función de nuestro ejemplo: 

```python
def area_triangulo(base: int, altura: int)-> float:
    """
        Calcula el área de un triángulo dada la medida de la base y de la altura.
    """   
    return (base * altura) / 2
```

¿Qué nos dice la signatura con respecto a la función?

  * ¿Cómo se llama la función?
  * ¿Cuántos parámetros se requieren para su invocación?
  * ¿De qué tipo son los parámetros?
  * ¿De qué tipo será el resultado de la función?

Lo único diferente con respecto al primer ejemplo es que tenemos dos parámetros en lugar de uno y que esos dos parámetros se separaron utilizando una coma.


### El cuerpo de una función

Pasamos ahora a estudiar el cuerpo de la primera función y lo primero que debemos notar es que todo el cuerpo está **indentado**. Esto quiere decir, que todo lo que hace parte del cuerpo de la función está escrito con un margen hacia la derecha. En este ejemplo particular el margen se ha creado usando 4 caracteres en blanco, lo cual corresponde a las buenas prácticas recomendadas de la comunidad Python.

```python
def area_cuadrado(lado: int)-> int:
    """
       Calcula el área de un cuadrado dada la medida de su lado
    """
    return lado * lado
```

<div class="cuidado">
La indentación no es opcional en Python, sino obligatoria. El cuerpo de todas las funciones tiene que estar indentado y el margen utilizado debe ser consistente: si una línea usa un cierto margen y la siguiente tiene más o menos caracteres, se producirá un error. La recomendación en este libro será siempre utilizar 4 caracteres en blanco para la indentación.
</div>

Las primeras líneas del cuerpo de esta función nos muestran otra forma de introducir comentarios en un programa, esta vez asociados a una función. En Python, si la primera línea del cuerpo de una función inicia con una cadena de caracteres, esa cadena se convertirá en la documentación asociada a la función y aparecerá cuando alguien llame a la función ```help``` usando el nombre de nuestra función. 

En general, siempre debería incluirse documentación en las funciones, por más sencillas y evidentes que sean. En este ejemplo se ha incluido sólo una documentación breve para la función ```area_cuadrado```, pero para casos más complejos habría sido conveniente documentar también los parámetros y el retorno de la función. Más adelante estudiaremos algunas buenas prácticas para completar la documentación de las funciones.

Además de la documentación, el cuerpo de la función ```area_cuadrado``` sólo tiene una instrucción: 

```python
    return lado * lado
```

La interpretación de esta instrucción es muy sencilla: cuando se ejecute esta instrucción, la función deberá *retornar* el valor de la expresión ```lado * lado```. En el contexto de la ejecución de una función, retornar hace referencia a responderle con un valor a quien haya invocado la función. Esto quiere decir que cuando se llega a una instrucción ```return```, la ejecución de la función termina y se responde con un valor de acuerdo a lo especificado en la signatura de la función.

Ahora bien, antes de retornar un valor, es necesario que Python evalue la expresión ```lado * lado``` y encuentre a qué valor equivale. Si no tuviéramos contexto, lo que podríamos suponer es que ```lado``` fuera el nombre de una variable y que la expresión está calculando el cuadrado de la variable. En realidad, no hemos definido ninguna variable con ese nombre, pero sí tenemos un *parámetro* con ese nombre en la signatura de la función. La expresión ```lado * lado``` está haciendo entonces referencia al parámetro que le pasen a la función cada vez que la invoquen.

Viendo todo en conjunto, lo que pasará cuando alguien invoque a nuestra función es lo siguiente:

1. El que invoque la función, tendrá que darle un valor al parámetro lado. La invocación podría ser algo como ```area_cuadrado(4)```.
2. Nuestra función intentará ejecutar la instrucción ```return lado * lado```. Como la parte derecha es una expresión cuyo valor se desconoce, se tendrá que evaluar primero.
3. Para evaluar la expresión ```lado * lado``` se debe conocer el valor de ```lado```. Como es un parámetro, entonces se tomará el valor que se le haya dado cuando se invocó a la función. En este caso, la expresión se convertiría en ```4 * 4```.
4. Como la expresión sigue sin tener un valor, se ejecuta la operación de multiplicación y la expresión se convierte en el valor ```16```.
5. Se ejecutará la instrucción ```return 16```: terminará la ejecución de la función y el valor 16 se le pasará al que haya invocado la función.


#### Un segundo ejemplo

Analizemos ahora la segunda función de nuestro ejemplo: 

```python
def area_triangulo(base: int, altura: int)-> float:
    """
        Calcula el área de un triángulo dada la medida de la base y de la altura.
    """   
    return (base * altura) / 2
```

* ¿Qué hace el cuerpo de esta función? 
* ¿Qué diferencias tiene con respecto al cuerpo de la primera función?


## Definir vs. Invocar

Hasta el momento hemos descrito en detalle solamente la forma en la que se define una función, pero no hemos estudiado cómo se invoca una función. Es muy importante tener muy clara la diferencia entre estas dos acciones: cuando definimos una función, sólo le estamos *enseñando* a Python cómo debería invocarse esa función y cómo debería comportarse un programa cuando la función se invoque; cuando invocamos una función, le estamos pidiendo a Python que *ejecute* el cuerpo de la función, dándole valores específicos para cada uno de sus parámetros.

nombres de parámetros vs. argumentos

llamar funciones desde funciones

usar funciones en los argumentos de invocaciones

Variables locales

Orden de ejecución?

```python
def area_casa(frente: int, techo: int)-> float:
    """
        Calcula el área del dibujo de una casa que se forma con un cuadrado
        y un triángulo encima (el techo).
        El frente de la casa será igual al lado del cuadrado y a la base del triángulo.
        La altura del techo será la altura del triángulo.
    """
    cuadrado = area_cuadrado(frente)
    triangulo = area_triangulo(frente, techo)
    return cuadrado + triangulo
```



## Funciones sin parámetro o sin retorno

Dos preguntas frecuentes entre los estudiantes son si una función siempre debe tener parámetros y si una función siempre debe retornar un valor. Si estas preguntas se hicieran en un contexto matemático, la respuesta sería negativa: las funciones establecen relaciones entre elementos de un conjunto y elementos de otro conjunto, así que siempre tienen al menos un parámetros y siempre tienen un resultado.

En el contexto de Python, sí es posible tener funciones sin parámetros y funciones que no tengan un retorno, pero la realidad es que este tipo de funciones sólo deberían usarse en un contexto muy particular (interacción con el usuario). A continuación explicamos brevemente por qué, en general, no es una buena idea tener este tipo de funciones.

### Funciones sin parámetros

Si una función no tiene parámetros, en principio siempre va a retornar el mismo valor. Si esto fuera cierto, en lugar de tener una función para calcular el valor, se debería tener una variable donde ese valor estuviera disponible para utilizarlo cuando fuera necesario. 

Python incluye algo así para almacenar el valor de Pi sin que sea necesario llamar cada vez a una función que lo calcule.

Hay 3 casos relativamente sencillos en los cuales tendría sentido tener funciones sin parámetros:

1. Cuando los datos para calcular el resultado de la función dependan de valores entregados por el usuario. En ese caso, aunque no se vería en la signatura, la función recibiría valores que cambiarían su resultado en cada ejecución.

2. Cuando el resultado de la función pueda cambiar con el paso del tiempo. Por ejemplo, una función que calculara un valor aleatorio podría no requerir ningún parámetro para cambiar el valor que retorne cada vez.

3. Cuando la función dependa de valores externos a ella, pero que no tengan que llegar por parámetro. Por ejemplo, una función podría depender de una variable global o de una condición del ambiente de ejecución, como la hora o la ruta desde la que se esté corriendo el programa.

### Funciones sin retorno

Si una función no tiene un retorno significa que el resultado de ejecutar sus instrucciones no es interesante para el resto del programa, o es interesante sólo por los efectos que haya podido tener en algún otro elemento del programa o del computador. Por ejemplo, una función sin retorno podría utilizarse para eliminar un archivo: la función eliminaría el archivo y no retornaría ningún valor.

En general, las funciones podrían no tener retorno cuando representen acciones que quieren realizarse y no tengan ningún resultado que informar.



## Sobre los *type-hints*

Si usted utiliza otros libros o si consulta en Internet, es muy posible que se encuentre con definiciones de funciones en las que no aparecen los tipos de los parámetros ni el tipo de los resultados. Esto se debe a que en Python el uso de estos elementos es opcional. De hecho, el nombre específico de estos elementos es *type-hints* y las herramientas (IDE, intérprete, compilador, etc.) los utilizan sólo como sugerencias.

En este libro vamos a usar *type-hints* en la definición de todas las funciones y esperamos que usted haga uso de ellos también. Por una parte, esto le facilitará aprender a usar otros lenguajes de programación como C, C++, Java, o TypeScript. Por otro lado, razonar sobre los tipos de datos debería ayudarlo a estructurar mejor sus programas, especialmente mientras adquiere una cierta destreza programando.


## Ejercicios

1. 


## Más allá de Python

Contexto de ejecución: sólo los parámetros

Tipos de parámetros y funciones - dynamic typing vs. strong typing

Camel Case



#### Notas 