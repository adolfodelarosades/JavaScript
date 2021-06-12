# 6. Commenting Your Code...FTW!

* What Are Comments?
* Commenting Best Practices


En este capítulo

* Aprenda a comentar su código
* Descubra las mejores prácticas en torno a los comentarios

Todo lo que escribimos en nuestro editor de código puede parecer que está destinado únicamente a los ojos de nuestro navegador:

```js
let xPos = -500;

function boringComputerStuff() {
  xPos += 5;

  if (xPos > 1000) {
    xPos = -500;
  }
}
boringComputerStuff();
```

Como pronto descubriremos, ese no es el caso. Hay otra audiencia para nuestro código. Esa audiencia está formada por seres humanos.

Nuestro código a menudo es usado o examinado por otras personas. Esto es especialmente cierto si usted y yo estamos trabajando en equipo con otros desarrolladores de JavaScript. A menudo, veremos su código y, a menudo, ellos verán nuestro código. Para que todo este código se vea lo más eficiente posible, debemos asegurarnos de que nuestro código tenga sentido cuando alguien que no sea nosotros lo esté mirando. Incluso si está trabajando solo, esto también se aplica a usted. Esa función brillante que tiene sentido para usted hoy podría ser un galimatías cuando la revise la próxima semana.

Hay muchas formas de solucionar este problema. Una de las mejores formas es usar algo conocido como comentarios. En este breve artículo, aprenderemos qué son los comentarios, cómo especificarlos en JavaScript y aprenderemos algunas buenas prácticas sobre cómo usarlos.

¡Adelante!

### ¿QUÉ SON LOS COMENTARIOS?

Los comentarios son las cosas que escribimos como parte de nuestro código para comunicar algo a los humanos:

```js
// This is for not inviting me to your birthday party!
let blah = true;

function sweetRevenge() {
  while (blah) {
    // Infinite dialog boxes! HAHAHA!!!!
    alert("Hahahaha!");
  }
}
sweetRevenge();
```

En este ejemplo, los comentarios están marcados con el carácter // y proporcionan información cuestionablemente útil sobre el código que se describe.

Lo que debe tener en cuenta acerca de los comentarios es que no se ejecutan ni se ejecutan como el resto del código que escribe. JavaScript ignora sus comentarios. No le gustas. No le importa lo que tenga que decir, por lo que no tiene que preocuparse por la sintaxis, la puntuación, la ortografía y todo lo demás que debe tener en cuenta al escribir código normal. Los comentarios existen solo para que nos ayuden a comprender qué está haciendo un fragmento de código.

Hay otro propósito para el que sirven los comentarios. Podemos usar comentarios para marcar líneas de código que no queremos que se ejecuten:

```js
function insecureLogin(input) {
  if (input == "password") {
    // let key = Math.random() * 100000;
    // processLogin(key);
  }
  return false;
}
```

En este ejemplo, las siguientes dos líneas se pueden ver en nuestro editor de código, pero no se ejecutarán:

```js
// let key = Math.random() * 100000;
// processLogin(key);
```

A menudo nos encontramos usando el editor de código como un bloc de notas, y los comentarios son una excelente manera de realizar un seguimiento de las cosas que hemos intentado para hacer que nuestro código funcione sin afectar la forma en que se ejecuta finalmente su aplicación.

Comentarios de una sola línea
Hay varias formas de especificar comentarios en nuestro código. Una forma es especificando comentarios de una sola línea usando la marca // seguida de lo que queremos comunicar. Esta es la variación de comentarios que ya hemos visto varias veces.

Podemos especificar estos comentarios en su propia línea dedicada:

```js
// Return the larger of the two arguments
function max(a, b) {
  if (a > b) {
    return a;
  } else {
    return b;
  }
}
```

También podemos especificar estos comentarios en la misma línea que una declaración:

```js
let zorb = "Alien"; // Annoy the planetary citizens
```

El lugar donde especificamos los comentarios depende completamente de usted. Elija una ubicación que le parezca apropiada para el comentario que está escribiendo.

Como disfruto sonar como un disco rayado, para llamar una vez más, nuestros comentarios no se ejecutan como parte de nuestra aplicación. Solo tú, yo y posiblemente Dupree podemos verlos. Si esa última línea no tenía sentido, lo que me está diciendo es que no vio una de las mejores comedias de nuestra generación. Le recomiendo encarecidamente que deje este libro o tutorial y se tome unas horas para rectificarlo.

Comentarios de varias líneas
El problema con los comentarios de una sola línea es que debe especificar los caracteres // delante de cada línea que desee comentar. Eso puede resultar muy agotador, especialmente si está escribiendo un comentario largo o comentando una gran cantidad de código.

Para esas situaciones, tiene otra forma de especificar comentarios. Tiene los caracteres / * y * / para especificar el comienzo y el final de lo que se conoce como comentarios de varias líneas:

```js
/*
let mouseX = 0;
let mouseY = 0;

canvas.addEventListener("mousemove", setMousePosition, false);

function setMousePosition(e) {
  mouseX = e.clientX;
  mouseY = e.clientY;
}
*/
```

En lugar de agregar marcas // delante de cada línea como un animal, podemos usar los caracteres / * y * / para ahorrarnos mucho tiempo y frustración.

En la mayoría de las aplicaciones, usaremos una combinación de comentarios de una sola línea y de varias líneas, según lo que intentemos documentar. Esto significa wNecesitamos estar familiarizados con ambos enfoques de comentarios.

> [tip.jpg](imagen/tip.jpg) **Tip**

**Comentarios de estilo JSDoc**

Cuando escribimos un código que desea que otros utilicen, probablemente desee una forma más fácil de comunicar lo que hace su código más allá de que la gente hurgue en el código fuente. ¡Esa forma más fácil existe, y es posible gracias a una herramienta conocida como JSDoc! Con JSDoc, modifica ligeramente la forma en que escribe sus comentarios:

```js
/**
 * Shuffles the contents of your Array.
 *
 * @this {Array}
 * @returns {Array} The current array with the contents
fully shuffled.
 */
Array.prototype.shuffle = function () {
  let input = this;

  for (let i = input.length - 1; i >= 0; i--) {

    let randomIndex = Math.floor(Math.random() *
(i + 1));
    let itemAtIndex = input[randomIndex];

    input[randomIndex] = input[i];
    input[i] = itemAtIndex;
  }
  return input;
}
```

Una vez que haya comentado sus archivos, puede utilizar la herramienta JSDoc para exportar las partes relevantes de sus comentarios a un conjunto de páginas HTML fácilmente navegables. Esto le permite dedicar más tiempo a escribir JavaScript al mismo tiempo que brinda a sus usuarios una manera fácil de comprender lo que hace su código y cómo usar varias partes de él.

Si desea obtener más información sobre cómo usar JSDoc, consulte su increíble página de Inicio para obtener más detalles.

## COMENTAR LAS MEJORES PRÁCTICAS

Ahora que tenemos una buena idea de lo que son los comentarios y las diversas formas que tenemos de escribirlos en JavaScript, hablemos un poco sobre cómo usar correctamente los comentarios para ayudar a que nuestro código sea fácil de leer:

* Siempre comente su código mientras lo escribe. Escribir comentarios es terriblemente aburrido, pero es una parte importante de escribir código. Es mucho más eficiente para usted (y otros) comprender lo que hace su código leyendo un comentario en lugar de leer línea tras línea de JavaScript aburrido.

* No posponga la redacción de comentarios para más tarde. Aplazar la redacción de comentarios para más adelante es el equivalente adulto de postergar una tarea. Si no comenta el código mientras lo escribe, probablemente se salte el comentario por completo. Eso no es bueno.

* Utilice más inglés y menos JavaScript. Los comentarios son uno de los pocos lugares al escribir JavaScript donde puede usar libremente el inglés (o cualquier idioma en el que prefiera comunicarse). No complique sus comentarios innecesariamente con código. Sea claro. Sé conciso. Utilizar palabras.

* Adopta los espacios en blanco. Al escanear grandes bloques de código, desea asegurarse de que sus comentarios se destaquen y sean claros para seguir. Eso implica ser liberal con la barra espaciadora y la tecla Intro / Retorno. Eche un vistazo al siguiente ejemplo:

```js
function selectInitialState(state) {
  let selectContent = document.querySelector("#stateList");
  let stateIndex = null;

  /*  
      For the returned state, we would like to ensure that
      we select it in our UI. This means we iterate through
      every state in the drop-down until we find a match. 
      When a match is found, we ensure it gets selected.
  */

  for (let i = 0; i < selectContent.length; i++) {

    let stateInSelect = selectContent.options[i].innerText;

    if (stateInSelect == state) {
      stateIndex = i;
    }
  }

  selectContent.selectedIndex = stateIndex;
}
```

   Tenga en cuenta que nuestro comentario está adecuadamente espaciado para distinguirlo del resto del código. Si sus comentarios están esparcidos en ubicaciones arbitrarias donde son difíciles de identificar, eso simplemente lo ralentiza innecesariamente a usted y a quienquiera que esté leyendo su código.

* No comente cosas obvias. Si una línea de código se explica por sí misma, no pierda el tiempo explicando lo que hace, a menos que exista algún comportamiento sutil que deba mencionar como advertencia. En su lugar, invierta ese tiempo en comentar las partes menos obvias de su código.

Las mejores prácticas que ve aquí lo llevarán lejos para asegurarse de escribir código correctamente comentado. Si está trabajando en un proyecto más grande con otras personas, puedo asegurarle que su equipo ya tiene algunas pautas establecidas sobre cómo se ven los comentarios adecuados. Tómese un tiempo para comprender esas pautas y sígalas. Estarás feliz. Tu equipo estará feliz.

<hr>

### El Mínimo Absoluto


Los comentarios a menudo se consideran un mal necesario. Después de todo, ¿preferiría tomarse unos minutos para documentar lo que claramente ya sabe, o preferiría implementar la próxima pieza interesante de funcionalidad? La forma en que me gusta describir los comentarios es la siguiente: Es una inversión a largo plazo. El valor y el beneficio de los comentarios a menudo no son inmediatamente obvios. Se vuelve obvio cuando comienza a tener otras personas revisando su código, y se vuelve obvio cuando tiene que volver a visitar su propio código después de haberlo olvidado por completo y cómo funciona. No sacrifique el ahorro de tiempo a largo plazo por un impulso a corto plazo. Invierta en comentarios de una sola línea (//) y de varias líneas (/ * y * /) ahora, antes de que sea demasiado tarde.

Como siempre, si tiene alguna pregunta sobre el contenido aquí, ¡yo y otros desarrolladores amigables estamos aquí para ayudarlo! Publica en los foros en https://forum.kirupa.com para desbloquearse rápidamente.
