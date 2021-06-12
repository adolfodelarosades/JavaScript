# 7. Timers

* Delaying with setTimeout

En este capítulo

* Aprenda a retrasar la ejecución de su código
* Descubra varias formas de ejecutar su código repetidamente sin bloquear toda su aplicación

De forma predeterminada, nuestro código se ejecuta sincrónicamente. Esa es una forma elegante de decir que cuando una declaración necesita ejecutarse, se ejecuta inmediatamente. No hay "y", "si" ni "pero" al respecto. El concepto de retrasar la ejecución o aplazar el trabajo para más adelante no forma parte del comportamiento predeterminado de JavaScript. Vimos esto cuando miramos los bucles antes. El bucle se ejecuta a la velocidad del rayo sin demora entre cada iteración. Eso es genial para hacer cálculos rápidos, pero no es genial si queremos hacer una actualización a un ritmo más mesurado (¡también más lento!).

¡Todo esto no significa que no exista la capacidad de detener la ejecución del trabajo instantáneamente! Si nos desviamos un poco de la carretera principal, hay tres funciones que nos permiten hacer principalmente eso (y más): setTimeout, setInterval y requestAnimationFrame. En este artículo, veremos qué hace cada una de estas funciones.

¡Adelante!

## RETRASO CON SETTIMEOUT

La función setTimeout nos permite retrasar la ejecución de algún código. La forma en que lo usamos es bastante agradable. Esta función nos permite especificar qué código ejecutar y cuántos milisegundos esperar antes de que se ejecute el código que especificamos. Poniéndolo en JavaScript, se verá así:

```js
```

Yendo un poco más a un ejemplo, si quisiéramos llamar a una función llamada showAlert después de 5 segundos, la declaración setTimeout se vería de la siguiente manera:

```js
```

¿Guay, verdad? Ahora, hablemos de algo menos interesante que debemos cubrir para que esté completo. Ese algo tiene que ver con la variable timeID que se inicializa en nuestra función setTimeout. No está ahí por accidente. Si alguna vez quisiéramos acceder a este temporizador setTimeout nuevamente, necesitamos una forma de referenciarlo. Al asociar una variable con nuestra declaración setTimeout, podemos lograrlo fácilmente.

Ahora, es posible que se pregunte por qué querríamos hacer referencia a un temporizador una vez que lo hayamos creado. No hay demasiadas razones. La única razón que se me ocurre es cancelar el temporizador. Para setTimeout, eso se logra convenientemente usando la función clearTimeout y pasando el ID de tiempo de espera como argumento:

```js
```

Si nunca planea cancelar su temporizador, puede usar setTimeout directamente sin que sea parte de la inicialización de la variable.

Hablemos de cuándo lo usaríamos comúnmente en el mundo real. Desarrollo de UI. Cuando estamos desarrollando UI, diferir alguna acción para un momento posterior es inusualmente común. Aquí hay algunos ejemplos con los que me encontré el mes pasado:

Se desliza un menú y, después de unos segundos de que el usuario ya no juegue con el menú, el menú desaparece.

Tiene una operación de ejecución prolongada que no se puede completar y una función setTimeout interrumpe esa operación para devolver el control al usuario.

Mi favorito (y uno sobre el que también escribí un tutorial) es donde se usa la función setTimeout para detectar si los usuarios están inactivos o inactivos.

Si realiza una búsqueda de setTimeout en este sitio o en Google, verá muchos más casos del mundo real en los que setTimeout resulta muy útil.

Bucle con setInterval
La siguiente función de temporizador que veremos es setInterval. La función setInterval es similar a setTimeout en que también le permite ejecutar código después de un período de tiempo específico. Lo que lo hace diferente es que no solo ejecuta el código una vez. Sigue ejecutando el código en un bucle para siempre.

Así es como usaría la función setInterval:

```js
```

Excepto por el nombre de la función, la forma en que usa setInterval es incluso idéntica a setTimeout. El primer argumento especifica el código en línea o la función que le gustaría ejecutar. El segundo argumento especifica cuánto tiempo esperar antes de que su código vuelva a repetirse. Opcionalmente, también puede inicializar la función setInterval en una variable para almacenar un ID de intervalo, un ID que luego puede usar para hacer cosas interesantes como cancelar el bucle. ¡¡¡Hurra!!!

¡OK! Ahora que hemos visto todo eso, aquí hay un ejemplo de este código en funcionamiento para hacer un bucle en una función llamada drawText con un retraso de 2 segundos entre cada bucle:

```html
```

Si deseamos cancelar el bucle, podemos usar la función clearInterval con el nombre apropiado:

```js
```

Su uso es similar a su equivalente clearTimeout t. Pasamos el ID de la instancia del temporizador setInterval que obtuvimos opcionalmente mientras configuramos nuestro setInterval en primer lugar.

En la vida real, setInterval fue la función principal que tuvo durante más tiempo para crear animaciones en JavaScript. Para obtener 30 o 60 fotogramas por segundo, haría algo de la siguiente manera jugando con el valor del tiempo de retardo:

```js
```

Para ver setInterval en acción en algunos otros ejemplos realistas en este sitio, consulte la parte inferior del artículo Creando un control deslizante de contenido dulce (https://www.kirupa.com/html5/creating_a_sweet_content_slider.htm) así como el artículo Creando un Reloj analógico (https://www.kirupa.com/html5/create_an_analog_clock_using_the_canvas.htm) artículo. ¡Ambos cuentan con setInterval de manera bastante prominente!

Animando suavemente con requestAnimationFrame
Ahora, llegamos a una de mis funciones favoritas: requestAnimationFrame. La función requestAnimationFrame se trata de sincronizar su código con un evento de repintado del navegador. Lo que esto significa es lo siguiente: su navegador está ocupado haciendo malabarismos con mil millones de cosas diferentes en un momento dado. Estas cosas incluyen jugar con el diseño, reaccionar a los desplazamientos de página, escuchar los clics del mouse, mostrar el resultado de los toques del teclado, ejecutar JavaScript, cargar recursos y más. Al mismo tiempo que su navegador está haciendo todo esto, también está redibujando la pantalla a 60 cuadros por segundo ... o al menos haciendo todo lo posible para hacerlo.

Cuando tiene un código destinado a animar algo en la pantalla, desea asegurarse de que su código de animación se ejecute correctamente sin perderse en la mezcla de todo lo que hace su navegador. El uso de la técnica setInterval mencionada anteriormente no garantiza que los marcos no se descarten cuando el navegador está ocupado optimizando para otras cosas. Para evitar que su código de animación sea tratado como cualquier otro JavaScript genérico, tiene la función requestAnimationFrame. Esta función recibe un tratamiento especial por parte del navegador. Este tratamiento especial le permite programar su ejecución perfectamente para evitar la caída de marcos, evitar trabajos innecesarios y, en general, mantenerse alejado de otros efectos secundarios que afectan a otras soluciones de bucle.

La forma en que usamos esta función comienza un poco similar a setTimeout y setInterval:

```js
```

La única diferencia real es que no especificamos un valor de duración. La duración se calcula automáticamente en función de la velocidad de fotogramas actual, si la pestaña actual está activa o no, si su dispositivo está funcionando con batería o no, y una gran cantidad de otros factores que van más allá de lo que podemos controlar o comprender.

De todos modos, este uso de la función requestAnimationFrame es simplemente la versión del libro de texto. En la vida real, rara vez hará una sola llamada a requestAnimationFrame de esta manera. La clave para todas las animaciones creadas en JavaScript es un bucle de animación, y es este bucle al que queremos lanzar requestAnimationFrame. El resultado de ese lanzamiento tiene el siguiente aspecto:

```js
```

Tenga en cuenta que nuestro requestAnimationFrame especifica que la función animationLoop se llama la próxima vez que el navegador decide volver a pintar. Parece que la función requestAnimationFrame llama a animationLoop directamente, lo cual no es el caso. Eso no es un error en el código. Si bien este tipo de referencia circular casi garantizaría un navegador congelado / bloqueado, la implementación de requestAnimationFrame lo evita. En cambio, garantiza que la función animationLoop se llame la cantidad justa de veces necesarias para garantizar que las cosas se dibujen en la pantalla para crear animaciones fluidas y fluidas. Lo hace sin congelar el resto de la funcionalidad de la aplicación.

Para obtener más información sobre requestAnimationFrame y su uso principal para crear animaciones impresionantes, debe consultar todo el contenido en la sección Animaciones en JavaScript. En esa sección, también profundizo en requestAnimationFrame más allá de los aspectos más destacados que hemos visto aquí.

El Mínimo Absoluto

Si cree que los temporizadores pertenecen a una categoría más específica en comparación con algunas de las otras cosas más esenciales, como las declaraciones y los bucles if / else que vimos anteriormente, probablemente tenga razón al pensar eso. Puede crear muchas aplicaciones increíbles sin tener que depender de setTimeout, setInterval o requestAnimationFrame. Sin embargo, eso no significa que no sea esencial conocerlos. Habrá un momento en el que tendrá que retrasar la ejecución de su código, repetir su código continuamente o crear una animación dulce utilizando JavaScript. Cuando llegue ese momento, estará preparado ... o al menos sabrá para qué buscar en Google.

Para ver estas funciones de temporizador utilizadas en la naturaleza, consulte estos artículos y ejemplos opcionales que pueden ayudarlo a Utah:

Creando animaciones usando requestAnimationFrame http://bit.ly/kirupaAnimationsJS

Creación de un control deslizante de contenido dulce http://bit.ly/sliderTutorial

Creación de un reloj analógico http://bit.ly/kirupaAnalogClock

The Seizure Generator http://bit.ly/kirupaSeizureGenerator (Advertencia de convulsiones: la animación de este sitio parpadea intensamente).

Lo he mencionado varias veces hasta ahora, pero JavaScript puede resultar frustrante. Temporizadores doblemente. Si alguna vez tiene algún problema, ¡yo y otros desarrolladores que hemos luchado contra el tiempo durante mucho tiempo estamos aquí para ayudarlo! ¡Publique en los foros en https://forum.kirupa.com para no sentirse frustrado!
