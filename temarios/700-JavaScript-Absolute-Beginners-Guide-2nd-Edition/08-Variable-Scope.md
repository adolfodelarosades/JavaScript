# 8. Variable Scope

* Global Scope
* Local Scope
* Miscellaneous Scoping Shenanigans


En este capítulo

* Comprender el alcance global
* Familiarícese con las diversas técnicas disponibles para utilizar el alcance local.
* Conozca algunas peculiaridades que pueden hacer que su código se comporte de manera impredecible.

Repasemos algo relacionado con las variables que vimos hace unos capítulos. Cada variable que declaramos tiene un cierto nivel de visibilidad que determina cuándo realmente podemos usarla. En términos comprensibles para los humanos, el hecho de que declaremos una variable no significa que se pueda acceder a ella desde cualquier lugar de nuestro código. Hay algunas cosas básicas que debemos comprender, y toda esta área de comprensión se incluye en un tema conocido como alcance variable.

En este tutorial, voy a explicar el alcance de las variables observando casos comunes que ya hemos visto (en su mayoría). Este es un tema bastante profundo, pero solo vamos a arañar la superficie aquí. Veremos que el alcance de las variables aumenta en muchos tutoriales posteriores en los que ampliaremos lo que aprendemos aquí.

¡Adelante!

## GLOBAL SCOPE

Vamos a comenzar nuestra exploración del alcance desde lo más alto con lo que se conoce como alcance global. En la vida real, cuando decimos que algo se puede escuchar globalmente, significa que podemos estar en cualquier parte del mundo y aún poder escuchar eso ... algo

![084fig01.jpg](images/084fig01.jpg)

En JavaScript, se aplica casi lo mismo. Si decimos, por ejemplo, que una variable está disponible globalmente, significa que cualquier código de nuestra página tiene acceso para leer y modificar esta variable. La forma en que hacemos que algo se aplique globalmente es declarándolo en nuestro código completamente fuera de una función.

Para ilustrar esto, echemos un vistazo al siguiente ejemplo:

```html
```

Aquí, simplemente estamos declarando una variable llamada contador e inicializándola a 0. En virtud de que esta variable se declara directamente dentro de la etiqueta del script sin colocarse dentro de una función, la variable contador se considera global. Lo que esta distinción significa es que se puede acceder a nuestra variable de contador mediante cualquier código que viva en nuestro documento.

El siguiente código destaca esto:

```html
```

En este ejemplo, la variable de contador se declara fuera de la función returnCount. A pesar de eso, la función returnCount tiene acceso completo a la variable de contador. Cuando se ejecuta el código, la función de alerta llama a la función returnCount que devuelve el valor de la variable de contador.

En este punto, probablemente se esté preguntando por qué estoy señalando esto. Hemos estado usando variables globales todo este tiempo sin darnos cuenta. Todo lo que estoy haciendo aquí es presentarte formalmente a un invitado que ha estado rondando tu fiesta por un tiempo.

ALCANCE LOCAL
Ahora, las cosas se ponen un poco interesantes cuando miramos cosas que no se declaran globalmente. Aquí es donde la comprensión del alcance realmente comienza a dar dividendos. Como vimos anteriormente, una variable declarada globalmente es accesible dentro de una función:

```js
```

Lo contrario no es cierto. Una variable declarada dentro de una función no funcionará cuando se acceda fuera de una función:

```js
```

En este ejemplo, la variable de estado se declara dentro de la función setState y el acceso a la variable de estado fuera de esa función no funciona. La razón es que el alcance de nuestra variable de estado es local a la propia función setState. Una forma más genérica de describir esto es diciendo que su variable de estado es solo local.

Nota de imagen

Usar variables sin declararlas

Si inicializamos la variable de estado sin declararla formalmente, el comportamiento del alcance es drásticamente diferente:

```js
```

En este caso, aunque nuestra variable de estado aparece primero dentro de la función setState, no declararla primero con let o const (o var, que es una forma más antigua de declarar variables) hace que esta variable viva globalmente. En general, no desea declarar una variable como esta. Siempre antepóngalo con let o const.

SHENANIGANS DE EXPLORACIÓN MISCELÁNEA
Dado que estamos hablando de JavaScript aquí, las cosas serían demasiado fáciles si dejáramos todo con un alcance variable como están ahora. En las siguientes secciones, voy a resaltar algunas peculiaridades que necesita estar familiarizado con.

Alcance de bloque
Nuestro código se compone de bloques ... montones, montones de bloques. ¿Qué es exactamente un bloque? Un bloque es una colección de declaraciones de JavaScript casi siempre envueltas entre llaves. Por ejemplo, echemos un vistazo al siguiente código:

```js
```

Contando el par de llaves, aquí hay tres bloques. Un bloque es la región contenida por la propia función isItSafe:

```js
```

El segundo bloque es la región de la declaración if:

Haga clic aquí para ver la imagen del código

```js
```

El tercer bloque es la región cubierta por la instrucción else:

```js
```

Cualquier variable declarada dentro de un bloque usando let o const es local para ese bloque y cualquier bloque hijo contenido dentro de él. Para comprender mejor esto, eche un vistazo al siguiente código que es una variación de la función isItSafe de antes:

```js
```

Declaramos la variable total como parte del bloque de funciones. Estamos accediendo a esta variable dentro del bloque if. ¿Qué piensas tú que sucederá? La variable total es totalmente (¡jaja!) Accesible aquí, porque el bloque if es un hijo del bloque de funciones. Para ponerlo en la jerga de nuestro tiempo, la variable total se considera dentro del alcance de la función de alerta.

¿Qué pasa con la siguiente situación?

```js
```

Tenemos una variable llamada advertencia declarada dentro de nuestro bloque if, y tenemos una función de alerta que intenta imprimir el valor de la advertencia. En este caso, debido a que estamos tratando de acceder a la variable de advertencia en un bloque que está fuera de aquel en el que se declaró originalmente la variable, nuestra función de alerta no mostrará el valor de verdadero. Dado dónde está nuestra función de alerta, la variable de advertencia se considera fuera de alcance.

Nota de imagen

Declaración de variables con la palabra clave var!

Hace unos párrafos, mencioné casualmente que las variables una vez se declararon con la palabra clave var. Las palabras clave let (y const) fueron nuevas adiciones para ayudarlo a declarar variables, y dondequiera que haya usado var en el pasado, debería usar let en su lugar. Nunca discutimos por qué es preferible dejar y dijimos que lo discutiremos más a fondo cuando analicemos el alcance variable. ¡Bueno aquí estamos!

Variables declaradas con alcance var para funciones. No se dirigen a bloques como los nuestros if / else. Si modificamos el ejemplo anterior para que nuestra variable de advertencia se declare usando var en lugar de let, nuestro código se verá de la siguiente manera:

```js
```

Anteriormente, la función de alerta para advertencia no mostraba nada porque la variable de advertencia estaba fuera del alcance cuando se declaraba con let. Con var, ese no es el caso. Verá verdadero mostrado. La razón de esto se debe a la gran diferencia entre let y var. Las variables declaradas con var tienen un alcance en el nivel de la función, por lo que siempre que en algún lugar dentro de la función se declare la variable, esa variable se considera dentro del alcance. Las variables declaradas con let, como vimos anteriormente, tienen un alcance al nivel de bloque.

El nivel de indulgencia proporcionado por var en el departamento de alcance es demasiado, y esta indulgencia hace que sea fácil cometer errores relacionados con las variables. Por esta razón, prefiero que todos usemos let cuando se trata de declarar variables.

Cómo procesa JavaScript las variables
Si pensaba que la lógica de alcance del bloque anterior era extraña, espere hasta que vea esta. Eche un vistazo a t el siguiente código:

```js
```

Cuando se ejecuta este código, podemos afirmar razonablemente que el valor de Hello! será mostrado. Razonablemente tendríamos razón. ¿Qué pasa si realizamos la siguiente modificación donde movimos la declaración de variable y la inicialización al final?

```js
```

En esta situación, nuestro código generará un error. Se accede a la variable foo sin que se haga referencia a ella. Si reemplazamos let con una var, así es como se vería nuestro código:

```js
```

Cuando se ejecuta este código, el comportamiento es diferente al que vimos anteriormente. Verá indefinido mostrado. Qué está pasando aquí?

Cuando JavaScript encuentra un alcance (global, función, etc.), una de las primeras cosas que hace es escanear el cuerpo completo del código en busca de variables declaradas. Cuando encuentra alguna variable, la inicializa por defecto con undefined para var. Para let y const, deja las variables completamente sin inicializar. Por último, mueve las variables que encuentra a la parte superior del alcance: el bloque más cercano para let y const, la función más cercana para var.

Profundicemos para ver qué significa esto. Nuestro código inicialmente se ve así:

```js
```

Cuando JavaScript pasa esto, este código se convierte en lo siguiente:

```js
```

La variable foo, a pesar de estar declarada en la parte inferior de nuestro código, se eleva a la parte superior. Esto se conoce más formalmente como izar. Lo que pasa con let (y const) es que cuando se levantan, se dejan sin inicializar. Si intenta acceder a una variable no inicializada, nuestro código arrojará un error y se detendrá. Si modificamos nuestro ejemplo anterior para usar var, la forma en que JavaScript vería las cosas se vería de la siguiente manera:

```js
```

La variable aún se eleva, pero se inicializa como indefinida. Esto asegura que nuestro código aún se ejecute.

La principal conclusión de todo esto es la siguiente: declare e inicialice sus variables antes de usarlas. Si bien JavaScript tiene algunas posibilidades para tratar casos en los que no hacemos eso, esas posibilidades son terriblemente confusas.

Cierres
No se puede concluir ninguna conversación sobre el alcance variable sin discutir los cierres. Es decir, hasta ahora. No voy a explicar los cierres aquí, ya que es un tema un poco más avanzado que cubriremos por separado en el Capítulo 9.

Antes de pasar al siguiente capítulo, si tiene alguna pregunta sobre el contenido aquí, publique en los foros en https://forum.kirupa.com, donde yo y otros desarrolladores estaremos encantados de ayudarle.

<hr>

### El Mínimo Absoluto

El lugar donde viven sus variables tiene un gran impacto en el lugar donde se pueden usar. Las variables declaradas globalmente son accesibles para toda su aplicación. Las variables declaradas localmente solo serán accesibles para cualquier ámbito en el que se encuentren. Dentro del rango de variables globales y locales, JavaScript tiene muchas cosas bajo la manga.

Este capítulo le brindó una descripción general de cómo el alcance variable puede afectar su código, y verá algunos de estos conceptos presentados al frente y al centro en un futuro cercano.
