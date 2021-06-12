# 6. Commenting Your Code...FTW!

* What Are Comments?
* Commenting Best Practices

6. Comentar su código ... FTW!
En este capítulo

• Aprenda a comentar su código

• Descubra las mejores prácticas en torno a los comentarios

Todo lo que escribimos en nuestro editor de código puede parecer que está destinado únicamente a los ojos de nuestro navegador:

Haga clic aquí para ver la imagen del código

sea ​​xPos = -500;

function boringComputerStuff () {
  xPos + = 5;

  si (xPos> 1000) {
    xPos = -500;
  }
}
boringComputerStuff ();
Como pronto descubriremos, ese no es el caso. Hay otra audiencia para nuestro código. Esa audiencia está formada por seres humanos.

Nuestro código a menudo es usado o examinado por otras personas. Esto es especialmente cierto si usted y yo estamos trabajando en equipo con otros desarrolladores de JavaScript. A menudo, veremos su código y, a menudo, ellos verán nuestro código. Para que todo este código se vea lo más eficiente posible, debemos asegurarnos de que nuestro código tenga sentido cuando alguien que no sea nosotros lo esté mirando. Incluso si está trabajando solo, esto también se aplica a usted. Esa función brillante que tiene sentido para usted hoy podría ser un galimatías cuando la revise la próxima semana.

Hay muchas formas de solucionar este problema. Una de las mejores formas es usar algo conocido como comentarios. En este breve artículo, aprenderemos qué son los comentarios, cómo especificarlos en JavaScript y aprenderemos algunas buenas prácticas sobre cómo usarlos.

¡Adelante!

¿QUÉ SON LOS COMENTARIOS?
Los comentarios son las cosas que escribimos como parte de nuestro código para comunicar algo a los humanos:

Haga clic aquí para ver la imagen del código

// ¡Esto es por no invitarme a tu fiesta de cumpleaños!
deja bla = verdad;

function sweetRevenge () {
  mientras (bla) {
    // ¡Cuadros de diálogo infinitos! ¡¡¡¡JAJAJA!!!!
    alerta ("¡Jajajaja!");
  }
}
dulce venganza();
En este ejemplo, los comentarios están marcados con el carácter // y proporcionan información cuestionablemente útil sobre el código que se describe.

Lo que debe tener en cuenta acerca de los comentarios es que no se ejecutan ni se ejecutan como el resto del código que escribe. JavaScript ignora sus comentarios. No le gustas. No le importa lo que tenga que decir, por lo que no tiene que preocuparse por la sintaxis, la puntuación, la ortografía y todo lo demás que debe tener en cuenta al escribir código normal. Los comentarios existen solo para que nos ayuden a comprender qué está haciendo un fragmento de código.

Hay otro propósito para el que sirven los comentarios. Podemos usar comentarios para marcar líneas de código que no queremos que se ejecuten:

Haga clic aquí para ver la imagen del código

function insecureLogin (entrada) {
  if (input == "contraseña") {
    // let key = Math.random () * 100000;
    // processLogin (clave);
  }
  falso retorno;
}
En este ejemplo, las siguientes dos líneas se pueden ver en nuestro editor de código, pero no se ejecutarán:

Haga clic aquí para ver la imagen del código

// let key = Math.random () * 100000;
// processLogin (clave);
A menudo nos encontramos usando el editor de código como un bloc de notas, y los comentarios son una excelente manera de realizar un seguimiento de las cosas que hemos intentado para hacer que nuestro código funcione sin afectar la forma en que se ejecuta finalmente su aplicación.

Comentarios de una sola línea
Hay varias formas de especificar comentarios en nuestro código. Una forma es especificando comentarios de una sola línea usando la marca // seguida de lo que queremos comunicar. Esta es la variación de comentarios que ya hemos visto varias veces.

Podemos especificar estos comentarios en su propia línea dedicada:

Haga clic aquí para ver la imagen del código

// Devuelve el mayor de los dos argumentos
function max (a, b) {
  si (a> b) {
    return a;
  } demás {
    volver b;
  }
}
También podemos especificar estos comentarios en la misma línea que una declaración:

Haga clic aquí para ver la imagen del código

let zorb = "Alien"; // Molestar a los ciudadanos planetarios
El lugar donde especificamos los comentarios depende completamente de usted. Elija una ubicación que le parezca apropiada para el comentario que está escribiendo.

Como disfruto sonar como un disco rayado, para llamar una vez más, nuestros comentarios no se ejecutan como parte de nuestra aplicación. Solo tú, yo y posiblemente Dupree podemos verlos. Si esa última línea no tenía sentido, lo que me está diciendo es que no vio una de las mejores comedias de nuestra generación. Le recomiendo encarecidamente que deje este libro o tutorial y se tome unas horas para rectificarlo.

Comentarios de varias líneas
El problema con los comentarios de una sola línea es que debe especificar los caracteres // delante de cada línea que desee comentar. Eso puede resultar muy agotador, especialmente si está escribiendo un comentario largo o comentando una gran cantidad de código.

Para esas situaciones, tiene otra forma de especificar comentarios. Tiene los caracteres / * y * / para especificar el comienzo y el final de lo que se conoce como comentarios de varias líneas:

Haga clic aquí para ver la imagen del código

/ *
deje mouseX = 0;
let mouseY = 0;

canvas.addEventListener ("mousemove", setMousePosition, falso);

function setMousePosition (e) {
  mouseX = e.clientX;
  mouseY = e.clientY;
}
* /
En lugar de agregar marcas // delante de cada línea como un animal, podemos usar los caracteres / * y * / para ahorrarnos mucho tiempo y frustración.

En la mayoría de las aplicaciones, usaremos una combinación de comentarios de una sola línea y de varias líneas, según lo que intentemos documentar. Esto significa w
