# 2. Values and Variables

* Using Variables
* More Variable Stuff

En este capítulo

• Aprenda a usar valores para almacenar datos.

• Organiza tu código con variables

• Eche un vistazo breve a las convenciones de nomenclatura de variables.

En JavaScript, se considera que cada dato que proporcionamos o usamos contiene un valor. En el ejemplo que vimos en nuestra introducción, las palabras ¡hola, mundo! podrían ser solo algunas palabras que pasamos a la función de alerta:

alert ("¡hola, mundo!");
Para JavaScript, estas palabras tienen una representación específica debajo de las cubiertas. Se consideran valores. Es posible que no hayamos pensado mucho en eso cuando escribimos esas palabras, pero cuando estamos en el país de JavaScript, cada dato que toca se considera un valor.

Ahora bien, ¿por qué es importante saber esto? Es importante porque trabajaremos mucho con valores. Trabajar con ellos de una manera que no te vuelva loco es algo bueno. Solo hay dos cosas que necesitamos para simplificar nuestra vida trabajando con valores. Necesitamos que:

Identifíquelos fácilmente

Reutilícelos en toda su aplicación sin duplicar innecesariamente el valor en sí

Esas dos cosas las proporciona aquello en lo que vamos a dedicar el resto de nuestro tiempo: las variables. Aprendamos todo sobre ellos aquí.

USANDO VARIABLES
Una variable es un identificador de un valor. En lugar de escribir hola, mundo !, cada vez que quiera usar esa frase en su aplicación, puede asignar esa frase a una variable y usar esa variable siempre que necesite usar hola, mundo! de nuevo. Esto tendrá más sentido en unos momentos, ¡lo prometo!

Hay varias formas de utilizar variables. En la mayoría de los casos, la mejor manera es confiando en la palabra clave let seguida del nombre que desea darle a su variable:

deja myText
En esta línea de código, declaramos una variable llamada myText. En este momento, nuestra variable simplemente ha sido declarada. No contiene nada de valor. Es simplemente una cáscara vacía.

Arreglemos eso inicializando nuestra variable a un valor como ... digamos ... ¡hola, mundo !:

Haga clic aquí para ver la imagen del código

let myText = "¡hola, mundo!";
En este punto, cuando se ejecute este código, nuestra variable myText tendrá el valor ¡hola, mundo! asociado a ello. Juntemos todo esto como parte de un ejemplo completo. Si todavía tiene abierto hello_world.htm desde antes, reemplace el contenido de su etiqueta de secuencia de comandos con lo siguiente ... o cree un nuevo archivo HTML y agregue el siguiente contenido en él:

Haga clic aquí para ver la imagen del código

<! DOCTYPE html>
<html>

<cabeza>
  <meta charset = "utf-8">
  <title> Aquí va un título interesante </title>

  <estilo>

  </style>
</head>

<cuerpo>
  <script>
    let myText = "¡hola, mundo!";
    alerta (miTexto);
  </script>

</body>

</html>
¡Observe que ya no estamos pasando en el hola, mundo! envíe un mensaje de texto a la función de alerta directamente. En su lugar, ahora estamos pasando el nombre de variable myText en su lugar. El resultado final es el mismo. Cuando se ejecuta este script, una alerta con ¡hola, mundo! se mostrará. Lo que este cambio nos permite hacer es tener un lugar en nuestro código donde hola, mundo! se está especificando. Si quisiéramos cambiar ¡hola mundo! to ¡El perro se comió mi tarea !, todo lo que tendríamos que hacer es hacer un cambio en la frase especificada por la variable myText:

Haga clic aquí para ver la imagen del código

let myText = "¡El perro se comió mi tarea!";
alerta (miTexto);
A lo largo de nuestro código, donde sea que hagamos referencia a la variable myText, ahora veremos aparecer el nuevo texto. Si bien esto es difícil de imaginar para algo tan simple como lo que tenemos ahora, para aplicaciones más grandes, esta conveniencia de tener solo una ubicación donde podemos hacer un cambio que se refleje en todas partes es un gran ahorro de tiempo. Verá más casos menos triviales del valor que proporcionan las variables en los ejemplos siguientes.

MÁS COSAS VARIABLES
Lo que aprendimos en la sección anterior nos llevará lejos en la vida. Al menos, lo hará en las partes de nuestra vida que impliquen familiarizarse con JavaScript. No profundizaremos mucho más en las variables aquí, ya que haremos todo eso como parte de capítulos futuros donde el código es más complejo y la importancia de las variables es más obvia. Dicho esto, hay algunas probabilidades y extremos que deberíamos cubrir antes de dar por finalizado el día.

Nombrar variables
Tenemos mucha libertad para nombrar nuestras variables como mejor nos parezca. Ignorando los nombres que deberíamos dar a las cosas en función de las preferencias filosóficas / culturales / estilísticas, desde un punto de vista técnico, JavaScript es muy indulgente con los caracteres que pueden incluirse en un nombre variable.

Esta indulgencia no es infinita, por lo que debemos tener en cuenta lo siguiente al nombrar nuestras variables:

Las variables pueden ser tan cortas como un carácter, o pueden ser tan largas como desee, piense en miles y miles de caracteres.

Las variables pueden comenzar con una letra, un guión bajo o el carácter $. No pueden empezar con un número.

Fuera del primer carácter, nuestras variables pueden estar formadas por cualquier combinación de letras, guiones bajos, números y $ caracteres. También podemos mezclar y combinar minúsculas y mayúsculas al contenido de nuestro corazón.

No se permiten espacios.

A continuación, se muestran algunos ejemplos de nombres de variables válidos:

Haga clic aquí para ver la imagen del código

let myText;
dejar $;
deje r8;
dejemos _counter;
let $ campo;
let thisIsALongVariableName_butItCouldBeLonger;
deje __ $ abc;
let OldSchoolNamingScheme;
Para ver si un nombre de variable es válido, consulte el validador de nombre de variable de JavaScript realmente impresionante y simple.

Además de los nombres válidos, también hay otras cosas en las que centrarse, como las convenciones de nomenclatura y cuántas personas suelen nombrar variables y otras cosas que se identifican con un nombre. Tocaremos estas cosas en otros capítulos.

Más sobre cómo declarar e inicializar variables
Una de las cosas que aprenderá sobre JavaScript es que es un lenguaje muy indulgente y fácil de trabajar.

Declarar una variable es opcional
Por ejemplo, no tenemos que usar la palabra clave let para declarar una variable. Podríamos hacer algo de la siguiente manera:

Haga clic aquí para ver la imagen del código

myText = "¡hola, mundo!";
alerta (miTexto);
Observe que la variable myText se usa sin declararse formalmente con la palabra clave let. Si bien no se recomienda, esto está completamente bien. El resultado final es que tenemos una variable llamada myText. Lo único es que, al declarar una variable de esta manera, la estamos declarando globalmente. No se preocupe si la última oración no tiene sentido. Veremos lo que significa globalmente cuando hablamos de alcance variable más adelante.

Declarar e inicializar en líneas separadas es genial
Hay una cosa más que señalar, y es la siguiente: la declaración e inicialización de una variable no tiene que ser parte de la misma declaración. Podemos dividirlo en varias declaraciones:

Haga clic aquí para ver la imagen del código

let myText;
myText = "¡hola, mundo!";
alerta (miTexto);
En la práctica, nos encontraremos rompiendo nuestra declaración e inicialización de variables todo el tiempo.

Cambio de valores de variables y la palabra clave constante
Por último, podemos cambiar el valor de una variable declarada vía let a lo que queramos cuando queramos:

Haga clic aquí para ver la imagen del código

let myText;
myText = "¡hola, mundo!";
myText = 99;
myText = 4 * 10;
myText = true;
myText = undefined;
alerta (miTexto);
Si tiene experiencia trabajando con lenguajes que son más estrictos y no permiten que las variables almacenen una variedad de tipos de datos, esta indulgencia es una de las características que la gente ama y odia de JavaScript. Dicho esto, JavaScript proporciona una forma de restringir el cambio del valor de una variable después de inicializarla. Esa restricción viene en forma de la palabra clave const que podemos declarar e inicializar nuestras variables con:

Haga clic aquí para ver la imagen del código

const siteURL = "https://www.google.com";
alerta (siteURL);
Al confiar en const, no podemos cambiar el valor de siteURL a otro que no sea https://www.google.com. JavaScript se quejará si intentamos hacer eso. Existen algunos errores al usar la palabra clave const, pero hace un gran trabajo en general para prevenir modificaciones accidentales de una variable. Para esas trampas molestas, las cubriremos en pedazos cuando sea el momento adecuado.

Sugerencia de imagen

Saltar adelante: alcance variable

Ahora que sabe cómo declarar e inicializar variables, un tema muy importante es el de la visibilidad. Necesita saber cuándo y dónde una variable que declaró se puede usar en su código. La frase general para esto se conoce como alcance variable. Si tiene curiosidad por saber más al respecto, puede avanzar y leer el Capítulo 8, "Alcance variable".

El Mínimo Absoluto

Los valores almacenan datos y las variables actúan como una forma fácil de hacer referencia a esos datos. Hay muchos detalles interesantes sobre los valores, pero esos son detalles que no necesita aprender en este momento. Solo sepa que JavaScript le permite representar una variedad de valores, como texto y números, sin mucho alboroto.

Para que sus valores sean más memorables y reutilizables, declare variables. Declaras variables usando la palabra clave let y un nombre de variable. Si desea inicializar la variable a un valor predeterminado, siga todo eso con un signo igual (=) y el valor con el que desea inicializar su variable. 
