# 2. Values and Variables

* Using Variables
* More Variable Stuff


En este capítulo

* Aprenda a usar valores para almacenar datos.
* Organiza tu código con variables
* Eche un vistazo breve a las convenciones de nomenclatura de variables.

En JavaScript, se considera que cada dato que proporcionamos o usamos contiene un valor. En el ejemplo que vimos en nuestra introducción, las palabras **hello, world!** podrían ser solo algunas palabras que pasamos a la función `alert`:

```js
alert("hello, world!");
```

Para JavaScript, estas palabras tienen una representación específica debajo de las cubiertas. Se consideran valores. Es posible que no hayamos pensado mucho en eso cuando escribimos esas palabras, pero cuando estamos en el país de JavaScript, cada dato que toca se considera un valor.

Ahora bien, ¿por qué es importante saber esto? Es importante porque trabajaremos mucho con valores. Trabajar con ellos de una manera que no te vuelva loco es algo bueno. Solo hay dos cosas que necesitamos para simplificar nuestra vida trabajando con valores. Necesitamos que:

* Identifíquelos fácilmente
* Reutilícelos en toda su aplicación sin duplicar innecesariamente el valor en sí

Esas dos cosas las proporciona aquello en lo que vamos a dedicar el resto de nuestro tiempo: las ***variables***. Aprendamos todo sobre ellos aquí.

## USANDO VARIABLES

Una variable es un identificador de un valor. En lugar de escribir **hello, world!**, cada vez que quiera usar esa frase en su aplicación, puede asignar esa frase a una variable y usar esa variable siempre que necesite usar **hello, world!** de nuevo. Esto tendrá más sentido en unos momentos, ¡lo prometo!

Hay varias formas de utilizar variables. En la mayoría de los casos, la mejor manera es confiando en la palabra clave `let` seguida del nombre que desea darle a su variable:

```js
let myText
```

En esta línea de código, declaramos una variable llamada `myText`. En este momento, nuestra variable simplemente ha sido **declarada**. No contiene nada de valor. Es simplemente una cáscara vacía.

Arreglemos eso **inicializando** nuestra variable a un valor como ... digamos ... **hello, world!**:

```js
let myText = "hello, world!";
```

En este punto, cuando se ejecute este código, nuestra variable `myText` tendrá el valor **hello, world!** asociado a ello. Juntemos todo esto como parte de un ejemplo completo. Si todavía tiene abierto **hello_world.htm** desde antes, reemplace el contenido de su `script` con lo siguiente ... o cree un nuevo archivo HTML y agregue el siguiente contenido en él:

```js
<!DOCTYPE html>
<html>

<head>
   <meta charset="utf-8">
   <title>An Interesting Title Goes Here</title>

   <style>

   </style>
</head>

<body>
   <script>
      let myText = "hello, world!";                                                   
      alert(myText);                                                                  
   </script>

</body>

</html>
```

¡Observe que ya no estamos pasando en el **hello, world!** envíe un mensaje de texto a la función `alert` directamente. En su lugar, ahora estamos pasando el nombre de variable myText en su lugar. El resultado final es el mismo. Cuando se ejecuta este script, un `alert` con **hello, world!** se mostrará. Lo que este cambio nos permite hacer es tener un lugar en nuestro código donde **hello, world!** se está especificando. Si quisiéramos cambiar **hello, world!** a **The dog ate my homework!** ¡El perro se comió mi tarea !, todo lo que tendríamos que hacer es hacer un cambio en la frase especificada por la variable `myText`:

```js
let myText = "The dog ate my homework!";
alert(myText);
```

A lo largo de nuestro código, donde sea que hagamos referencia a la variable `myText`, ahora veremos aparecer el nuevo texto. Si bien esto es difícil de imaginar para algo tan simple como lo que tenemos ahora, para aplicaciones más grandes, esta conveniencia de tener solo una ubicación donde podemos hacer un cambio que se refleje en todas partes es un gran ahorro de tiempo. Verá más casos menos triviales del valor que proporcionan las variables en los ejemplos siguientes.

## MÁS COSAS VARIABLES

Lo que aprendimos en la sección anterior nos llevará lejos en la vida. Al menos, lo hará en las partes de nuestra vida que impliquen familiarizarse con JavaScript. No profundizaremos mucho más en las variables aquí, ya que haremos todo eso como parte de capítulos futuros donde el código es más complejo y la importancia de las variables es más obvia. Dicho esto, hay algunas probabilidades y extremos que deberíamos cubrir antes de dar por finalizado el día.

### Nombrar variables

Tenemos mucha libertad para nombrar nuestras variables como mejor nos parezca. Ignorando los nombres que deberíamos dar a las cosas en función de las preferencias filosóficas/culturales/ estilísticas, desde un punto de vista técnico, JavaScript es muy indulgente con los caracteres que pueden incluirse en un nombre variable.

Esta indulgencia no es infinita, por lo que debemos tener en cuenta lo siguiente al nombrar nuestras variables:

* Las variables pueden ser tan cortas como un carácter, o pueden ser tan largas como desee, piense en miles y miles de caracteres.
* Las variables pueden comenzar con una letra, un guión bajo o el carácter `$`. ***No pueden empezar con un número***.
* Fuera del primer carácter, nuestras variables pueden estar formadas por cualquier combinación de letras, guiones bajos, números y caracteres `$`. También podemos mezclar y combinar minúsculas y mayúsculas al contenido.
* No se permiten espacios.

A continuación, se muestran algunos ejemplos de nombres de variables válidos:

```js
let myText;
let $;
let r8;
let _counter;
let $field;
let thisIsALongVariableName_butItCouldBeLonger;
let __$abc;
let OldSchoolNamingScheme;
```

Para ver si un nombre de variable es válido, consulte el [**JavaScript Variable Name Validator**](https://mothereff.in/js-variables) realmente impresionante y simple.

Además de los nombres válidos, también hay otras cosas en las que centrarse, como las convenciones de nomenclatura y cuántas personas suelen nombrar variables y otras cosas que se identifican con un nombre. Tocaremos estas cosas en otros capítulos.

### Más sobre cómo Declarar e Inicializar Variables

Una de las cosas que aprenderá sobre JavaScript es que es un lenguaje muy indulgente y fácil de trabajar.

#### Declarar una Variable es Opcional

Por ejemplo, no tenemos que usar la palabra clave `let` para declarar una variable. Podríamos hacer algo de la siguiente manera:

```js
myText = "hello, world!";
alert(myText);
```

Observe que la variable `myText` se usa sin declararse formalmente con la palabra clave `let`. Si bien no se recomienda, esto está completamente bien. El resultado final es que tenemos una variable llamada `myText`. **Lo único es que, al declarar una variable de esta manera, la estamos declarando globalmente**. No se preocupe si la última oración no tiene sentido. Veremos lo que significa globalmente cuando hablamos de alcance variable más adelante.

#### Declarar e Inicializar en Líneas Separadas es genial

Hay una cosa más que señalar, y es la siguiente: ***la declaración e inicialización de una variable no tiene que ser parte de la misma declaración***. Podemos dividirlo en varias declaraciones:

```js
let myText;
myText = "hello, world!";
alert(myText);
```

En la práctica, nos encontraremos rompiendo nuestra declaración e inicialización de variables todo el tiempo.

#### Cambio de Valores de Variables y la palabra clave `const`

Por último, podemos cambiar el valor de una variable declarada vía `let` a lo que queramos cuando queramos:

```js
let myText;
myText = "hello, world!";
myText = 99;
myText = 4 * 10;
myText = true;
myText = undefined;
alert(myText);
```

Si tiene experiencia trabajando con lenguajes que son más estrictos y no permiten que las variables almacenen una variedad de tipos de datos, ***esta indulgencia es una de las características que la gente ama y odia de JavaScript***. Dicho esto, JavaScript proporciona una forma de restringir el cambio del valor de una variable después de inicializarla. Esa restricción viene en forma de la palabra clave `const` que podemos declarar e inicializar nuestras variables con:

```js
const siteURL = "https://www.google.com";
alert(siteURL);
```

Al confiar en `const`, no podemos cambiar el valor de `siteURL` a otro que no sea **https://www.google.com**. JavaScript se quejará si intentamos hacer eso. Existen algunos errores al usar la palabra clave `const`, pero hace un gran trabajo en general para prevenir modificaciones accidentales de una variable. Para esas trampas molestas, las cubriremos cuando sea el momento adecuado.

> ![tip](images/tip.jpg) **Tip**
> 
> **Saltar adelante: alcance variable**
>
> Ahora que sabe cómo declarar e inicializar variables, un tema muy importante es el de la visibilidad. Necesita saber cuándo y dónde una variable que declaró se puede usar en su código. La frase general para esto se conoce como **alcance variable - variable scope**. Si tiene curiosidad por saber más al respecto, puede avanzar y leer el Capítulo 8, "Alcance variable".

<hr>

### El Mínimo Absoluto

Los valores almacenan datos y las variables actúan como una forma fácil de hacer referencia a esos datos. Hay muchos detalles interesantes sobre los valores, pero esos son detalles que no necesita aprender en este momento. Solo sepa que JavaScript le permite representar una variedad de valores, como texto y números, sin mucho alboroto.

Para que sus valores sean más memorables y reutilizables, declare variables. Declaras variables usando la palabra clave `let` y un **nombre de variable**. Si desea inicializar la variable a un valor predeterminado, siga todo eso con un signo igual (`=`) y el valor con el que desea inicializar su variable. 

## 🔴 💻 `02-01-Hello-World-con-Variables.html`

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>01-02-Hello-World-con-Variables</title>
</head>
<body>
    <script>
        let myText = "Hola, mundo!"; 
        alert(myText);
    </script>
</body>
</html>
```

![image](https://user-images.githubusercontent.com/23094588/121655569-ff315a00-ca9e-11eb-8668-eff22073f20c.png)

## 🔴 💻 `02-02-Hello-World-con-Variables.html`

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>01-02-Hello-World-con-Variables</title>
</head>
<body>
    <script>
        let myText;
        myText = "hello, world!";
        myText = 99;
        myText = 4 * 10;
        myText = true;
        myText = undefined;
        alert(myText);
    </script>
</body>
</html>
```

![image](https://user-images.githubusercontent.com/23094588/121655670-11ab9380-ca9f-11eb-9867-90291149ebdb.png)


## 🔴 💻 `02-03-Hello-World-con-Constantes.html`

```html
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>01-02-Hello-World-con-Variables</title>
</head>
<body>
    <script>
        const siteURL = "https://www.google.com";
        alert(siteURL);
    </script>
</body>
</html>
```

![image](https://user-images.githubusercontent.com/23094588/121655892-3e5fab00-ca9f-11eb-906d-50b239a30a4d.png)


