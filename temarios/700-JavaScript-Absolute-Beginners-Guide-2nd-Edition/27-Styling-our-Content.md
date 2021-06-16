# 27. Styling our Content

* Why Would We Set Styles Using JavaScript?
* A Tale of Two Styling Approaches
* Checking Whether a Class Value Exists

En este capítulo

* Aprenda a cambiar CSS usando JavaScript.
* Comprender los pros y los contras de establecer estilos directamente en lugar de ajustar los valores de clase.
* Use `classList` para hacer que jugar con los valores de las clases de elementos sea muy sencillo

En el capítulo anterior, vimos cómo modificar el contenido de nuestro DOM usando JavaScript. La otra parte de lo que hace que nuestros elementos HTML se destaquen es su apariencia, su estilo. Cuando se trata de diseñar algún contenido, la forma más común es crear una regla de estilo y hacer que su selector apunte a un elemento o elementos. Una regla de estilo se vería de la siguiente manera:

```css
.batman {
  width: 100px;
  height: 100px;
  background-color: #333;
}
```

Un elemento que se vería afectado por esta regla de estilo podría verse así:

```html
<div class="batman"></div>
```

En cualquier página web, veremos desde unas pocas hasta muchas MUCHAS reglas de estilo, cada una de las cuales se superpone maravillosamente para diseñar todo lo que vemos. Sin embargo, este no es el único enfoque que podemos utilizar para diseñar contenido con CSS. ¡No sería HTML si no hubiera varias formas de realizar la misma tarea!

Ignorando los estilos en línea, el otro enfoque que podemos utilizar para introducir elementos a la bondad de los estilos CSS implica JavaScript. Podemos usar JavaScript para **establecer directamente un estilo en un elemento**, y también podemos usar JavaScript para **agregar o eliminar valores de clase en elementos** que alterarán qué reglas de estilo se aplican.

En este tutorial, aprenderemos sobre ambos enfoques.

¡Adelante!

## ¿POR QUÉ CONFIGURAREMOS ESTILOS CON JAVASCRIPT?

Antes de continuar, probablemente sea útil explicar por qué querríamos usar JavaScript para afectar el estilo de un elemento en primer lugar. En los casos comunes en los que usamos reglas de estilo o estilos en línea para afectar el aspecto de un elemento, el estilo se activa cuando se carga la página. Eso es asombroso, y eso es probablemente lo que queremos la mayor parte del tiempo.

Hay muchos casos, especialmente a medida que nuestro contenido se vuelve más interactivo, en los que queremos que los estilos se activen dinámicamente según la entrada del usuario, algún código que se haya ejecutado en segundo plano y más. En este tipo de escenarios, el modelo CSS que involucra reglas de estilo o estilos en línea no nos ayudará. Si bien los ***pseudoelectores*** como ***hover*** brindan algo de apoyo, todavía estamos muy limitados en lo que podemos hacer.

La solución que necesitaremos emplear para todos ellos es una que involucre JavaScript. JavaScript no solo nos permite diseñar el elemento con el que estamos interactuando, lo que es más importante, también nos permite diseñar elementos en toda la página. Esta libertad es muy poderosa y va mucho más allá de la capacidad limitada de CSS para diseñar contenido dentro (o muy cerca) de sí mismo.

## UNA HISTORIA DE DOS ENFOQUES DE ESTILO

Como vimos en la introducción, tenemos dos formas de alterar el estilo de un elemento usando JavaScript. Una forma es establecer una propiedad CSS directamente en el elemento. La otra forma es agregando o quitando valores de clase de un elemento que puede resultar en que ciertas reglas de estilo sean aplicadas o ignoradas. Analicemos ambos casos con mayor detalle.

### Setting el Estilo Directamente

Cada elemento HTML al que accede a través de JavaScript tiene un objeto `style`. Este objeto le permite especificar una propiedad CSS y establecer su valor. Por ejemplo, así es como se ve la configuración del color de fondo background de un elemento HTML cuyo valor del `id` es **superman**:

```js
let myElement = document.querySelector("#superman");
myElement.style.backgroundColor = "#D93600";
```

Para afectar muchos elementos, puede hacer algo de la siguiente manera:

```js
let myElements = document.querySelectorAll(".bar");
for (let i = 0; i < myElements.length; i++) {
   myElements[i].style.opacity = 0;
}
```

En pocas palabras, para diseñar elementos directamente usando JavaScript, el primer paso es acceder al elemento. Nuestro práctico método `querySelector` de antes es bastante útil aquí. El segundo paso es simplemente encontrar la propiedad CSS que le interesa y darle un valor. Recuerde, muchos valores en CSS son en realidad strings. También recuerde que muchos valores requieren una unidad de medida como **px** o **em** o algo así para ser reconocidos. También recuerda ... en realidad, lo olvidé.

Por último, algunas propiedades de CSS requieren que se proporcione un valor más complejo con un montón de texto aleatorio seguido del valor que le interesa. Uno de los más populares en este segmento es la propiedad `transform`. Un enfoque para establecer un valor complejo es utilizar una buena concatenación de cadenas a la antigua:

```js
myElement.style.transform = "translate3d(" + xPos + ", " + yPos + "px, 0)";
```

Eso puede resultar realmente irritante, ya que hacer un seguimiento de las comillas y demás es algo tedioso y propenso a errores. Una solución menos irritante es utilizar la sintaxis template literal (literal de la plantilla):

```js
myElement.style.transform = `translate3d(${xPos}px, ${yPos}px, 0)`;
```

Observe cómo este enfoque le permite seguir proporcionando valores personalizados mientras evita toda la complejidad de la concatenación de cadenas.

> ![tip.jpg](images/tip.jpg)
> 
> **Especial Revestimiento de algunos Nombres de Propiedades CSS**

JavaScript es muy exigente con lo que constituye un nombre de propiedad válido. La mayoría de los nombres en CSS obtendrían el sello de aprobación de JavaScript, por lo que puede usarlos directamente desde la carton. Sin embargo, hay algunas cosas a tener en cuenta.

Para especificar una propiedad CSS en JavaScript que contenga un guión, simplemente elimínelo. Por ejemplo, `background-color` se convierte en `backgroundColor`, la propiedad `border-radius` se transforma en `borderRadius`, y así sucesivamente.

Además, ciertas palabras en JavaScript están reservadas y no se pueden usar directamente. Un ejemplo de una propiedad CSS que cae en esta categoría especial es `float`. En CSS es una propiedad de diseño. En JavaScript, significa algo más. Para usar una propiedad cuyo nombre está completamente reservado, anteponga **css** a la propiedad, donde `float` se convierte en `cssFloat`.

### Agregar y Eliminar Clases con JavaScript

El segundo enfoque implica agregar y eliminar valores de clase que, a su vez, cambian las reglas de estilo que se aplican. Por ejemplo, digamos que tenemos una regla de estilo que tiene el siguiente aspecto:

```css
.disableMenu {
   display: none;
}
```


En HTML, tenemos un menú cuyo `id` es **`dropDown`**:

```html
<ul id="dropDown">
   <li>One</li>
   <li>Two</li>
   <li>Three</li>
   <li>Four</li>
   <li>Five</li>
   <li>Six</li>
</ul>
```

Ahora, si quisiéramos aplicar nuestra regla de estilo `.disableMenu` a este elemento, todo lo que tendríamos que hacer es agregar **disableMenu** como un valor `class` al elemento **`dropDown`**:

```html
<ul class="disableMenu" id="dropDown">
   <li>One</li>
   <li>Two</li>
   <li>Three</li>
   <li>Four</li>
   <li>Five</li>
   <li>Six</li>
</ul>
```

Una forma de lograr esto implica establecer la propiedad `className` de un elemento, un enfoque que vimos anteriormente. El problema con `className` es que somos responsables de mantener la lista actual de valores de clase aplicados. Peor aún, la lista de valores de clase se nos devuelve como un string. Si tenemos varios valores de clase que queremos agregar, eliminar o simplemente activar/desactivar, tenemos que hacer un montón de trucos relacionados con string propensos a errores que simplemente no son divertidos.

Para ayudar a aliviar algunos de los inconvenientes, ahora tenemos una API mucho más agradable que hace que agregar y eliminar valores de clase de un elemento sea ridículamente fácil. Esta nueva API se conoce cariñosamente como `classList`, y proporciona un puñado de métodos que harán que trabajar con valores de clase sea pan comido:

* `add`
* `remove`
* `toggle`
* `contains`

Lo que hacen estos cuatro métodos puede ser bastante evidente por sus nombres, pero veámoslos con más detalle.

### Agregar Class Values

Para agregar un valor de class a un elemento, obtenga una referencia al elemento y llame al método `add` a través de `classList`:

```js
let divElement = document.querySelector("#myDiv");
divElement.classList.add("bar");
divElement.classList.add("foo");
divElement.classList.add("zorb");
divElement.classList.add("baz");

console.log(divElement.classList);
```

Después de que se ejecute este código, nuestro elemento `div` tendrá los siguientes valores de clase: **bar**, **foo**, **zorb**, **baz**. La API `classList` se encarga de garantizar que se agreguen espacios entre los valores de clase. Si especificamos un valor de clase no válido, la API `classList` se quejará y no lo agregará. Si le decimos al método `add` que agregue una clase que ya existe en el elemento, nuestro código aún se ejecutará, pero el valor de la clase duplicada no se agregará.

### Eliminar Class Values

Para eliminar un valor de clase, podemos llamar al método `remove` en `classList`:

```js
let divElement = document.querySelector("#myDiv");
divElement.classList.remove("foo");

console.log(divElement.classList);
```

Después de que se ejecute este código, se eliminará el valor de la clase **foo**. Lo que nos quedará es solo **bar** y **zorb**. Bastante simple, ¿verdad?

### Alternar - Toggling Class Values

Para muchos escenarios de estilo, existe un flujo de trabajo muy común. Primero, verificamos si existe un valor de clase en un elemento. Si el valor existe, lo eliminamos del elemento. Si el valor no existe, agregamos ese valor de clase al elemento. Para simplificar este patrón de alternancia muy común, la API `classList` le proporciona el método `toggle`:

```js
let divElement = document.querySelector("#myDiv");
divElement.classList.toggle("foo"); // remove foo
divElement.classList.toggle("foo"); // add foo
divElement.classList.toggle("foo"); // remove foo

console.log(divElement.classList);
```

El método `toggle`, como su nombre lo indica, agrega o elimina el valor de clase especificado en el elemento cada vez que se llama. En nuestro caso, la clase **foo** se elimina la primera vez que se llama al método `toggle`. La segunda vez, se agrega la clase **foo**. La tercera vez, se elimina la clase **foo**. Te dan la imagen.

## COMPROBAR SI EXISTE UN CLASS VALUE

Lo último que veremos es el método `contains`:

```js
let divElement = document.querySelector("#myDiv");

if (divElement.classList.contains("bar") == true) {
   // do something
}
```

Este método comprueba si el valor de clase especificado existe en el elemento. Si el valor existe, devuelve **true**. Si el valor no existe, obtiene **false**.

### Ir más lejos

Como puede ver, la API `classList` le proporciona casi todo lo que necesita para agregar, eliminar o inspeccionar valores de clase en un elemento con mucha facilidad. El énfasis está en la palabra casi. Para las pocas cosas que la API no proporciona de forma predeterminada, puede conectarse y leer mi artículo completo sobre muchas más cosas que puede hacer con `classList`: http://bit.ly/kClassList.

<hr>

### El Mínimo Absoluto

Entonces, ahí lo tiene: dos enfoques basados en JavaScript perfectamente precisos que puede usar para diseñar sus elementos. De estas dos opciones, si tiene la capacidad de modificar su CSS, preferiría que utilizara elementos de estilo adding and removing classes. La simple razón es que este enfoque es mucho más fácil de mantener. Es mucho más fácil agregar y eliminar propiedades de estilo de una regla de estilo en CSS en lugar de agregar y eliminar líneas de JavaScript.

¿Tienes alguna pregunta? La gente amigable en los foros puede tener una respuesta. ¡Dirígete a https://forum.kirupa.com para preguntar!
