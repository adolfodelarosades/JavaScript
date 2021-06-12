# 5. Looping with for, While, and Do...While!

* The for Loop
* Some for Loop Examples
* The Other Loops


5. Hacer un bucle con for, While y Do ... While!
En este capítulo

• Aprenda a ejecutar código repetidamente

• Trabajar con bucles for, while y do ... while

Cuando esté codificando algo, habrá ocasiones en las que desee repetir una acción o ejecutar un código varias veces. Por ejemplo, digamos que tenemos una función llamada saySomething que queremos llamar repetidamente 10 veces.

Una forma en que podríamos hacer esto es simplemente llamando a la función 10 veces usando copiar y pegar:

Haga clic aquí para ver la imagen del código

Di algo();
Di algo();
Di algo();
Di algo();
Di algo();
Di algo();
Di algo();
Di algo();
Di algo();
Di algo();
Esto funciona y logra lo que nos propusimos hacer, pero ... no deberíamos hacer algo como esto. Después de todo, duplicar código nunca es una buena idea. Si tuviéramos una moneda de cinco centavos por cada vez que lee eso aquí, tendríamos unas cuatro o cinco monedas de cinco centavos. #matandolo

Ahora, incluso si decidimos duplicar un código varias veces manualmente, este enfoque no funciona realmente en la práctica. La cantidad de veces que necesitaremos duplicar nuestro código variará en función de algunos factores externos, como la cantidad de elementos en una colección de datos, algunos resultados de algún servicio web, la cantidad de letras en una palabra y varias otras cosas que seguirá cambiando. No siempre será un número fijo como 10. A menudo, la cantidad de veces que queremos repetir un código puede ser MUY MUY grande. No queremos copiar y pegar algo unos cientos o miles de veces para repetir algo. Sería terrible.

Lo que necesitamos es una solución genérica para repetir código con control sobre cuántas veces se repite el código. En JavaScript, esta solución se proporciona en forma de algo conocido como bucle. Hay tres tipos de bucles que podemos usar para repetir algún código:

para bucles

while bucles

hacer ... bucles while

Cada una de estas tres variaciones de bucle nos permite especificar el código que queremos repetir (también conocido como bucle) y una forma de detener la repetición cuando se cumple una condición. En las siguientes secciones, aprenderemos todo sobre ellos.

¡Adelante!

Nota de imagen

¡Algo más allá de la alerta!

Hemos estado usando la función de alerta estos últimos capítulos para que nuestro código muestre algo en la pantalla. En este capítulo, veremos una forma más de mostrar algo en la pantalla que es un poco menos intrusivo. Vamos a utilizar la función document.write:

Haga clic aquí para ver la imagen del código

document.write ("¡Mostrar esto en la pantalla!");
Esta función imprimirá el texto que proporcione en la página que se muestra en su navegador sin mostrar un cuadro de diálogo que requiera que lo cierre cada vez que aparezca. Verá por qué queremos algo que sea más liviano cuando aprenda más sobre los bucles y cómo es posible que deseemos imprimir muchas cosas en la pantalla.

EL FOR LOOP
Una de las formas más comunes de crear un bucle es utilizar la instrucción for para crear un bucle for. Un bucle for nos permite ejecutar repetidamente algún código hasta que una expresión que especifiquemos devuelva falso. Para ayudar a aclarar esta definición, veamos un ejemplo.

Si tuviéramos que traducir nuestro ejemplo anterior de saySomething usando for, se vería de la siguiente manera:

Haga clic aquí para ver la imagen del código

para (sea i = 0; i <10; i ++) {
  Di algo();
}

function saySomething () {
  document.writeln ("¡hola!");
}
Si desea seguir más activamente y ver este código por sí mismo, ingrese este código dentro de algunas etiquetas de secuencia de comandos en un documento HTML:

Haga clic aquí para ver la imagen del código

<! DOCTYPE html>
<html>

<cabeza>
  <meta charset = "utf-8">
  <title> ¡Bucles! </title>

  <estilo>

  </style>
</head>

<cuerpo>
  <script>
    para (sea i = 0; i <10; i ++) {
      Di algo();
    }

    function saySomething () {
      document.writeln ("¡hola!");
    }
  </script>
</body>

</html>
Una vez que su documento esté listo, guárdelo y obtenga una vista previa en su navegador. Una vez que se haya cargado la página, lo que verá se muestra en la Figura 5.1.

Imagen
FIGURA 5.1

¡Hola! se repite a lo largo de la página.

¡La palabra hola! se repetirá diez veces en su página. Esto es posible gracias al bucle for, por lo que se lo agradeceremos aprendiendo todo sobre cómo funciona. Primero, aquí está nuestra estrella:

Haga clic aquí para ver la imagen del código

para (sea i = 0; i <10; i ++) {
  Di algo();
}
Este es un bucle for. Probablemente se vea muy diferente de otras declaraciones que hemos visto hasta ahora, y eso se debe a que ... bueno, es muy diferente. Para comprender las diferencias, generalicemos un bucle for en la forma que se muestra en la Figura 5.2.

Imagen
FIGURA 5.2

General, alto nivel para bucle.

Esta vista de alto nivel corresponde a los valores reales de nuestro ejemplo (Figura 5.3).

Imagen
FIGURA 5.3

Los valores reales.

Cada una de estas tres regiones de diferentes colores juega un papel muy importante en el funcionamiento de su bucle. Para usar bien un bucle for, debemos saber qué logra cada región, por lo que pasaremos los próximos minutos profundizando en cada sección.

El punto de partida
En la primera región, definimos el punto de inicio de nuestro ciclo. Una cosa común a pue aquí hay un código para declarar e inicializar una variable, similar a lo que hicimos en la Figura 5.4.

Imagen
FIGURA 5.4

Declarar e inicializar una variable i.

Lo que le estamos diciendo a JavaScript es que comience nuestro ciclo con la variable i inicializada a 0.

El paso
Vamos a saltar a la siguiente región de pasos (Figura 5.5).

Imagen
FIGURA 5.5

El paso.

En esta etapa, especificamos cómo evolucionará nuestro punto de partida. Para nuestro ejemplo, lo que estamos diciendo es que cada vez que se ejecuta nuestro bucle, el valor de i aumentará en 1. Eso es capturado por el críptico i ++. Cubriremos lo que significa ++ más adelante cuando veamos cómo funcionan los números y las matemáticas en JavaScript, pero otra forma de representar esto sería decir i = i + 1.

La condición (también conocida como cuánto tiempo seguir repitiendo)
Volviendo a la etapa que saltamos, tenemos la parte de condición de nuestro ciclo que determina cuándo dejará de funcionar el ciclo (Figura 5.6).

Imagen
FIGURA 5.6

La condición que forma parte del bucle.

En nuestro ejemplo, la condición es que nuestra variable i sea menor que el valor de 10:

Si nuestra variable i es menor que 10, esta expresión se evalúa como verdadera y nuestro ciclo continúa ejecutándose.

Si nuestra variable i se vuelve igual o mayor que 10, la condición es falsa y nuestro ciclo termina.

Poniendolo todo junto
Bien, ahora que hemos examinado cada parte de nuestro ciclo for con mayor detalle, usemos nuestro conocimiento recién adquirido para recorrerlo todo a la vez y ver qué está sucediendo. Nuestro ejemplo completo, repetido desde antes, es el siguiente:

Haga clic aquí para ver la imagen del código

para (sea i = 0; i <10; i ++) {
  Di algo();
}

function saySomething () {
  document.writeln ("¡hola!");
}
Cuando nuestro bucle for se golpea inicialmente en el punto de inicio, la variable i se crea y se inicializa a 0. A continuación, vamos a la parte de condición del bucle que determina si nuestro bucle debe seguir ejecutándose o no. La condición comprueba si el valor de i es menor que 10. ¿Es 0 menor que 10? Sí, así que esta condición se evalúa como verdadera y se ejecuta el código contenido dentro del bucle. Una vez hecho esto, comienza la parte del paso de nuestro ciclo. En esta etapa, la variable i se incrementa en 1 para tener un valor de 1. En este punto, nuestro ciclo ha pasado por un ciclo, comúnmente conocido como iteración. . Es hora de comenzar la siguiente iteración.

Para la siguiente iteración, el ciclo comienza de nuevo, excepto que la variable i no se reinicializa. Su valor es 1 de la iteración anterior, por lo que se transfiere. Para la condición, volvemos a verificar si el nuevo valor de 1 es menor que 10 ... que es. El código dentro de nuestro bucle (básicamente la función saySomething) y la parte del paso del bucle donde i se incrementa en 1 suceden. El valor de i se incrementa luego en 1 hasta un valor de 2, y esta iteración se realiza para el día ... ¡dejando la puerta abierta para la siguiente iteración!

Este proceso repite iteración tras iteración hasta que la condición i <10 se evalúa como falsa. Dado que comenzamos el ciclo con i siendo 0, el ciclo está configurado para terminar cuando el valor de i es menor que 10, e i se incrementa en 1 en cada iteración, este ciclo (y cualquier código contenido en él) se ejecutará 10 veces antes parada. ¡Uf!

ALGUNOS PARA EJEMPLOS DE BUCLE
En la sección anterior, diseccionamos un bucle for simple y etiquetamos todo su funcionamiento interno. Lo que pasa con los bucles for y casi todo en JavaScript es que un ejemplo simple no siempre cubre todo lo que podríamos necesitar. La mejor solución es mirar algunos ejemplos más de bucles for, y eso es lo que vamos a hacer en las próximas secciones.

Romper un bucle
A veces, es posible que deseemos finalizar nuestro ciclo antes de que se complete. La forma en que terminamos un ciclo es usando la palabra clave break. A continuación se muestra un ejemplo:

Haga clic aquí para ver la imagen del código

para (sea i = 0; i <100; i ++) {
  document.writeln (i);

  si (i == 45) {
    rotura;
  }
}
Cuando el valor de i es igual a 45, la palabra clave break evita que el bucle continúe. Si bien este ejemplo fue un poco artificial, cuando nos encontramos con un caso del mundo real para terminar nuestro ciclo, ahora sabemos qué hacer.

Omitir una iteración
Habrá momentos en los que queramos que nuestro bucle omita su iteración actual y pase a la siguiente. Eso se maneja inteligentemente con la palabra clave continue:

Haga clic aquí para ver la imagen del código

dejar pisos = 28;

para (sea i = 1; i <= pisos; i ++) {
  si (i == 13) {
    // no hay piso aquí
    Seguir;
  }

  document.writeln ("En el piso:" + i + "<br>");
}
A diferencia de break donde nuestro bucle simplemente se detiene y vuelve a casa, continue le dice a nuestro bucle que se detenga y pase a la siguiente iteración. A menudo nos encontraremos usando continue cuando manejamos errores en los que solo queremos que el ciclo pase al siguiente elemento.

Yendo al revés
No hay ninguna razón por la que nuestro punto de partida tenga que tener una variable inicializada a 0 y luego incrementar esa variable hacia arriba:

Haga clic aquí para ver la imagen del código

para (sea i = 25; i> 0; i--) {
  document.writeln ("hola");
}
Con la misma facilidad, puede comenzar alto y luego disminuir hasta que su condición de bucle devuelva un falso.

Es posible que haya escuchado que hacer algo como esto increafirma el rendimiento de su bucle. El jurado aún está deliberando sobre si disminuir es en realidad más rápido que aumentar, pero siéntase libre de experimentar y ver si nota algún beneficio en el rendimiento.

No tienes que usar números
Al completar su bucle for, no tiene que usar solo números:

Haga clic aquí para ver la imagen del código

para (sea i = "a"; i! = "aaaaaaaa"; i + = "a") {
  document.writeln ("hmm ...");
}
Puede usar lo que quiera siempre que su bucle llegue a un punto en el que pueda terminar. Observe que en este ejemplo estamos usando la letra a como nuestra moneda para ejecutar este ciclo. En cada iteración, el valor de i se incrementa con la letra a, y el ciclo se detiene cuando i es igual a aaaaaaaa.

¡Oh, no, no lo hizo!
¡Oh si! Sí, lo hice. Fui allí, tomé una foto, publiqué en Facebook y regresé:

Haga clic aquí para ver la imagen del código

sea ​​i = 0;
deje yay = verdadero;

para (; yay;) {
  si (i == 10) {
    yay = falso;
  } demás {
    i ++;
    document.writeln ("raro");
  }
}
No es necesario que complete las tres secciones de su bucle for para que funcione. Siempre que, al final, logres satisfacer la condición de terminación del bucle, puedes hacer lo que quieras ... tal como muestra el ejemplo anterior.

LOS OTROS LAZOS
Vivir a la sombra del amado bucle for son las variantes while y do ... while loop. En aras de la integridad, veamos rápidamente ambos.

El bucle while
El ciclo while repite algún código hasta que su condición (otra expresión) devuelve falso. Eche un vistazo al siguiente ejemplo:

Haga clic aquí para ver la imagen del código

dejar contar = 0;

while (cuenta <10) {
  document.writeln ("¡repitiendo!");

  contar ++;
}
En este ejemplo, la condición está representada por la expresión count <10. Con cada iteración, nuestro ciclo incrementa el valor de conteo en 1:

Haga clic aquí para ver la imagen del código

dejar contar = 0;

while (cuenta <10) {
  document.writeln ("¡repitiendo!");

  contar ++;
}
Una vez que el valor de count se convierte en 10, el ciclo se detiene porque la expresión count <10 devolverá falso. Si observa todo lo que hace el bucle while, parece una gran imitación del bucle for. Mientras que el bucle for requería formalmente que definiera las etapas de inicio, condición y paso, el bucle while espera que usted mismo defina esas etapas a su manera.

El do ... while Loop
Ahora, llegamos al Meg Griffin de las variantes de bucle. Ese sería el bucle do ... while cuyo propósito está aún menos definido que while. Donde el bucle while tenía su expresión condicional primero antes de que se ejecutara, el bucle do ... while tiene su expresión condicional al final.

Aquí hay un ejemplo:

Haga clic aquí para ver la imagen del código

dejar contar = 0;

hacer {
    document.writeln ("¡No sé qué estoy haciendo aquí! <br>");


    contar ++;
} while (cuenta <10);
La principal diferencia entre un bucle while y un bucle do ... while es que el contenido de un bucle while nunca podría ejecutarse si su expresión condicional es falsa desde el principio:

Haga clic aquí para ver la imagen del código

while (falso) {
  document.writeln ("¡No puedo tocar esto!");
}
Con un bucle do ... while, debido a que la expresión condicional se evalúa solo después de una iteración, se garantiza que el contenido de su bucle se ejecutará al menos una vez:

Haga clic aquí para ver la imagen del código

hacer {
  document.writeln ("¡Este código se ejecutará una vez!");
} while (falso);
Eso puede resultar útil en algunas situaciones. Ahora, antes de que terminemos, hay un último dato que debo contarte antes de seguir adelante. Las declaraciones break y continue que vimos anteriormente como parte del increíble bucle for también funcionan de manera similar cuando se usan dentro de las variantes while y do ... while.

El Mínimo Absoluto

Entonces, ahí lo tiene: un vistazo a los bucles for y cómo podemos usarlos junto con una cobertura muy básica de los bucles while y do ... while. En este momento, es posible que no nos veamos usando mucho los bucles. A medida que comencemos a involucrarnos en situaciones más complicadas que involucran colecciones de datos, elementos en su DOM, manipulación de texto y otras cosas, usaremos bucles mucho más. Básicamente ... ¡mantén toda la información que hemos visto aquí muy cerca!

Si tiene alguna pregunta sobre el contenido aquí, ¡no se quede atascado! Publique en los foros en https://forum.kirupa.com ayuda realmente rápida tanto de mí como de algunos de los desarrolladores más inteligentes y amigables de la web.
