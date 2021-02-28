# 10 Laboratorio 2: Aplicación de la Lista de Tareas • 17 clases • :clock1: 1h 51m

* 103 Introducción a la sección 01:35
* 104 Temas puntuales de la sección 00:13
* 105 TODO: Demostración del programa que haremos al final de la sección 01:27
* 106 Inicio de proyecto - Todo 05:14
* 107 Todo Class 04:40
* 108 TodoList Class 08:08
* 109 Construir las tareas en el HTML 10:02
* 110 Evento para agregar un Todo 06:48
* 111 Marcar como completado un Todo 10:24
* 112 Eliminar un Todo 04:52
* 113 Eliminar Todos completados 08:49
* 114 LocalStorage y SessionStorage 06:42
* 115 Guardando y recuperando Todos 15:03
* 116 Reconstruyendo instancias de Todos 10:13
* 117 Aplicar filtros 09:52
* 118 Todos en la GitHub Pages 06:43
* 119 Código fuente de la sección 00:05

## 103 Introducción a la sección 01:35

Estamos entrando a la sección 10 del curso la cual es otro laboratorio en la cual vamos a poner en práctica todo lo que hemos aprendido hasta el momento.

Utilizaremos wiipad utilizaremos clases importación de módulos haremos persistente nuestra información  utilizando el cesion y el Local Storage.

También desplegaremos todo dijo Telles.

Para asegurarnos de que nuestra aplicación funcione en todo lugar ahora hay otra cosa que les quiero mencionar.

Trabajar con Wolfpack y la estructura de El sistema usa los directorios que usted va a crear dentro varía mucho dependiendo de la librería que ustedes utilicen ya que por lo cual yo les voy a decir a ustedes les aconsejo que sigan los lineamientos que dichas librerías y dicho framework se les aconseje en las buenas prácticas.

Por qué.

Porque ustedes perfectamente pueden crear sus directorios como quieran y al fin de cuentas esto se va a empaquetar todo y va a crear un solo bóndi pero dependerá de dichos lineamientos de esas librerías y frameworks.

Pero por momentos ustedes en este curso van a haber una manera estándar de trabajar más adelante vamos a crear ciertos procedimientos que nos permitan ejecutar la inicialización de algún componente o alguna página y van a ver por qué si ya han trabajado con otros frameworks y librerías se van a dar cuenta del por qué tiene su ciclo de vida y cómo es que funciona eso.

Espero que más o menos cuando ustedes lo vean lo puedan asociar de que digan Ah por eso es que que hace esto.

Ah por eso es que amolar hace esto de esta manera y ese es el objetivo.

Pero bueno vamos a aprender muchas cosas interesantes reforzar otras cosas y los veo en el siguiente video.

## 104 Temas puntuales de la sección 00:13

En esta sección tocaremos los siguientes temas:

* Webpack
* Uso de clases
* Uso del LocalStorage y SessionStorage
* Importaciones
* Módulos
* Lógica para el manejo de todos
* Despliegues
* Arreglos
* Más...

Esta sección aplicaremos lo que aprendimos en Webpack para crear una aplicación que podamos utilizar, desplegar y probar en múltiples navegadores sin importar que usemos características de la última versión de JavaScript.

## 105 TODO: Demostración del programa que haremos al final de la sección 01:27

Esto es lo que vamos a hacer en esta sección.

Crearemos una aplicación de listas de tareas en la cual nosotros podemos agregar lo que queramos.

3.
4.
5 Enter.

Podemos borrarlos acá marcar como completados aplicar filtros.

Quiero ver todos los completados todos los pendientes.

También puedo borrar todos los completados y así sucesivamente.

Quiero que no tengo que poner aquí 3 tú y yo 5 tú 10 lo que sea quiero que noten que si toco el botón de refresh todos mis tubos permanecen ahí.

Por qué.

Porque estamos también trabajando mediante o si no saca a la pestaña de Application locales Storage y quiero que noten que todos mis tubos están almacenados acá.

Eso lo veremos en esta sección también yo los puedo borrar en tiempo real esto se está limpiando.

Como ustedes pueden observar y ahí va otra cosa que quiero que ustedes noten es el wherever en el cual está corriendo la aplicación.

Esto lo hemos desplegado en pellets de tal manera que cualquier persona en cualquier lugar del mundo va a poder observar su aplicación de JavaScript funcionando.

Si nos vamos a la pestaña de Sources también quiero que noten que nuestra aplicación está optimizada para funcionar con navegadores web viejos y adicionalmente todo mi código está ofuscado y en una sola línea.

Todo esto es lo que vamos a hacer en esta sección.

Espero que estén emocionados que estén con ánimos de aprender y los veo en el próximo video.

## 106 Inicio de proyecto - Todo 05:14

Comencemos con este proyecto.

Les voy a pedir que se descarguen el material adjuntó un archivo comprimido que les comprimirlo tiene esos dos estos dos archivos son índex HTML y un punto CSS.

Si quieren ustedes lo pueden abrir o pueden hojear.

Ya les voy a explicar de dónde obtuvo el código fuente de acá no se preocupen.

Y estos son los estilos.

No va a funcionar todavía la aplicación porque vamos a tener que utilizar Wolfpack porque es la manera moderna de trabajar o es la manera en la cual yo quiero que nosotros sigamos trabajando.

Los futuros proyectos también en el material adjunto.

Ustedes van a encontrar el enlace que lo lleva al repositorio que yo creé en la sección pasada.

Si ustedes no saben qué fue lo que hice no se preocupen pues básicamente ya es la configuración del web como nosotros la dejamos en la sección propiamente del Wattpad.

Entonces les voy a pedir que lo descarguemos aquí como un zip.

Voy a cerrar esto ahora ya lo tengo yo tengo el proyecto acá tengo mi proyecto lo voy a descomprimir no voy a borrar eso y este es básicamente todo mi proyecto como yo lo había dejado es mi cascarón para no tener que rehacer todas las configuración anterior del Wolfpack porque qué pereza volverlo a hacer.

Entonces este directorio lo vamos a colocar dentro de la carpeta JavaScript y dentro de ella que le vamos a poner a este proyecto 04 menos todo van a presionar enter.

Tomen la carpeta déjenla dentro de Visual Studio o su editor de texto favorito en el editor favorito de ustedes y tendremos que reconstruir los módulos de noted.

Para eso voy a escribir:

```sh
npm install
```

Esto tiene que hacer el procedimiento.

Esperamos un segundo debería tardar mucho y bueno claro eso depende de la velocidad suya de Internet pero no lo dejamos que haga el mismo, no se preocupen de estar a punto de terminar.

Perfecto termina y ahora podemos ejecutar:

```sh
npm start
```

para que lance y bueno ya ahora mi aplicación para que me permita a mí desarrollar de una manera rápida, siempre dejemos las herramientas de desarrollo al lado y esto es como yo necesito que esté la aplicación por lo menos para el inicio.


Voy a cerrar la terminal con la X, no con el basurero porque esto termina el procedimiento, con la X y hagamos el Source y aquí tengo índex que tiene esta información y acá no esto me va a servir entonces les voy a pedir ahora que tomemos el archivo índex lo vamos a poner aquí dentro de Visual Studio Code COPINH sé todo lo que esté aquí con controlado Cumana lo copian con control C y reemplazan todo el código que tiene el índex actual por este índex junto a HTML y graban los cambios.

Si ustedes regresan a la aplicación van a ver que ahora tenemos esto que se mira aún peor pero por menos ya tenemos aquí el HTML excelente.

Ok.

Antes de continuar con los estilos bajen un poco y van a notar que hay varios comentarios que esto obviamente no todo lo hice.

Hay unas cosas que yo traduje y en fin todo este código yo le extraje de este sitio web que es todo en bici hay un bueno ya está hecho este ejercicio de muchas formas con fines educativos para estudiantes ustedes lo pueden hojear si así lo desean.

Pero todo este código nosotros lo vamos a hacer a nuestra manera.

Y bueno ahí tenemos otros otros enlaces y ahí están las referencias y aquí también está el temple por la persona que lo hizo ahí está su sitio web ustedes pueden ir ahí si así lo desean.

Ahora me falta el estáel como ustedes pueden ver aquí tengo el HTML body color tal.

Este es los estilos globales perfectamente lo puedo poner acá entonces voy a pedir que ahora hagamos lo mismo con el estaes juntos CSS lo podemos reemplazar ahí pero lo que yo voy a ocupar es que copien todo el estáel que yo les pasé el material adjunto y lo reemplacen por el Estado que tenemos en nuestro proyecto.

Ok todo esto este montón de líneas.

Entonces ustedes graban los cambios van a revisar a su aplicación y debería de verse de esta manera.

Obviamente aquí dice hola fernando no se preocupen ya vamos a quitar eso pero tenemos nuestra aplicación lista para empezar a trabajar y crear.

Bueno empezar a crear actividades de tareas por hacer o listas de todos tenemos la información acá y pueden jugar un poco con el código HTML pero les voy a pedir que tengan cuidado porque nos va a servir bastante para cuando estemos trabajando y creando sus elementos.

Voy a seleccionar todo esto voy a quitar el comentario grabar los cambios revisar acá y van a ver que quise probar JavaScript como una lista de tareas que lleváis.

Hay un botón para eliminar hay un check y entre otras cosas si regreso acá y ahora voy a quitar este otro comentario con controles las gravó los cambios y aquí tenemos una lista de tareas que no está terminada.

Ustedes van a notar que para marcar una tarea como terminado en el LG o analista ordenada tenemos acá este modo tenemos que agregar a la clase cumplir y en el check box que es este elemento que tenemos acá hay que agregarle la Classic check para que aparezca el checo esta palomilla.

Cómo le digo a ustedes que vamos a trabajar con estos botones para aplicar filtros entre otras cosas plegamientos.

Esto es todo lo que yo necesito que tengan por favor dejen un comentario bueno les he comentado esto porque la idea es que los creamos nosotros mediante Javascript y hagamos funcionar esta aplicación con lo que hemos aprendido.

Entonces dejémoslo así y los veo en la siguiente clase.


## 107 Todo Class 04:40

Ok comencemos con la lógica de nuestra aplicación.

Regresemos a El código de buenas que tenemos en el estudio Coupet dentro de la carpeta Source.

Voy a quedarme un nuevo directorio llamado clases.

También los podríamos colocar dentro de las carpetas J.V aunque ya depende mucho de cómo quieren manejar ustedes la estructura de directorios.

Pero le voy a poner clases o clases ya dentro de clases clic derecho nuevo archivo y queremos nuestra primera clase se va a llamar todo punto clase punto J.V noten que el punto clases realmente no es obligatorio que yo lo ponga.

Pero de esta manera va a quedar bastante claro de que este archivo sólo va a contener la información de esta clase pero también es bueno que cuando ustedes estén trabajando con algún framework se apeguen a las reglas de ese Framework en este caso yo voy a definirlo todo apuntó Clas junto a J.V presionã entrevistamos en el archivo hay varias cosas que yo quiero manejar en la lista de tareas.

Si nosotros realizamos esto nosotros tendríamos cuando se creó la tarea.

Podríamos identificar las tareas con algún Heydi identificar si está completada o no. Hay varios juegos que nosotros vamos a ocupar.

Entonces comencemos lo primero como esta clase la voy a utilizar fuera de este archivo tengo que poner la palabra reservada Export class is a llamar Dudú o el nombre que ustedes quieran darle pero yo lo voy a manejar como un todo.

Haremos el constructor pero constructor pero no habrá hojas y aquí el constructor.

Básicamente lo único que yo tendría que recibir es la tarea o la descripción de lo que yo tengo que hacer.

Lo demás yo lo voy a calcular en el momento.

Por qué.

Porque cuando yo quiero una nueva tarea obviamente está sin completar.

O sea está pendiente obviamente la fecha de creación por ejemplo es el momento actual.

Entonces hay varias cosas que yo necesito que puedo deducir de manera automática.

Entonces digamos disputo tarea va a ser igual a la tarea que yo recibo por el argumento.

Por ejemplo aprender JavaScript aprender Payton aprender PHP o comprar leche cualquier cosa lo demás que yo voy a poner en esta clase lo voy a definir en este momento.

Por ejemplo yo voy a ocupar un identificador único de la tarea le voy a poner ahí y esto va a ser igual a una manera sencilla de crear un Heydi que realmente puede ser duplicado pero para nuestro ejercicio jamás va a ser duplicado.

Va a ser el Newgate que ya hablaremos sobre las fechas pronto y eso me crea un objeto con una fecha y hora actual pero si yo pongo el punto gibt Time yo voy a tener información como unos números parecidos a estos.

Qué es la representación actual de la hora minuto segundo milisegundo del momento actual.

Entonces eso me va a servir para manejarlo como un Ardi.

Personalmente voy a decir que disputo completado completado.

Digamos que ese es el que me va a decir si la tarea está terminada o no voy a poner como Fox entre disputo y pongamos la fecha de creación creado.

No voy a poner así es igual a Newsday.

Hay algo sencillo.

Algo así está ahí.

Entonces cada vez que yo crea una nueva tarea simplemente tengo que mandar lo que necesito hacer y automáticamente me crea todo esto.

Entonces voy a grabar los cambios voy a regresar al índex punto J.V.

Todo esto lo puedo borrar.

Dejemos este Staël porque es necesario para que incluya nuestro estilo globales y hagamos una simple prueba.

Voy a crearme una constante llamada tarea es igual a new Dudú parentesis Punto y Coma asegúrese de importar todo de acá de este lugar.

Perfecto.

Usualmente prefiero dejar los estilos acá y o bien al inicio porque puede ser que esto sea lo primero que necesito construir eso por lo menos no lo voy a utilizar y lo voy a dar de esta manera.

New todo y todo necesito mandarle alguna actividad como por ejemplo pongámosle aprender JavaScript o hagamos un solo de la tarea para ver qué sucede.

Voy a grabar los cambios voy a regresar a qué navegador web y ustedes van a notar que automáticamente se está ejecutando el código.

La tarea es aprender JavaScript.

Este es el Heydi que es en base a la fecha completado falso y tengo la fecha de creación que es el objeto de JavaScript de la mano de la fecha actual y eso está bien.

Básicamente eso es todo lo que yo tengo que hacer en el momento en que yo escriba acá y presione Enter.

Voy a tomar esto y ese valor del street que voy a recuperar del campo de texto se lo voy a asignar al valor de la tarea y voy a crear una nueva instancia de mi clase.

Pero básicamente eso es todo lo que yo necesito por los momentos.

Eventualmente tendré que agregarle un par de lógica adicional acá pero no lo quiero poner hasta que no miremos la necesidad por lo menos eso es todo lo que yo quiero hacer con el tuplas y los veo en el siguiente video.

## 108 TodoList Class 08:08

Bien se me ocurre que ahora yo necesito almacenar todos mis tareas pendientes por hacer en un arreglo algo como constante todos va a ser igual un arreglo vacío y luego tendría que estar tomando cada vez que era una tarea estar insertando dentro de los tubos.

En teoría si fuera así de sencillo está bien pero yo tengo que pensar en que voy a tener otros procedimientos como por ejemplo cambiar cuando una tarea se completa o no borrarlas borrar todas y aplicar estos filtros.

No se preocupe por estos errores es que yo baje el servidor lo bajé como ustedes pueden observar y lo voy a volver a levantar.

Entonces tenemos ese inconveniente y se me ocurre que lo mejor es que nosotros queremos una clase especializada para manejar todo lo referente a mi lista de tus alumnos a la carpeta clases click derecho nuevo archivo.

Vamos a ponerle nombre tu menos lista apuntó Class J.V.

Recuerden seguir el patrón de desarrollo o los lineamientos de nomenclatura de los archivos.

Dependiendo del framework que ustedes utilicen en lo particular a mí me gusta seguir este patrón porque queda bastante claro que es cada cosa.

Entonces este edulis va a agrupar toda mi lista de todos entonces exportarlas tú les abrís Rojas.

Recuerden que estoy utilizando Horkheimer Keys porque son clases.

El estándar dice que con ustedes quedan clases los nombres de las clases la primera letra siempre tiene que estar capitalizada y todas las demás palabras también ok quedémonos el constructor y lo único que voy a hacer el constructor es crearme un arreglo de y lo inicializar vacío.

Eso es todo lo que voy a hacer por momentos en el constructor.

Adicionalmente pensemos por adelantado un par de métodos que yo voy a ocupar yo voy a manejar utilizando una instancia de la clase todos estos todos por consecuencia voy a ocupar algo para crear un nuevo todo ok ahora dice Rojas.

Lo único que voy a hacer con este nuevo tubo yo debería recibir un turbo o una tarea por hacer y lo voy a insertar en este arreglo.

Entonces sería despuntó tu 2.Los y voy a insertar el turbo que recibo.

Eso es básicamente todo por los momentos agregaríamos una línea más también si tengo algo para agregar debería tener alguna opción que me permita a mí borrar todos con una X que aparecía al lado del tubo.

Entonces creamos ese botón o ese método perdón eliminar todo y para eliminar el todos nosotros podíamos recibir también todo o si quieren simplemente el Heydi de la tarea que yo necesito eliminar.

Eso lo vamos a implementar luego pero ahora sólo implementamos los métodos generales también voy a cambiar si estaba marcado a si estaba completado no completado y si estaba no completado a completado le podríamos poner nombre todo tú vamos a ponerle de nombre marcar completado o todo el buen nombre que ustedes quieran ya lo vamos a cambiar si fuera necesario y también ocuparía saber cuál es el Heydi del tubo que yo necesito.

También puedo mandar el todo completo pero sólo voy a mandar el Agri para que sea un poco más simple y dependiendo del Heydi yo voy a buscar Saidi en mi arreglo de todos y si estaba completado lo marcó como no completado y si estaba no completado lo voy a marcar como completado.

Ese es el objetivo de este método también si miramos el código aquí tenemos un botón o vamos a tener un botón qué debería disparar una acción para borrar todos los completados y eso borrar todos los completados debería estar también en esta clase.

Voy a poner acá eliminar completados.

No deberíamos de recibir ningún argumento porque ya sabemos tenemos una instancia donde están todos mis dudas.

Simplemente voy a barrer el arreglo y eliminar todos los que tengan todo igual.

Eso es básicamente todo por ahora simplemente voy a definir estos métodos.

Regresemos a nuestro Index y crea uno saca la instancia del todo listo constante.

Oponerle Turu list es igual a new Dudu List Tapp parentesis punto y coma.

Asegúrese de importar este todo List de su archivo.

Ahora voy a grabar los cambios y ustedes van a ver lo siguiente aquí yo estoy viendo que tengo dos importaciones.

No está mal.

No podemos dejar así pero qué pasaría si más adelante tenemos cinco seis siete clases entonces serían cinco 6 7 importaciones que yo necesitaría en este archivo y eso se ve un poco feo lo que podríamos hacer es un pequeño truco que les puede servir para reducir eso es que aquí en la carpeta clases voy a hacer click derecho nuevo archivo y necesito que le pongan aquí sí el nombre índex apuntó J.S. iban a presionar enter este archivo de índex me va a servir para agrupar todas las clases que yo tengo en esta carpeta y exportarlas para que en lugar de que lo importemos así tengamos un único lugar centralizado de importaciones de clases.

Para eso necesito importar mis archivos puedo poner import algo from slats y Class puntico y también el todo menos listo todo menos Liset class.

Aquí va a importar el Dudú y aquí está el Turu listo que tengo las dos importaciones exactamente igual que las tengo acá pero ahora voy a hacer un Export y voy a exportar el Turu y también voy a exportar él todo listo.

Voy a grabar los cambios y esto es todo lo que tengo acá.

Si yo agregar a otra clase lo importo acá y la exporto de esa manera mi archivo índex punto ese es el que contiene todas las referencias a todas las clases.

Voy a cerrar el Index y aquí puedo comentar estas dos líneas y hacer una única importación del archivo juntos las clases.

Nada más eso porque cuando nosotros especificamos lo dejamos así estamos en este directorio y no especificamos ningún otro nombre entonces va a buscar el Index pu.to J.S. por defecto.

Entonces aquí ya vamos a poder hacer la importación del todo y todo listo.

Y queda mucho más fácil hacer esta importación que tener varias líneas como éstas.

Voy a borrar esto grabar los cambios y levantemos el procedimiento MPM Start que en mi caso yo lo bajé sin querer cerrar esto o cerrar esto descargar acá y aquí tenemos todo funcionando correctamente pero antes de terminar el video se acuerdan que lo que yo quiero hacer es que en mi tu edulis quiero manejar aquí toda la lista de las tareas y ya tengo un método para crear eso el cual recibió un todo y agrega Y entonces va vámonos a nuestro índex y en lugar de hacer de todo así nada más en lugar de hacer este impresión de consola una vez creada la tarea yo lo que voy a hacer es un todo listo punto nuevo tu parentesis y voy a mandar la tarea puntico.

Ahora en primamos en consola todo listo.

Voy a grabar los cambios.

Voy a regresar al navegador web y ya recargó y ustedes van a ver que tenemos la clase o la instancia del edulis que adentro tiene mis todos y aquí dice.

Ustedes pueden observar que dice que lo que tiene adentro es un arreglo y adentro hay un Turu excelente.

Me está reconociendo bien las clases y tenemos la tarea aprender ya que el día en el que se crea el Heydi único completado falso y la fecha de creación se creará otro.

Por ejemplo crear otra tarea aprender JavaScript.

Voy a poder comprar un unicornio loscambios voy a regresar acá y aquí lo puse como una constante.

Voy a crear tarea dos tareas dos voy a llamar esto con toreados pregrabados cambios voy a revisar un navegador web y ahora tengo dos tuus excelente uno es aprender JavaScript y el otro es comprar un unicornio.

Ahora aquí ustedes van a poder observar qué es exactamente el mismo Heydi pero en la vida real esto no va a pasar porque la persona no va a poder escribir dos tuus tan rápido ok envía código si puede ser que suceda pero yo no lo voy a hacer así en la realidad lo que nosotros sabíamos es mandar una información al servidor y el servidor es quien me crea un Heydi ok pero esto va a servir por ahora no se preocupen si es el mismo eso lo vamos a arreglar después.

Bueno eso es todo lo que quiero hablar por los momentos en la próxima clase vamos a implementar los demás métodos que nosotros vamos a ocupar en nuestro todo. Las.

## 109 Construir las tareas en el HTML 10:02

Yo sé que les dije en el video anterior que íbamos a crear los métodos pero eso mejor lo hacemos bajo demanda disculpas por eso que no se preocupen no piensen que me salte un video ni nada por él ni nada por el estilo.

Lo que quiero hacer en esta clase es enfocarme en la creación de los elementos en el HTML de mis componentes específicos de los tubos.

Es decir aquí yo ya tengo uno que es aprender JavaScript y quiero que aparezca acá tengo otro que es comprar un unicornio aunque eso lo vamos a manejar.

Uno de los momentos iba aparecer abajo entonces si quieren borremos el del unicornio y dejemos solo una tarea.

Ok dejémoslo así tenemos el consolon también nos va a servir mezclamos los cambios en el Index obviamente esto se recarga y sólo tenemos un turno excelente vamos a crear un nuevo archivo o trabajar mejor con el que ya tenemos aquí de componentes.

Nada de lo que está acá me va a servir lo voy a borrar y trabajemos en este archivo.

Recuerden que este archivo ya estaba creado y si ustedes no lo tienen simplemente póngalo ahí lo crean y ya lo que yo voy a ocupar acá es un método que me permita crear en el html ese bueno todo muy parecido como lo tenemos aquí en el index.

Por momentos voy a ponerle exporto no estoy muy seguro si esto lo voy a exportar o no. Ya vamos a ver en base a la necesidad iba a ser constante y se va a llamar crear tu HTML HTML es el nombre que ustedes quieran darle pero esto va a ser igual a una función de flecha horillas ok yo voy a necesitar recibir un todo y en base a ese todo es lo que yo voy a construir en el html.

Entonces vamos al Index punto HTML y básicamente lo que yo necesito es recrear todo este Elai que todo este lo necesito construir yo para insertarlo dentro de la lista ordenada que tengo acá de este edulis.

Entonces uno saca componentes de uno es una constante llamada HTML y todo esto va a ser igual y póngalo con Baketik porque esto me permite insertar caracteres en Multicines multilatina de como un estudio multi línea podemos decir así también me va a permitir a mí hacer interpolación de string para cambiar ciertas cosas.

Nosotros vamos a tener que básicamente llenar esta información.

Comencemos con el más sencillo que es el Lebel que dice probar JavaScript en base al todo G.M. abrir tu clase para ver sus métodos.

Aquí tenemos una tarea esa tarea es la que debe aparecer aquí adentro.

Entonces sabemos que esa información vienen estudo a borrar este probar JavaScript.

Voy a usar un símbolo de dólar y la interpolación de string y voy a hacer voy a decir el punto y lo habíamos puesto tarea o descripción tarea le pusimos tarea Ok voy a grabar los cambios y eso es lo que estoy haciendo por los momentos que aún me faltan cosas por editar pero lo voy a dejar por lo menos sólo con geste de alguna manera.

Yo voy a ocupar las referencias HTML al elemento que tengo acá.

Noten que está por Klaus okey Dudu se llama dull list.

Entonces voy a tomar este nombre voy a copiar regresar a mis componentes y aquí voy a crearme las referencias referencias en HTML.

Entonces creamos la primera referencia que va a ser todo listo constante se va a llamar DIV Turu List y esto va a ser igual a document puntos Kuerten selector y voy a obtener el List perfecto.

Voy a copiar esto y aquí abajo lo voy a utilizar.

Pero saben que antes de utilizarlo necesito crear el elemento HTML porque todavía no lo tengo.

Esto es simplemente es un string de lo que yo voy a ocupar.

Entonces voy a crearme el elemento HTML constante Dip así lo voy a poner y esto va a ser igual al documento apuntó.

Create Element parentesis y me voy a crear un div.

Yo sé que eso será un poco extraño me van a decir por qué estás creando.

No debería ser un LMI Sí y no. Sí debería ser un eloi Pero noten que aquí tengo la configuración y necesito poner esta clase y tengo un Heydi que voy a ocupar también lo ocupo poner ahí.

Entonces necesito crearme un elemento que contenga esa lista ordenada.

Entonces voy a presionar enter.

Voy a decir que el punto Inner HTML va a ser igual a todo el elemento HTML que tengo del todo Póntico.

Una vez hecho eso ahora sí puedo insertarlo acá DIV todo listo punto y por los momentos voy a ser el Append Append parentesis y o insertar el DIB pero en teoría esta función lo que debería de retornar es el video en teoría por qué.

Porque esa función de crear todo lo que va a hacer regresar el elemento HTML y en otro lugar voy a hacer la inserción.

Voy a grabar los cambios y vamos a ver si esto funciona.

Note que lo estoy exportando se llama crear todo.

Voy a regresar a mi índex punto J.V que aquí es donde yo tengo mi tarea.

Vamos a probar si esto funciona.

Taub asegúrese de que lo importe.

Aquí tenemos la importación y lo que necesita esto es el todo que en nuestro archivo se llama tarea que es aprender JavaScript.

Voy a poner un par de signos de admiración que voy a mandar la tarea.

Punto y Coma voy a grabar los cambios voy a revisar el navegador web y aquí tengo aprender JavaScript.

Excelente noticia salió con notables signos de admiración porque son los que yo puse acá.

Si yo los borro y grabo los cambios van a notar que aquí ya desaparecen.

Recuerdan que lo hace muy muy rápido y por eso es que da la impresión de que se instantaneo.

Ahora podemos jugar con estas con este CHEC y podemos jugar con este tachado que tenemos acá.

Si nosotros regresamos a nuestros componentes y quitábamos este cumpliré lo borro y grabo los cambios.

Voy a regresar acá.

Noten que se quita el tachado que tenía ahí esta clase de la que me permite a mí controlar eso y si yo quito aquí la palabra checked entonces en el imput no aparecer el check por defecto.

Entonces tenemos que jugar con insultos con estos dos valores y por suerte ya que tiene lo que el operador condicional ternario.

Se acuerdan que lo habíamos visto anteriormente en el curso lo podemos implementar exactamente aquí.

Muy útil mediante la interpolación de string.

Voy a poner un símbolo de dólar ahorro y cero llaves.

Y recuerden que lo que sea que yo ponga aquí adentro tiene que ser una expresión de JavaScript válida como un operador condicional ternario entonces la condición que yo voy a utilizar para evaluar va a ser un todo punto completado.

Recuerden que este completado es este que tenemos acá y por defecto es un villano excelente entonces no tengo que hacer nada si completado Estruch entonces voy a poner la clase cumpliré pero lo escribimos bien con flirt no como lo escribí.

Por favor póngalo bien y si no entonces no voy a poner nada porque no necesito que aparezca esa clase entonces voy a grabar los cambios voy a regresar a navegador web y recargo y no está tachado.

Por qué.

Porque por defecto todo por defecto mi todo es tan marcado como completado igual falso podemos hacer la prueba.

Si voy aquí a mi índex aquí tengo la tarea.

Puedo decir que la tarea autocompletado igual.

Trump grabó los cambios.

Entonces debería aparecer tachado.

Excelente.

Ahora hagamos lo mismo con el otro lugar.

Entonces revisamos a componentes y hagan ustedes ahora mismo impriman este cheque si está completado o no.

Entonces pongan de paso el video e intenten hacer eso ustedes es exactamente igual a esto pero intenten hacerlo ustedes.

Yo regreso con la solución en breve.

Así que ahora ok lo lograron hacer tuvieron conveniente.

Espero que no. Es bastante sencillo básicamente era copiar esto y voy a reemplazar la palabra checked por esta condición igual completado y si está completado entonces es la palabra checked.

De esta manera y si no no pongo nada voy a grabar los cambios puedo regresar al navegador web y aquí aparece con el check excelente empezamos a blindex voy a borrar esta línea los cambios y ahí está perfecto.

Todavía hay algo que quiero hacer en uno de los componentes y es que aquí yo estoy almacenando o que quiero almacenar aquí el Heydi del elemento.

Por qué.

Porque después simplemente cuando yo haga clic en algún por ejemplo en la X en algún lugar yo necesito identificar a qué elemento yo le hice clic para saber cuál fue soy y en base a eso poderlo eliminar.

Entonces aquí voy a poner el punto ahí voy a grabar los cambios y aunque en teoría ya terminamos hay algo que quiero que ustedes noten.

Voy a inspeccionar este elemento aquí tenemos un saber tenemos nuestra lista de todos bajamos un poco y aquí está este div.

Este viernes todo el elemento pero realmente no es muy buena práctica que si es una lista ordenada en lugar de un L y tengamos un DIV realmente este lo tenemos que eliminar no lo ocupamos acá simplemente yo lo creé para poder insertarle todo ese HTML entonces en lugar de insertar y en lugar de insertar todo el HTML en lugar de insertar Lundy lo único que me va a interesar a mí es que inserte el primer hijo que en este caso el primer hijo sería mi L'Illa creado entonces aquí voy a hacer el APEN del punto first Element Child no voy a grabar los cambios voy a regresar al navegador web recargo y inspeccionamos nuevamente esto vamos a ver tenemos nuestro huelen que es el Todolí bajo un poco y aquí tenemos inmediatamente el Lehi ok aquí está Miele y ya después viene todo lo que es la lista ordenada o el liciten perdón.

Entonces esto es exactamente lo que yo necesito y así lo voy a dejar.

Espero que me hayan comprendido por qué extraje el del DIP.

De esta manera me permite crear un elemento ya con sus nodos y toda la cosa pero sólo me interesa que este estándar esté elegí al elemento.

Lo mismo voy a hacer aquí abajo sólo para estar seguro de que voy a cuando utilice este método.

Regrese ese elemento ya el HTML.

Esto es todo lo que voy a hacer en esta clase.

Pero que me lo han comprendido y los veo en el siguiente video.

## 110 Evento para agregar un Todo 06:48

Ok continuemos.

Por un momento lo único que tenemos acá es el tubo creado pero lo estamos creando manualmente.

Lo que quiero ser ahora es escribir acá como ejemplo comprar algo y presionar ENTER y presionar ENTER

eso aparezca como una lista quien tuvo que hacer eso lo puedo crear aclaró también como las referencias

HTML y hacer una lista negra.

También puedes crear un archivo independiente pero no es mucho lo que vamos a hacer voy crear una constante

para manejar la referencia al IMPUT.

Vamos a ver cómo se llama IMPUT.

Tenemos que buscar acá porque aquí está es un imput y tiene una clase ni todo eso es lo que yo voy a

ocupar para seleccionar este input y poder agregar el Eben Listen.

Entonces voy a ponerle txt input esto es igual a Tocumen apuntó QWERTY selector parentesis y de la misma

manera ni YouTube recuerden que eso está apuntando a este input excelente.

Tomemos este txt input abajo de crear todo.

Voy a poner aquí eventos podemos txt input punto a tener paréntesis y necesito el evento que voy está

escuchando que es el Kirov es decir cuando la persona suelta la tecla y cuando suelta la tecla voy a

disparar.

Esta acción también es importante que ustedes pongan aquí el evento.

El evento les va a decir que Tecla fue la que presionó al usuario podemos poner un consolón del crimen

para que lo miremos hagamos los cambios vamos a regresar al navegador web y voy a empezar a escribir

algo ok ven y aparecen todos los eventos.

Aquí está la tecla y todas la cosa hay dos cosas que me van a interesar acá.

Uno voy a irme aquí el último abrir el último el último 1 que me interesa es el Balio.

No sé si lo podemos ver por acá que vamos a ver aquí se abrió.

Vamos a ver si tenemos el valioso está desordenado pero en algún lado tendremos el value target.

Vamos a ver si tenemos el target de aquí el Balio aquí está el valio que es lo que la persona terminó

por escribir.

Este es el valor que me interesa y también hay otro valor importante que es el Coded este de acá el

chico.

Básicamente me dice a mí qué tecla fue la que presionó al usuario porque va a ser importante diferenciar

entre si presiona por ejemplo Enter.

Notemos que el chico del enter es 13 y si ustedes presionaron enter apareció otro número.

Ese sería el número que va a tener que usar y diferenciarlo entre cualquier otra tecla.

Por ejemplo la flecha direccional arriba.

El chico es diferente entonces tengo que trabajar en base al 13.

Regresemos acá.

Voy a quitar esa consola porque ya no lo necesito.

Voy a tener que hacer una condición tengo que evaluar si había puesto Live.

Voy a evaluar si el punto chico es exactamente igual a 13.

Entonces significa que la persona presionó Enter.

Entonces ahora desarrollarás cuando yo presionado voy a crearme un nuevo todo constante nuevo todo va

a ser igual a new tu tap Box Tutu no pareció el todo.

Vamos a ver si lo podemos importar entonces hagamos la importación algo from Pontus las punto.com las

clases nada mas eso y me interesa él todo ok.

Con esto voy a ponerlo todo y voy a mandar lo que la persona escribió.

Entonces eso estaría en el txt input punto Balio y si no estoy mal creo que lo puedo obtener de esa

manera.

Vamos a ver si es cierto solo para estar seguros creo que se puede obtener así voy a grabar los cambios

si no tendríamos que apuntar al target pero bueno vamos a probar.

Aquí ya recargó empezar a escribir a veces y presionar ENTER.

Y ahí está bueno a pesar de que Villaveces a MS pero bueno al presionar enter ustedes van a ver que

estamos recibiendo el valor.

El único inconveniente es que la persona puede ser que haga click en el lugar y presione Enter.

Y yo tengo que evaluar que no sea un estro invasivo.

Entonces esa es otra condición que voy a tener que bueno prevenir o tengo que hacer una validación para

que la persona no puede insertar caracteres vacíos entonces hagámoslo de una vez y si el txt input punto

Balio punto length Leng.

De esta manera si eso es mayor a cero entonces voy a ejecutar este código si no voy a ignorarlo perfecto

ya tengo el Balio y ya tengo creado el todo lo que seguiría es que tengo que insertar este nuevo Turu

en mi arreglo vamos a usarlo tengo que insertarlo en mi arreglo de éste todo listo entonces voy okupar

insertar o hacer una importación import algo from conducirlas del Index necesito mi instancia del todo

list del todo listo pero no me está pareciendo asegurémonos de exportarlo para poder importar este archivo

o este objeto para poder importar grabemos los cambios aquí para poderlo importar acá entonces aquí

sí deberíamos de ver el todo listo ok si sale correctamente entonces somos este todo listo.

Recuerden que todos los objetos en Yaguas que pasan por referencia y eso ves perfectamente lo que yo

necesito.

Punto y ya vemos el método del todo lo que es nuevo.

Todo todo todo y Coma Ok voy a grabar los cambios pero si lo dejo así como está voy a tener que imprimir

todo listo para ver si efectivamente me insertó grabemos ahora si todos los cambios regresemos al navegador

web.

Voy a poner algo como comprar un unicornio presionó Enter.

Ahora tengo todo listo ahora tengo dos elementos que uno es aprender JavaScript excelente y el otro

es comprar un unicornio pero no apareció en el html y eso era de esperarse porque para insertarlo en

el html voy a ocupar llamar mi método que acabamos de crear en la clase anterior que es crear un HTML.

Entonces voy a llamar ese método qué hacer crear todo HTML parentesis si voy a mandar el nuevo todo

punto y coma voy a grabar los cambios eso debería ser todo un navegador web.

Vamos a ver comprar unicornio pero no entre y perfecto ya lo agrego pero ahora tenemos otro problema

que imagino que ya más de uno de ustedes vio y es que debería de borrarse esto cuando yo presionó Enter

para borrarlo es bastante sencillo.

Después de haber insertado voy a decir que el txt input punto válido va a ser igual a un estro invasivo.

Eso es básicamente todo.

Grabamos los cambios aquí se purgó el unicornio porque todo está en memoria y cada vez que se refresca

se vacía la memoria.

Comprar unicornio inocente y perfecto se borra y estoy listo para insertar otra cosa.

A ver qué excelente pero cuando un navegador web se pierde todo.

Luego vamos a hacer que esa información sea persistente utilizando el local storage.

Pero ya llegaremos a eso por lo menos eso es todo lo que me interesa.

Lo dejamos así y los veo en la siguiente clase.

## 111 Marcar como completado un Todo 10:24

Es momento de trabajar con la parte de cambiar este valor es decir cuando yo hago click que también

se aplica la clase y que en mi objeto de edulis cambiar el valor de este todo completado.

Si ya hice click acá.

Entonces hay varias cosas que hacer para comenzar.

Lo primero es abrir la clase y enfocarnos en marcar completado.

Todavía no tengo la lógica y lo voy a hacer de una vez.

Bueno hay muchas formas de trabajar con esto.

Una sería que en lugar de un arreglo fuera un objeto y cada una de las de las llaves sea el Heydi.

Eso es algo bastante interesante que se puede hacer pero estoy decidiendo Bueno yo me decidí a hacerlo

por la parte de los arreglos porque es más común verlo así.

Es muy común trabajar de esta manera.

Ok vamos a ver yo necesito barrer todo este arreglo buscar este Heydi y cambiar ese valor.

Entonces vamos a hacerlo de una vez.

Primero voy a hacer un ciclo foro para ver cada uno de esos elementos constante tú o disputó todos ahora

se arrolladas.

Ahora necesito evaluar si el que estoy evaluando en este preciso instante es si hay vida ese todo es

igual a esta.

Entonces ese es el que tengo que cambiar entonces y si todo apuntó Heydi.

Es exactamente igual a la que recibo entonces aquí hay que hacer el cambio pero antes de hacer ese cambio

aquí va a pasar lo siguiente Si nosotros vemos nuestros componentes eventualmente yo voy a leer este

valor de acá yo voy a obtener este tubo apuntó Heydi y eso lo voy a leer como un ring aquí va a llegar

un Schering y si yo lo hago con un triple igual tiene que ser tanto el tipo como su valor van a ser

iguales y muy posiblemente en mi arreglo van a ser ustedes pueden observar van a ser números entonces

antes de hacer esa comparación déjenme hacer un consumo de Heidi y él tuvo un punto débil sólo para

confirmar esos valores pero estoy casi seguro que van a ser strengths uno va a ser un estreno y otro

va a ser un número bueno por eso voy a poner doble igual pero ya vamos a ver eso funcionando.

Entonces si el aire es igual a la que recibo por el argumento cambiamos el valor apuntó completado.

Va a ser igual a la negación del todo.

Autocompletado es decir si esto es otro la negación de otro es falso.

Y si esto fuera falso la negación es falso.

Eso es básicamente todo.

Como ya no suponiendo que cuando yo entré acá no va a haber otro todo con el mismo Heydi voy a hacer

un break para salirme de el ciclo porque eso es todo lo que necesito por marcar completado ya vamos

a ver esta parte de consolón cuando lleguemos al punto pero ahora necesitamos trabajar en base a identificar

cuál elemento es el que yo hago click comprar unicornio ok yo voy a ocupar diferenciar si es éste o

es éste o para poder hacerlo diferente es bueno marcar este juego completado y también ya tenemos nosotros

este Dib todo listo que si vemos el HTML es este elemento donde dentro de él están cada uno de los elementos

el que yo voy creando podemos utilizar ese mismo componente para agregarle un evento cuando alguien

haga clic en él.

Entonces vamos a ver cómo lo implementaría.

Dip Turu List punto a de tener voy a crear el Lissner click Koma recibiríamos elemento función de flecha

cero ya ves que por ahora lo único que quiero hacer es imprimir en consola click en un elemento y también

hagamos el laimpresión del evento los otros consolón son los que quiero ser para empezar graven los

cambios.

Regresemos acá y voy a hacer click en aprender JavaScript noté que tenemos el click y tenemos un mouse

y ven y esto es bastante.

El problema es que a mí no me interesa el mago pero sí me interesa este target aquí me dice target Leiber

porque se clic en ley pero si yo hago clic en la X en el target a lo que yo le hice clic va a ser un

botón con su clase de Strait pero me interesa el botón.

Entonces aquí en vez sí me interesa el punto target.

Voy a grabar los cambios.

Voy a regresar acá Recaro un navegador web puede hacer clic en el check y aquí tengo que hice clic con

imput.

Voy a hacer click en el Lebón y se el iPhone puede hacer clic en la X y es un botón.

Entonces si yo necesito saber exactamente qué elemento fue voy a poner aquí punto local local me voy

a grabar otra vez los cambios.

Voy a recargar navegador web esto lo hace solo aquí hago clic en el botón y clic en el input.

De esa manera puedo identificar qué parte del este.

Hice clic excelente.

Entonces voy a grabar una referencia a ese valor.

Será una constante llamada nombre elemento.

Va a ser igual va a ser igual a estoy acá.

Recuerden que esto va a ser un input va a ser un leu o un botón.

Esos son los únicos tres que hay porque lo único que está dentro de ese elemento ahora voy a ocupar

a hacer también la referencia al elegi completamente.

Por qué.

Porque cuando yo toqué esa X voy a tener que destruir el elemento HTML también y eso es algo que voy

a ocupar de referencia por eso todo le voy a intentar recuperar ese valor constante.

Voy a poner aquí tu elemento o elemento tu elemento va a ser igual a punto target.

Ahí estamos igual ahora punto parent.

Vamos a poder Parent Element punto y coma.

Creo que es uno más pero vamos a ver y primamos en todo elemento voy a grabar los cambios voy a regresar

al navegador web.

Voy a hacer click en cualquier lugar y lo que hice fue click en el DIV Class View Class y tenemos esta

información pero realmente hay un elemento antes de esto que este DIV es el que contiene el input Leuven

el botón pero necesito la referencia al Lehi entonces pacer otro punto para un elemento voy a grabar

los cambios voy a recargar el navegador web.

Bueno ya no lo hace por mí y aquí ahora sí tengo la referencia completa a Eloy que este es el elemento

que yo necesito porque si ya después llego y lo borro se borra aquí también del HTML.

Eso es lo que voy a ocupar.

Excelente pero no sé si ustedes notaron perdón que vuelva a regresar acá pero cuando yo hago click aquí

tengo el Heydi del elemento.

Por ejemplo si yo creo uno nuevo voy a crear comprar unicornio enter yo hago clic en comprar unicornio

tengo la idea de ese Lehi y si yo hago clic en comprar voy a aprender JavaScript tengo el Heydi de aprender

JavaScript obviamente en su caso van a ser Heydi diferentes pero ustedes pueden ver muy fácilmente estoy

diferenciando cuáles son y cuál es el otro.

Entonces extrañábamos ahora este Heydi para eso voy a regresar aquí en una constante llamada tudo Heydi

y esto va a ser igual a El tu elemento punto y hay una instrucción en JavaScript que es Get a Trivium.

De esta manera vamos a poner el nombre del atributo que ustedes les interesa mi atributo es dejeme mostrárselos

este data Heydi ustedes pueden obtener la clase pueden obtener todo lo que tenga esa clase pero lo que

me interesa es este data Heydi entonces aquí voy a poner data Heydi podemos revisar si eso es cierto.

Voy a imprimir todo Heydi los cambios que esto va a hacer los que tenemos que mandar a nuestra clase

de todo clase Feist Toko acá y ese es el Audi y eso es lo que estoy recuperando acá.

Voy a crear otro comprar unicornio nuevo unicornio yo sé que molesto con eso pero ahora se explica y

este es el Leydi del unicornio y aquí lo tenemos excelente.

Vamos bien vamos bien ya tenemos todas las variables listas ahora yo lo que quiero trabajar es marcar

el todo como completado o no parte del trabajo ya está hecho porque si hago click acá ya se marca automáticamente

porque ese es el comportamiento por defecto de un check box en HTML.

Pero yo no tengo marcada en mi arreglo yo no tengo marcado eso de que aprender JavaScript ya ha sido

terminado entonces tengo que hacer el procedimiento.

Voy a preguntar si el nombre del elemento punto includes incluís o sea si el nombre de elemento incluye

algo llamado imput quiere decir que hizo clic en el check.

Entonces ahora hiceron ya.

Pero voy a poner aquí abro y cerró llaves Enter the voy a ponerlo acá.

Entonces hagamos la lógica si la persona hizo clic en ese lugar voy a decir todo listo punto y lo que

me interesa es marcar completado el Dudú que tenga el punto y coma.

Eso es casi todo lo que tengo que hacer.

Voy a hacerlo mi impresión de consola con solo de él.

Todo listo para que lo observemos.

Voy a grabar los cambios cargar el navegador web voy a hacer click acá.

Pareciera que lo hizo pero no salta el tachado.

Ahora voy a los todos y aquí tenemos que completar otro.

Si yo vuelvo a hacer clic ahora debería decir que todo está completado falso.

Eso está bien pero no estamos viendo la clase que le pone el tachado acá vamos a ver cómo podemos añadir

eso.

Nosotros tenemos la referencia al elemento HTML que es el elemento para hacer referencia a todas las

clases se acuerdan que era el flash List y si yo quiero estar agregando o cambiando una clase que es

todo y la clase que quiero que esté bueno que si ya existe la quita y si no existe la pone esa va a

ser la clase cómplice.

Eso es básicamente todo vamos a ver si funciona loscambios que es un navegador web tocó el check aparece

ahí vuelvo a quitarlo y está funcionando como yo esperaba.

Bueno eso es básicamente todo lo que quería llegar pero antes antes de terminar la clase esto es lo

que yo quería mostrarles.

Estamos recibiendo un string.

Esto está en todos las clases estamos recibiendo un string pero lo que tenemos en la clase es un número.

Por eso los diferencias de color y por esa razón es que estoy haciendo la evaluación igual.

Igual ustedes si quieren podrían transformar este hoy día un número y así pueden evaluarlo de esta manera

pero eso sería un paseillo no que lo podemos dejar así tenemos este con su blog y los cambios y estamos

listos para continuar en el siguiente video en el cual vamos a trabajar con la X pero eso va a ser mucho

más fácil de lo que acabamos de hacer.



## 112 Eliminar un Todo 04:52

Es momento de trabajar con la parte de eliminación de un todo y para eliminar todo.

Hay muchas formas nosotros podríamos hacer una lógica parecida a esta y si el aire es el mismo que nosotros

lo borremos logramos desaprensión del arreglo pero podemos utilizar una función que ya viene un método

que ya viene dentro de los arreglos que es el filtro en el material adjunto yo les dejo a ustedes la

documentación del Filter por si acaso tienen dudas al respecto.

Si nosotros miramos este ejemplo que tenemos acá tenemos una colección donde está el spray limit élite

y otras cosas.

Tenemos una colección de palabras y si aplicamos el wards apuntó Filter o sea aplicamos el método Filter.

Este arreglo la condición que estamos dando acá es que pregunta si cada una de las palabras tiene un

largo mayor a seis letras.

Y si tiene más de seis letras eso es lo que va a regresar aquí y regresa una nueva copia del arreglo.

Exactamente lo que yo voy a ocupar.

Entonces vamos a ver cómo podemos implementar eso.

Aquí nosotros me voy a ocupar barrer todos los tubos con el filtro entonces disputo todos puntos Filter

parentesis y viene un Kovac ese Kovac va a recibir como argumento el tuyo o sea muy parecido a lo que

tengo aquí abajo va a ahorrar cada uno de ellos y voy a tener un tubo individual ese tubo voy a preguntar

si todo apuntó allí es diferente a la IDIC que recibo por el argumento.

Noten que soy poniendolo con un solo igual si no dominacion o igual eso significa que sea diferente

a este EITI.

Recuerden que si yo pusiera otro está comparandolo también por identidad.

Quiere decir que tiene que ser el mismo tipo de números con números Construïm y el mismo valor.

Pero ya vimos en el video pasado de que aquí vamos a recibir un string y nosotros tenemos almacenado

un número.

Por eso lo hago de esta manera.

Ok entonces toda esta instrucción va a regresar.

Un nuevo arreglo excluyendo el todo que coincida con el Heydi que tengo entonces este nuevo arreglo

lo voy a almacenar en el disco todos se mirarán un poco extraño pero toda esta instrucción va a regresar

un nuevo arreglo iba a ser almacenado en el Tut que ya tengo acá escribiendo cada uno de sus valores.

Entonces esto me va a eliminar o me va a ser la impresión de que estoy eliminando ese tubo o que vamos

a ver si eso es cierto voy a grabar los cambios y ahora regresemos a la parte de nuestro Eben Lissner

que teníamos de edulis porque ya tenemos todo inclusive sabemos cuando hacemos clic en el botón déjenme

hacer el consolón del nombre elemento sólo para refrescar la memoria grabé unos cambios esto sólo sucede

en el material junto recuerden si yo clic en el nombre tengo una referencia le llegó click en input

tengo una referencia al imput y si hago clic en esta X hago referencia al botón.

Entonces voy a poner la condición ahora y si el nombre elemento punto incluís botón si eso incluye el

botón entonces quiere decir que hay que borrar todo.

Eso es lo que quiero hacer el usuario.

Entonces qué sería lo que tendríamos que hacer.

Bueno lo primero hay que hacer el llamado al todo listo punto.

Hacemos el llamado a nuestro método de eliminar todo eliminar todo paréntesis y mandamos el Heydi que

ya lo tenemos aquí y eso lo borra el arreglo pero la referencia a HTML todavía va a existir.

Si quieres voy a grabar los cambios.

Voy a regresar al navegador web esto se recarga toco la X y note que ya no tenemos ningún Turu en el

arreglo pero sigue existiendo en el html entonces tenemos que eliminarlo del HTML y cómo hacemos eso.

Bueno hoy hacer referencia a este día todo listo tu lista y necesito remover Jael el que coincida con

este elemento OK de acá.

Eso es básicamente todo para eliminar un elemento HTML.

Hay muchas otras formas pero esta es una porque ya tenemos el elemento sabemos que está dentro de él

y vamos a eliminarlo.

Vamos a ver si esto cierto tocó la X y se elimina.

Vamos a crear otro como por ejemplo salvar salvar al mundo entero crearme otro o de nuevo con el unicornio

o comprar Unicornio.

Aprender JavaScript.

Comer y jugar.

Yo voy a eliminar aprender JavaScript perfectos eliminar eliminar jugar perfecto.

Salvar el mundo comprar el unicornio y jugar excelente.

Ya tengo una manera de eliminarlos y eso es básicamente todo.

Voy a quitar este consumo.

Ya no lo voy a ocupar y estoy aquí abajo también no voy a borrar.

Bueno eso era todo la eliminación Gravesen los cambios y los veo en el próximo video.



## 113 Eliminar Todos completados 08:49

Porque en la clase anterior borramos todos independientes ahora quiero borrarlos todos los que estén

completados.

Vamos a desarrollar la lógica.

Abramos el archivo de tu duh list.

Creo que teníamos creada creado el método pero no lo hemos implementado.

Vamos a hacerlo.

La verdad es que hacer este método es bastante sencillo vamos a ver si tengo un ejemplo acá para explicarles

aquí tenemos la eliminación de un todo y recibimos el Heydi y la condición que establecemos es que vamos

a regresar un nuevo reino excluyendo o filtrando el tubo que coincida con ese allí.

Básicamente esta instrucción nos puede servir para implementar eliminar todos.

No recibimos ningún argumento.

Pero cuál sería la condición que yo quisiera implementar acá.

Entonces prácticamente lo que tengo que hacer es borrar esto y preguntar cierto punto completado.

Si yo lo dejo así retornaría únicamente todos los que están completados.

Pero no necesito eso no necesito lo inverso entonces para eso voy a poner el signo de admiración.

Necesito todos los que no estén completados.

Va a sonar raro porque quiero eliminarlos completados pero la idea de este filtro es que regrese únicamente

los elementos que a mí me interesan y para este caso me interesan todos los que no están completados.

Básicamente esta es toda la lógica en mi clase.

Yo sé que posiblemente más de uno de ustedes dice Bueno pero para qué estoy manejando este archivo de

clases y todo lo tengo acá.

O sea si todo lo tengo en objetos de HTML y podría trabajar en base a eso y en teoría es cierto pero

va a haber un momento en el cual yo voy a querer almacenar esto en algún lugar persistente y ahí si

ya no me va a servir ni HTML porque lo voy a perder.

Entonces implementemos la acción y el evento para que nosotros podamos al presionar este botón o que

no estoy seguro si es un botón pero al presionar este enlace o lo que sea que tengamos acá en el html

borre todos los completados.

Entonces abramos nuevamente el archivo js componentes voy a subir y voy a ocupar una referencia a ese

elemento HTML que hace bueno si es un botón.

Si hay un botón que tiene esta clase de click cumpliré.

Voy a tomarme esta clase regresar a mis componentes.

Voy a crearme un nuevo elemento que puede ser Kairi selector.

Voy a ponerle nombre.

Les parece BSN borrar pero el nombre es bueno.

Su total discreción.

Copiar esto vamos a bajar un poco el final.

Implementemos Listen even Listen.

Necesito estar pendiente del click y cuando hago click simplemente quiero disparar esta acción.

Perfectamente puedo recibir el evento pero no me va a servir de nada.

Yo sé que cuando hago clic en ese botón no importa que coordenada haga click lo que me importa es que

cuando se toque ese botón es bueno dispara mi acción de borrar.

Lo primero sería tu duh list.

Punto.

Borrar Borrar completado lo pusimos vamos a eliminar completado ser una cosa ok.

Eliminar completados paréntesis punto y coma.

Y eso lo elimina de mi arreglo que tengo en la clase.

Pero todavía bueno si yo grabo los cambios pero en este preciso instante todos mis todos todavía seguiría

existiendo en el html.

Por ejemplo a tu 1 2 3 4 pero si yo toco ese botón toco el botón se eliminan pero todavía siguen estando

en el html.

Entonces necesito de alguna manera poder barrer todos los elementos que tenga este y este contenedor

o esté Viv y empezar a eliminarlos uno por uno.

La única diferencia o tal vez lo único engañoso es que voy a tener que empezar a borrar de abajo hacia

arriba.

Por qué.

Porque si yo borro esto y veamos que estamos en un ciclo.

Y ahora voy con el siguiente elemento pero esto Yo lo eliminé erróneamente podría tomar el cuarto a

saltarse el tercero por la posición índice porque va a ir cambiando.

Entonces por eso voy a eliminar los de abajo hacia arriba porque si elimino éste la posición y nese

de todos los demás sigue siendo la misma.

Entonces por eso voy a eliminar de abajo hacia arriba.

Ese es el único truco extraño que vamos a tener que implementar acá.

Entonces para eso voy a ocupar hacer la referencia a todos los hijos que tenga este día todo listo.

Ok entonces vamos a comenzar acá lo primero voy a hacer un fork escribamos Let y igual a Di todo listo

que lo tengo guardado.

Punto.

Children Children acá punto menos uno.

Ok porque necesito empezar en la última posición y acuérdense que todos los arreglos en JavaScript empiezan

en cero y por eso estoy restando uno porque aquí puede ser que yo tenga.

Por ejemplo si sólo tuviera uno en este caso sólo tengo uno pero la posición índice de éste es cero.

Por eso le estoy restando uno.

Acá yo necesito ejecutar este foro siempre y cuando sea mayor a cero o mayor o igual a cero porque el

cero sería el primer elemento y aquí voy a ser el menos menos para hacer el procedimiento inverso.

Porque recuerdan cuando nosotros empecemos y puede tener valor de 10 y se va a ir de decremento hasta

llegar a menos uno que ya sería un número que ya necesito salirme de ahí.

También ese es un buen ejercicio para que ustedes vean cómo se puede hacer un favor inverso.

Los invito a que Uds. prueben las otras maneras para hacerlo de cualquier otra forma que ustedes quieran.

Con el objetivo de que practiquen OK pero eso es una manera que puede ser útil para resolver este problema.

Ok entonces lo que yo necesito ahora es preguntar si el elemento en el cual el elemento actual que estoy

barriendo está completado o no y si está completado borrarlo voy a en una constante llamada elemento

que va a ser igual a tu lista.

Punto children.

Y necesito el hijo en esa posición y voy a ser un consumidor del elemento para que lo podamos ver en

consola.

Voy a agravarlos cambio puedo regresar navegador web.

Voy a tocar el botón de completados y aquí tenemos que estoy recuperando todo el Elegy todo el elemento

de ley que tengo hoy.

Si tuviéramos otro tuvo uno dos o tres que voy a limpiar esto voy a tocar el botón de eliminar completados.

Tengo cada uno de ellos como ustedes pueden observar pero lo interesante es que se imprimen en orden

inverso.

Este sería el último.

Este será el siguiente y así sucesivamente.

Entonces tengo que revisar si tenemos completado un elemento hay que eliminar esto otra forma de hacerlo

sería trabajar con el mismo arreglo.

Pero cuando nosotros apliquemos filtros pudiera ser que el índice no corresponda al índice que tenemos

en el arreglo y por eso estoy trabajando únicamente con el HTML.

Ignorando mi clase si se preguntan por qué hice eso qué entonces ahora tengo que preguntar si el elemento

punto y aquí viene una pregunta interesante cómo puedo saber si este elemento está completado o no hay

muchas formas una de ellas sería revisar si el input voy a tocar aquí el completado o voy a volver a

presionar este botón y una de ellas.

Bueno aunque ustedes ya lo vieron acá una de ellas sería ver el input a ver si está con su clase check.

Eso se podría evaluar pero como ustedes pueden observar lo más sencillo es tomar este cumpliré porque

ya lo tenemos puesto.

Ok voy a ver si tengo estos dos todos marcados con completados tocó el botón tengo cumplirãn en éste

y también tengo conspiren en éste.

Entonces lo más fácil en este caso es preguntar si tiene esta clase y si la tiene voy a borrarlo.

Entonces punto.

List punto contains.

De esta manera puedo comprobar si ese elemento tiene una clase y la clase que quiero evaluar es cómplice.

Esa clase de ahí sí lo tiene.

Entonces tengo que eliminar ese elemento de el DIV list.

Entonces titulitis punto rimo Jael y vamos a mandar el elemento punto y coma.

Eso es básicamente todo.

Traemos los cambios vamos a probar esto.

Queremos otra vez.

1.

2 3 o póngale el nombre más creativo que ustedes quieran pero ya me está dando como.

Ya no me estoy quedando sin ideas.

Entonces ya no sé qué más poner me voy a eliminar el 1 y el 3.

Vamos a ver si eso es cierto toco el botón y se eliminó el 1 y el 3.

Excelente puedo tocar aquí quiero eliminar todos menos el 4 perfecto y ahora puedo marcarlo como ha

completado y borrar eso si yo toco el botón no debería dar ningún error porque no hay elementos en el

arreglo sea el número de elementos el arreglo sería cero pero como le estoy restando uno sería menos

1 y menos 1 no es mayor o igual a cero y por eso no me disparan ningún error.

También podríamos ser más eficientes y ejecutar esta instrucción porque siempre lo estamos ejecutando

cuando tocamos el botón pero ahí queda a discreción de ustedes qué tanto bueno qué tan quisquillosos

quieren hacer con su código.

A mí me parece que lo podemos dejar así y los veo en el siguiente vídeo.



## 114 LocalStorage y SessionStorage 06:42

Hemos llegado a un punto donde ya me estorba que la información no sea persistente.

Es decir empiezo a escribir todo.

1 2 3 Enter pero yo recargo navegador web o imagínense que yo me muevo otra pantalla y después regreso

y perdí la información.

Entonces esto no me gusta cómo hago para mantener la información a pesar de que yo reinicie o cierre

el navegador web.

Bueno para eso ya tenemos algo que se llama en locales Storage y el cesion Storage que les voy a pedir

que índex punto JBS.

Voy a implementar algo rápidamente sólo para fines ilustrativos y después lo implementamos en algún

lugar en nuestro programa para trabajar con lo que el estores y el secesiones storage.

No hace falta instalar ni importar nada porque ya es una característica propia del navegador web pero

vale la pena decir que esto solo funciona cuando ustedes están trabajando o su aplicación va destinada

a la web.

Si ustedes van a trabajar y no deciden el Bakken el backing no tiene acceso a lo que les Storch ahí

tendríamos que usar el sistema u otras cosas para almacenar la información.

Una base de datos por ejemplo pero en este caso nosotros podemos trabajar con el local Storch y lo vamos

a poder ver en la pestaña de Application.

Puede ser que ustedes no vean la pestaña de Application.

Puede ser que estén estas flechitas aquí la busca pero en mi caso aquí yo la tengo y Tokman application.

Por cierto ustedes pueden mover estas pestañas y colocarlos donde mejor les plazca.

Aquí ustedes van a buscar en la parte de storage y vamos a hacer clic en locales storage.

Posiblemente tengan algo que es una información del web pack pero no se preocupen eso básicamente es

parte de la sesión que nosotros estamos manejando.

Y aquí también tenemos el sello Nestor y no tenemos absolutamente nada.

No se preocupen si ustedes al abrirlo no hay nada si o si no tienen esta fecha no importa.

Eso quiere decir que no hay nada almacenado ahí.

Pero estos dos horas y seis sesiones de esto parece trabalenguas pero son exactamente la misma cuestión.

La única diferencia entre el local Storage y sesiones Storage es que el cesion Storage se va a borrar

todo cuando ustedes cierran por completo el navegador web por ejemplo yo presiono contra el cual presiona

al F4 terminó la tarea y fulcro.

Entonces ahí va a purgar todo lo que tenga almacenado en el sello Storage y cuando vuelvo a abrir mi

aplicación aquí no voy a tener nada.

A diferencia de locales torrents que sí aguanta un reinicio inclusive de su computadora.

Aquí ustedes van a poder almacenar información que necesiten su aplicación.

Pero recuerden esta información es visible por el usuario final por lo cual no es conveniente que ustedes

almacenen contraseñas o cosas sensibles para el usuario o que vamos a ver qué podemos hacer acá para

trabajar con el local estores.

Simplemente escribimos local local Storage Tapp punto y aquí tenemos varios métodos y propiedades como

por ejemplo cuántos elementos hay remover un ítem colocar un ítem y creo que hay otro ítem perdón aquí

está el ítem no está el clic que está abierto el local Storage para confirmar si existe alguna llave

y en este caso yo quiero el set either parentesis orillero jackets noten que aquí me está ayudando hizo

el estudio y me dice que la llave tiene que ser de tipo string y el valor tiene que ser de tipo String.

A fuerza ustedes no pueden grabar números no pueden grabar objetos no pueden grabar nada que no sea

diferente a un string y agresivo pero qué dolor de cabeza porque todos son objetos ya vamos a ver cómo

hacer esto por los momentos que uno saca en el set Heute.

Voy a poner algo como Mi llave o Miky por favor no pongan espacios no pongan nada raro no pongan caracteres

especiales traten de limitarse a lo que es el nombre de cualquier propiedad de un objeto en JavaScript.

Entonces le voy a poner mi llave coma seguido del valor que ustedes quieren almacenar como por ejemplo

a veces uno dos tres King.com grabar los cambios voy a recargar Killa recarga el navegador web y deberíamos

de ver automáticamente acá mi llave.

A veces uno dos tres.

Si ustedes quieren reemplazar ese valor ustedes simplemente lo vuelven a escribir.

Voy a grabar los cambios y a ver que automáticamente se aplica.

Si ustedes no se les aplicará automáticamente entonces con este botón para hacer refresh o si no se

explica acá.

Bueno por aquí hay un refresh y no estoy mal.

O bueno hacemos el refresco anual y abrimos acá nuevamente.

Hay varias maneras de refrescar esto.

Perfecto.

Si ustedes quieren eliminar un valor entonces pueden hacerlo de varias maneras si ustedes quieren pueden

hacerlo si pero la llave seguiría existiendo solo que ahora está con nuestro vacío.

Podríamos decir voy a colocar acá una instrucción de un set their mouth parentesis Tocoma el SEC taimados

va a ejecutar esta instrucción.

Voy a ponerlo en un segundo y un segundo y medio de 1500 milésimas de segundo.

Entonces el CETA es un procedimiento que yo sé que todavía no hemos visto muy a detalle pero esto va

a ser también para aprovecharlo.

Yo puedo disparar el Kovac que estoy especificando aquí en mil quinientas milésimas de segundo es decir

un segundo y medio y aquí lo voy a borrar locales Storage punto y aquí remove them y entre llaves el

nombre de la llave que yo necesite.

Entre estos apóstrofe es el nombre de la llave que tengo hoy.

Entonces en un segundo y medio se va a borrar este valor queremos y ahí está.

Como ustedes pueden observar voy a comentar esta línea porque no me interesa el cesion Storage es exactamente

igual solo que aquí sería cesion Storch.

Entonces si ustedes graban los cambios regresa al navegador web.

Aquí lo deberíamos tener en el sello en Storage ok.

Esa es básicamente la diferencia de los dos pero yo le recomendaría que ustedes decidan qué es lo que

necesitan en su aplicación.

Usualmente lo que les soroche es más que suficiente para grabar los cambios.

Ahora sí tenemos la pregunta del millón Cómo puedo hacer para mantener mis dudas porque recuerden que

él tuvo que aprender JavaScript lo estoy creando en este momento y ya es momento de quitarlo de acá.

Voy a quitar estoy acá y voy a grabar los cambios.

Voy a recargar el navegador web y ahora si ya no tengo nada si empiezo a escribir todo.

1.

2.

Perfecto pero recargó navegador web que no tengo nada.

Vamos a grabar esto en el local storage.

Les voy a pedir que vayamos a nuestra clase al edulis Class implementemos dos métodos vamos a ocupar

un método para guardar en el local Storage abrieron ya ves y voy a ocupar otro para cargar de locales

poder cargar local storage o cargar todos almacenados previamente.

Ok pero voy a dejarlo hasta este punto no quiero que el video se haga muy pesado.

Esto fue la introducción al local Storage y al sello Storage nos vemos el siguiente video donde vamos

a implementar estos métodos.




## 115 Guardando y recuperando Todos 15:03

En la clase pasada nosotros nos quedamos en la implementación de estos dos métodos de guardar y cargar

todos de locales soroche.

Si nosotros miramos acá en nuestro local estores en la pestaña de Application en Google Developer tuvo

semanas developer tool según Crom ustedes van a notar que dice el local 2.80 80.

Eso es algo que se me olvidó explicar en el video anterior.

Pero es que ustedes van a poder tener un local Storage por dominio.

Es decir si ustedes se van a Facebook.com va a haber un local Storage destinado sólo para Facebook a

Twitter si se van a tener el punto com va a tener un local esto es sesiones Ouch por cada dominio y

ustedes sólo van a poder acceder a locales torax de dominio en el cual ustedes están corriendo la aplicación.

En este caso solo sería el Local Storage pero cuando ya lo perdone el local Jost pero ustedes no desplieguen

algún sitio web algún dominio entonces el Local Storage va a hacer referencia a ese dominio.

Una vez dicho eso hagamos el procedimiento para guardar en el local Storch.

Nosotros tenemos nuestro listado de todos que esto es básicamente lo que yo quiero almacenar.

Pero cómo lo haríamos.

Bueno empezamos con la palabra Local Storage.

Esto es una palabra entre comillas reservada pero ustedes podrían poner una variable que se llame local

Storch pero tienen que tener cuidado porque le caerían encima a estas funcionalidades por lo cual no

es bueno que ustedes le pongan ese nombre.

Entonces punto ser Aitken parentesis y voy a crearme una llave llamada Turu común y el valor que yo

quiero almacenar acá debería de ser disputo todos.

Ok puntocom si yo grabo los cambios pero necesito llamar este y guardar todo en donde lo voy a llamar.

Vamos a ver lo vamos a poner en varios lugares.

Cuando eliminamos un tubo nosotros deberíamos de llamar el disputo guardar local Storch.

Por qué.

Porque cuando hacemos una modificación a este arreglo deberíamos de grabarlo acá.

Ok vamos a ver entonces cuando grabamos deberíamos ejecutar este local.

Este procedimiento este método de guardar el storage pero también cuando los marcamos como completados

aquí también hicimos una modificación a un tubo y deberíamos de guardarlo todos los tubos así como están.

Si bajamos un poco cuando los eliminamos aquí también deberíamos de llamar el guardar Local Storage

y básicamente eso serían los lugares a grabar los cambios pero haciendo pequeño paréntesis en la clase

anterior.

Se acuerdan que yo les dije que para almacenar en el local Storch todo tiene que ser strengths.

Y aquí estoy intentando grabar un arreglo.

Vamos a ver qué pasa si yo lo intento hacer de esa manera.

Quedémonos aquí en la consola para ver si aparece algún error obviamente YA RECARGAMOS el navegador

web.

Voy a crear un nuevo producto.

1 enter 2 enter y bueno no lanzó ningún error y si nosotros realizamos nuestra clase debería de estarse

llamando aquí también.

Bueno aquí también nos hizo falta cuando creamos un nuevo todo o que podíamos hacer esto nuevamente

o que agravarlos cambios recargó ustedes van a notar que se borró todo.

1 Enter.

No dio ningún error.

2 Enter.

Y no está pasando nada no está sucediendo ningún error que interrumpa mi aplicación y si nos vamos a

la parte de Application en locales Storage en todo.

Ustedes van a ver que dice Object Object y aquí también Object Object y qué es esto qué es esto de Object

object.

Eso es muy común que ustedes lo vean.

Por ejemplo voy a crearme una constante llamada a que va a ser igual a un objeto punto y coma.

Si yo digo apunto tu string tu string Enter.

Note que dice Object Object que es casualmente lo mismo que era guaca el Object Object es la representación

de un objeto en su forma string y cuando ustedes lo graban en el estores así de Object Object no van

a poder recuperar estos su estructura original porque son literalmente.

Es un estudio que dice Object objects literalmente dice eso no hay manera de abrir ese objeto porque

así quedó es la representación exterior del objeto y es muy común que ustedes lo vean así en otros lugares.

Entonces qué podemos hacer en este caso.

Bueno existe otra forma de transformar todos a la hora de grabarlos y transformarlos a un Jayson.

A qué me refiero con eso me refiero a poder transformarlo algo muy parecido a como tenemos este paquete

y no al paquete punto y eso es muy parecido transformarlo así el objeto y a su vez pasar ese objeto

así como lo tenemos acá y pasarlo a un tren de manera que grabe todo el objeto abierto por decirlo así

y ese objeto abierto lo grabé en el aire.

Yo sé que eso sonará un poquito enredado pero vamos a probarlo entonces para eso existe otro objeto

en JavaScript que es todo capitalizado que es Jayson punto y aquí tenemos varios métodos importantes

que es el pase y el swinging Giphy en la próxima sección.

Si no estoy mal vamos a hablar más sobre los Jacksons pero pocas palabras si yo pongo Jayson punto string

Yuffie le estoy diciendo que me convierta este arreglo de todos este caso lo voy a mandar aquí adentro

estoy diciendo que me convierta mi arreglo de todos a un Jayson perfecto lo que esos sonará extraño

pero voy a grabar los cambios.

Voy a regresar al navegador web y sólo crece un Turu voy a poner titu uno presiona Enter.

Vamos a ir a la pestaña de Application vamos un poco más grande para que lo podamos ver y ustedes van

a notar que lo que grabó acá es ese objeto abierto así le estaba diciendo yo pero es ya la representación

del objeto.

Ustedes lo pueden ver aquí abajo también.

Ok no te quedó grabado como tarea Heydi aquí abajo ya Google Krome les facilita a ustedes para que lo

puedan ver como objeto pero realmente lo que está grabando es esta información de aquí arriba note que

vienen las llaves cuadradas para indicar que es un arreglo.

Luego vino la llave que es para un objeto entre comillas la tarea.

Nosotros no pusimos esas comillas y todo el audio entre comillas y viene toda la información del objeto

exactamente lo que yo necesitaba grabar.

Si ahora creo otro todo tú 2 presionó Enter.

Ahora tengo dos objetos que están dentro de este todo perfecto.

Entonces de esa manera Chalo estoy grabando.

Si yo recargo un navegador web noten que perdemos los dos pero en el local Storage se mantuvieron esos

dos tubos que yo había creado previamente.

Si ustedes no lo ven entonces revisen o asegúrese de que hayan ejecutado en en todo este guardar lo

que les Storage perfecto.

Ahora viene el proceso inverso necesito poder leer este objeto que está en mi local Storage y poder

establecer celos a estos tus ok entonces el siguiente paso va a ser tomar estos todos y construirlos

acá vamos a ver cómo hacemos eso en la parte de cargar el local storage.

Nosotros siempre antes de trabajar con el local esto no es propiamente una propiedad del mismo sea una

llave grabada y tenemos que verificar si ese objeto existe como por ejemplo y si en el local Storage

Puntoticket Haytham si existe el Turu entonces voy a ejecutar este código si no es si no voy a hacer

esto otro quiere decir que en este punto todavía no teníamos nada grabado en el Local Storage pero no

necesariamente ese es el único caso.

Puede ser que la persona haya vaciado el caché haya hecho purgado todo acá en Clear Storage y hayas

tocado este botón eso lo purgó todo entonces hay varias razones por las cuales siempre hay que manejar

el local Storage no sólo porque ustedes lo hayan grabado y están seguros que lo grabaron no necesariamente

puede ser que exista.

Entonces hay que manejar un Eros que si no existe entonces voy a decir que dispón tutús va a ser igual

a un arreglo vacío y de esa manera lo inicializar ok no estoy ni realizando como lo tengo aquí en el

constructor que después del procedimiento podríamos quitar ese es instruccion porque va a estar de más.

Ok.

Y ahora si existe entonces voy a decir que disputo todos todos.

Va a ser igual y ahora me toca recuperar esos tubos pero es esta misma instrucción pego punto y coma.

Voy a hacer ahora que una impresión de él disputo todos para que miremos qué es lo que está en el local

Storch o que voy a poder cargar local los puntos voy a ponerlo así para que lo observemos grabar los

cambios.

Voy a regresar al navegador web me quedo aquí en la consola Ox pero me falta llamar G cargar locales

Storch y esto lo voy a cargar cuando estoy creando mi constructor o una nueva instancia de mi clase

todo listo.

Esa línea la puedo comentar y lo voy a pegar acá despuntó pero aquí falta un disputo cargar locales

Storch en el constructor y esta línea ya no va a ser necesaria porque si no existe aquí mismo lo estoy

inicializar y si existe entonces inicial hizo ese objeto con el valor que tenga Local Storage.

Si yo grabo los cambios regreso al navegador web.

Vamos a ver qué es lo que sucedió.

Tenemos que cargar locales Storage y viene un streaming.

Esto no es un objeto como ustedes pueden ver yo no los puedo abrir y está como en ese color gris que

ustedes deberían de asociar de que eso es un string siguió intentó agregaran algo o UT3 presiona Enter.

Tengo un error y me dice que el tipo disputo todo punto pues no es una función.

Y por qué creen que pasa eso.

Porque si lo dejo así tú dus en este preciso punto.

Es un string y lo puedes confirmar haciendo un ataque o Taipe o dispositivos Ok voy a grabar los cambios

voy a recargar navegador web y aquí está tu es de tipo string y no es un arreglo por eso es que ya no

puedo insertar nada.

Hoy vamos a ver aquí en Application y ven que no se creó ese otro objeto.

Entonces qué es lo que tengo que hacer.

Bueno yo tengo que transformar este punto que hoy tengo que recuperarlo a como era su objeto original

en este caso antes de pasarlo por el Jayson Punch-Out.

Y como hay un Jayson punto string Giphy que lo convierte a un Jayson string debería de haber un proceso

inverso que tome un Jayson string y lo transforme a sujeto original y efectivamente lo existe entonces

Jayson punto Pals y entre paréntesis vamos a mandar el objeto que tiene que ser un Jayson pero nosotros

sabemos que es porque si lográbamos trabamos todos los cambios acá voy a regresar al navegador web y

ahora así cargar local y aquí tenemos un objeto que en este caso es un arreglo que tiene objetos dentro

y aquí me dice que de tipo ok perfecto.

Ahora si yo pongo nutres presiono Enter.

No dio ningún error y en el local Storage vamos a ver acá en la aplicación y aquí tenemos el tercer

elemento excelente.

El único inconveniente que tenemos es que a pesar de que ya los estamos manteniendo yo recarga un navegador

web no los estamos viendo físicamente acá eso ya lo vamos a arreglar y todavía tenemos un pequeño problema

que quiero que ustedes observen.

Vamos a ver si lo podemos poner acá.

Y es que el arreglo internamente ahora solo son objetos no son instancias de mi clase de tu pero eso

lo resolveremos más adelante.

Pero otra cosa que quiero hacer antes de terminar este video es que todo este código es un poquito largo

y la verdad lo único que me interesa es una línea de código aquí entonces podríamos utilizar el operador

ternario para asignar estos disputo todos y eso los voy a dejar ustedes estarían en este momento.

Necesito que usen el operador ternario pues si no se acuerdan aquí les dejo más o menos como es la sintaxis

sería disputo todos pacer igual ya que ustedes tienen que crear el operador ternario que me permita

realizar todo este mismo proceso.

Obviamente si los consoleros pero de manera de que me permita asignar mi disputo todos ya sea un arreglo

vacío si no hay nada o bien éste ya es un punto paz si ya tenemos algo.

Entonces póngale paso al video intenten hacer eso ustedes mismos en este momento así que manos a la

obra

lograron hacer.

Tuvieron algún inconveniente.

Espero que no. Entonces tendríamos que hacer lo siguiente primero confirmar si existe en el local storage.

Esto es mi condición entonces la voy a pegar acá Ok voy a decir sin el OK la historia existe eso sí

existe.

Voy a presentar un enter porque también esta es otra manera de hacer lo que se mire bonito.

Si esto existe entonces voy a ejecutar esta línea sin el punto y coma un punto pasa lo que hay en todo

caso contrario voy a regresar a un arreglo vacío y eso es básicamente lo mismo y ya podríamos borrar

todo esto si así lo que entonces queda mucho más limpio y fácil de leer.

Me voy a grabar los cambios deberíamos de tener exactamente el mismo procedimiento pero ahora nos falta

tomar nuestro arreglo de todos que tenemos en mano ya lo tenemos creado y ponerlos acá para eso nos

vamos a ir al índex.

De hecho todo esto ya casi quieren ustedes lo deja yo lo voy a borrar lo voy a borrar todo esto y una

vez ya hacemos este todo listo se opusieron con solo disputo del todo listo punto todos ustedes van

a observar que aquí los vamos a tener aquí tenemos dos tubos.

Ok pero me falta reconstruirlos en el html y para eso voy a tener que llamar.

Vamos a ver si lo tenemos aquí a la mano vamos a ocupar dónde está Construct bueno crear todo HTML deberíamos

llamar esta instrucción por cada uno de los métodos que tenemos hoy.

Entonces podría decir un todo listo punto Fortich pero 2.2.1 y parentesis aquí tendríamos un todo y

lo que vamos a hacer es mandar a llamar ese procedimiento lortu ok.

Punto y Coma voy a grabar los cambios.

Vamos a ver si esto funciona.

Recarguen navegador web.

Aquí tenemos cada uno de sus tubos y yo puedo intentar cambiarlos.

Voy a recargar el navegador web y van a ver que se mantiene.

Por qué.

Porque eso está grabado en el local storage.

Cada cambio que yo hago acá almacena esa información en locales Storage inclusive si yo borro uno y

recargo.

Ahí se van a quedar lo último que quiero hacer solo por un pequeño tip es que cuando ustedes tienen

una instrucción como ésta donde el argumento que quieren enviar es el único argumento que mandan a otra

u otra función o método que ustedes tienen acá entonces perfectamente pueden obviar poner s tu función

de flecha y quitar estos paréntesis y quitar el argumento.

En pocas palabras si yo grabo los cambios esto debería de ser exactamente lo mismo como ustedes pueden

observar.

Poner tu 2 tu 4 y recargó navegador van a ver que funciona exactamente igual pero sólo quiero que tengan

presente de que esto se puede hacer en pocas palabras con ustedes miren esta sintaxis quiere decir que

el primer argumento del corvas que estamos teniendo en el frizz o en cualquier método está llamando

el crear este HTML o la función que ustedes especifiquen aquí adentro y el argumento que le está mandando

acá va a ser pues y el argumento que les está mal que va a estar mandando aquí adentro es el primer

argumento que regresa el Fortich.

Eso sólo funciona bien si es sólo un argumento si ustedes ya tuvieran el forista regresarã que hoy el

ve entonces ahí si ya no funciona tendríamos que definirlo acá.

Ok pero en este caso lo voy a dejar de esta manera la forma corta pero ustedes pueden dejarlo como quieran.

Puede ser que les sea más fácil de ver la función de flecha o verlo de esta forma lo dejamos así y continuamos

con el siguiente video.




## 116 Reconstruyendo instancias de Todos 10:13

Lo que les voy a enseñar en esta clase no es necesario para fines de este ejercicio pero pudiera ser

que ustedes tengan en sus proyectos.

Puede ser que ustedes lo lleguen a necesitar.

A qué me estoy refiriendo.

A hacerlo con su blog de los tubos acá de punto dumb no sólo es el todo listo tu punto todos porque

voy a grabar los cambios lo único que hice fue una impresión después de que ya se reconstruya y haga

todo eso ustedes van a observar que aquí tengo mis dudas que es este nombre que puse acá fin y tenemos

un arreglo de objetos ok esto no es un arreglo de instancias de todo es un arreglo de objetos y cómo

puedo estar seguro cómo sé qué es eso bueno vamos a hacer lo siguiente acá voy a crear un método constante

YouTube hacer Guarani todo un paréntesis voy a poner a aprender JavaScript ok Punto y Coma voy a insertarlo

estuvo listo apuntó.

Insertar o agregar como le pusimos nuevo tu ni otro voy a grabar los cambios note que lo único que hice

fue crear una instancia de un nuevo todo recargo y aquí ustedes van a notar la diferencia más fácilmente

tengo los cuatro todos anteriores que fueron reconstruidos mediante locales storage.

Luego hice una inserción y esa inserción si dice que es de tipo Turu los demás no lo son y si yo recargo

el navegador web ahora tengo aquí el último todo que yo agregué fue aprender JavaScript.

También está apareciendo porque obviamente lo tengo en duro en el código pero este ya dejó de ser un

todo y ahora se convirtió en un objeto normal de locales Storch porque viene de lo que el Storch.

Esto no sería gran inconveniente voy a borrar comentar esto voy a grabar los cambios voy a descargarlo

y aquí los tenemos.

Eso no sería gran inconveniente déjeme borrar uno para este ejercicio porque realmente yo en la clase

de mostrárselos en clases realmente no estoy haciendo nada del otro mundo pero si aquí tuviéramos algún

método como por ejemplo pongamos algo como imprimir imprimir Classe llaves y lo único que voy a hacer

acá es un consulado entre Baketik que diga la tarea disputo tarea espacio y coloquemos el aire y el

Audi dispón taichí.

Qué tiene este método esta clase.

El tuplas tiene este método entonces acá a pesar de que en teoría todo Liz tiene todo su arreglo de

todos en teoría con todo listo punto todos en la posición cualquiera la expresión cero y quiero llamar

el método que yo acabo de crear que se llama imprimir clase.

En teoría esto debería ser válido porque estoy haciendo referencia a el tubo que se encuentra dentro

del Edulis y que imprima eso.

Esto lo voy a quitar por ahora si yo grabo los cambios y Recaro un navegador web tengo un error que

me dice que todos le disputo todos.

Imprimir clause No es una función.

Pero noten que eso debería de ser perfectamente válido porque si yo hago nuevamente esto y ahora digo

el futuro no está que no todo punto imprimir clase punto y coma de algunos cambios recargo si funciona.

Aprender JavaScript y su respectivo Heydi y estos son inconvenientes que tendríamos si leemos de locales

Storage y queremos trabajar con la instancia del objeto porque todos sus métodos se pierden las propiedades

no pero los métodos si se van a perder porque los métodos no son almacenados en el local Storch mediante

el Jayson punto estrellé.

Entonces qué podemos hacer en este caso.

Una manera de hacerlo o de resolver este inconveniente es que nosotros creemos en él en la clase tú

no edulis en la clase tú creemos alguna instrucción que me permita recuperar o crear una nueva instancia

en base a valores que vienen de locales Stores por ejemplo o que vienen de un objeto que pareciera un

todo pero realmente no es un todo ok vamos a hacer lo siguiente Voy a crearme un método estático Static

que se va a llamar from Jayson parentesis y yo podría recibir un todo o algo que parezca un tubo podemos

ponerle VJ un objeto y aquí voy a tomar ese objeto que note que el objeto debería ser algo muy parecido

vamos a recargar el navegador web pacá solo para fines ilustrativos los cambios un objeto que sería

exactamente esto es algo que parece un todo pero realmente no es un todo tiene la tarea Heydi y tiene

todo esto pero no es una instancia de mi todo entonces eso es lo que yo voy a recibir a cambio recibiría

un objeto y aquí digamos responder aquí constante temp todo como un todo temporal y esto va a ser igual

o nueva una nueva instancia del todo.

Recuerden que para llamarse constructor necesito mandar la tarea y yo voy a suponer que este objeto

tendría esa propiedad tarea también ok entonces aquí podría llamar Ojota punto tarea y eso crea una

nueva instancia y luego tendría que establecer las propiedades aquí podríamos usar la desestructuración

de argumentos para aprovechar esto aquí yo voy a recibir un objeto pero me interesa extraer el Heydi

la tarea completado y también lo que es la fecha de creación creado si le puse ok y es exactamente lo

mismo.

Entonces aquí ya no tengo que poner Ojota simplemente manda la tarea.

Perfecto.

Esto ya crea una nueva instancia pero me falta el Heydi completado y tarea y puedo hacer referencia

a esas propiedades directamente aquí abajo.

Yo voy a decir que el tema Tu punto hoy va a ser igual a la idea que recibo.

Luego viene el completado y por último ups.

Por último tendría el creador.

Déjenme arreglar esto un poco para que se mire por lo menos para que se mire bonito.

Ya tenemos personalizado este tema todo pero ahora yo tengo que regresar la instancia Return de temp.

De esta manera creo en la instancia así como las propiedades así como vengan y esto me va a permitir

a mí poder recuperar mis métodos que tiene la clase que yo definí en esa clase.

Voy a grabar los cambios en donde tengo que llamar este from Jayson ahora porque si es el código así

si sigue seguimos teniendo el mismo problema de que estos son objetos y no son instancias de mi todo

entonces sólo podríamos hacer aquí en él cargar de locales storage.

Una vez ya pasa este procedimiento ya los cargamos de storage ya sabemos que tenemos una de dos o un

arreglo vacío o un arreglo de objetos que parecieran tuus pero son objetos nada más objetos literales

entonces aquí puedo decir que disputo todos va a ser igual a que existe un método en todos los arreglos

voy a ponerlo todos juntos Mapp el Mapp me permite barrer cada uno de los elementos que están dentro

de un arreglo y retornar un nuevo arreglo con cada uno de esos de sus objetos mutados sonará algo extraño

pero si quieres saber más sobre el Mapp por favor vayan a Mozilla envien que debería ser su fuente oficial

de información sobre métodos y propiedades de JavaScript ok así como.

De vez en cuando yo les pongo los enlaces.

Vayan ustedes y Investing un poco más sobre el MAP.

Entonces él va a recibir un argumento que sería un VJ que sería el elemento cada uno de los elementos

que están en ese arreglo de todos los pasos por una función de flecha y lo que quiero hacer ahora es

retornar mi mi nuevo tubo que estoy creando que voy a crear con el from Jayson.

Aquí sería todo por qué lo pongo con las mayúsculas porque es una propiedad estática porque quiero hacer

referencia a esa propiedad estática punto.

From from Jayson parentesis.

Y también noten que from Jayson con ustedes me llevo unas llaves y un argumento significa que tengo

que mandar un objeto y aquí adentro se está haciendo la desestructuración es decir se para cada una

de las propiedades que me interesa.

Entonces aquí voy a mandar él o BJ punto y coma.

Eso es básicamente todo lo que tendría que hacer acá si yo grabo los cambios regreso al navegador web

y nos define ok todos nos define porque no lo tengo importado acá como ustedes pueden observar.

Entonces importemos entonces import algo from Tuxtlas lo puedo dejar así índex o simplemente hacer la

transferencia directamente al todo como ustedes quieran y aquí me interesa importar el tú grabamos los

cambios vamos a ver ahora y en lugar de tener objetos ahora sí tengo instancias de cada uno de sus tubos.

Por consecuencia en el índex ya podría ser esto que tomar el primer todo y llamar la instancia.

El método imprimirlas grabó los cambios de aquí tengo uno tal cosa excelente.

Eso es básicamente lo que quería cubrir en esa parte que voy a borrar esto y esto también.

Esto también no puedo borrar.

Lo único bueno de hecho dejémoslo por los momentos porque todavía quiero hacer alguna pequeña pequeña

optimización

en esta instrucción cumple el mismo criterio que yo les enseñé en el video pasado se acuerdan.

Este mismo criterio que estoy recibiendo un argumento y ese argumento lo quiero mandar por un Kovac

en este caso sería esta función y el primer argumento es el primer argumento que regresa al frizz exactamente

es lo mismo que cumple esto tengo un objeto que es en este caso todo esto es mi Kovac osea toda el resto

de la función que yo quiero ejecutar.

Tengo el argumento y ese argumento es el que estoy mandando aquí.

Entonces por consecuencia yo puedo eliminar esto.

Recuerden esto es opcional puedo eliminar esto y quitar estos paréntesis.

De esta manera cada uno de los valores que va a recibir va a ser el primer argumento que se va a mandar

a esta función o método que grabamos los cambios.

Voy a recargar navegador web y tenemos exactamente el mismo efecto pero nuestro código es un poco más

simple de leer eso ya es opcional si quieren lo dejan si no lo dejan como estaba originalmente lo dejamos

así y continuamos en la siguiente clase.




## 117 Aplicar filtros 09:52

En esta clase vamos a trabajar con la parte de los filtros y no miramos me refiero a esos de acá muestra

a todos que por defecto son los que tendríamos que mostrar pendientes completados y esto ya lo hicimos.

Ok solo nos quedan hacer estas dos partes.

Vamos a comenzar trabajamos en la parte de los componentes y vamos a ocupar también nosotros poder seleccionar

algo en particular o sea para poder hacer clic en algún elemento.

Si nosotros regresamos al índex punto HTML vamos a ver que hay un elemento bueno hay una lista ordenada

que tiene la clase filtros en el cual están cada uno de estos esos como enlaces o aun contactos que

tienen todos pendientes y completados.

Entonces vamos a trabajar con esto voy a tomar aquí la clase fitness crear una constante.

Hay muchas formas de hacer esto por cierto uno perfectamente puede decir bueno si hago click acá o acá

pero quiero hacer un solo Liz tener que estar pendiente de cualquier click que se haga en esta lista

ordenada.

Entonces a este elemento lo voy a darle le voy a poner.

Huele de lista de desliz o un orden.

Perdón filtros y esto va a ser igual a document .4 y selector y seccionar los filtros por el aiki implementemos

una lista en el aquí al final finado están mis listones que al final va a suponer esto.

Punto a deben tener que estar escuchando el evento click voy a recibir el evento función de flecha orillero

Chaves ok.

Voy a poner aquí en Kosovo este evento y grabar los cambios.

Voy a regresar al navegador web voy a tocar acá y ven que se dispara algo en esos tres lugares pero

de hecho hay que tener cuidado porque podría hacer click en medio.

O sea como parte de la lista ordenada y también lo va a disparar.

Entonces vamos a ver qué podemos hacer acá.

Voy a poner aquí y punto target punto text.

Me interesa saber qué es esto.

Voy a grabar los cambios.

Voy a regresar acá voy a hacer click en un elemento y aquí tengo pendientes completados y todos excelente.

Y si yo hago click aquí en medio tengo un defined.

Entonces tengo que nada más tener en cuenta que puede venir con defined.

Para eso voy a almacenar ese filtro en una variable y va a ser igual a esto punto y coma son una sencilla

validación y preguntemos si el filtro.

Recuerden que si el filtro tiene algo entonces entraría pero si pongo el signo de admiración o doble

signo de migración como ustedes quieran pero si no existe entonces lo que voy a hacer aquí es un rechazo.

Por cierto en JavaScript si ustedes sólo tienen una instrucción pueden dejarlo de esta manera y funcionaría

igual a pesar de que se puede dejar así.

Mucha gente se acostumbra siempre aunque sólo sea una línea a ponerla ya es porque queda más claro y

va un punto y coma.

Bueno sigamos.

Qué es lo que quiero hacer ahora.

Si nosotros miramos en nuestro archivo de CSS tenemos una clase acá que esquiven nosotros podremos trabajar

con esto es decir ponerle el atributo Jive dependiendo de lo que esté seleccionado o no. Si están pendientes

entonces que el atributo y no se aplica a esas si están completados que sólo se aplique a los que ya

están completados.

Entonces podemos jugar con esta clase.

Eso es básicamente todo el secreto.

Voy a hacer un ciclo Forth para barrer cada uno de los elementos que tenemos hoy que tenemos en nuestro

ditugu list.

Voy a quedarme una constante llamada elemento o Dip Dudu Liz Punco Children publicó más o menos voy

a hacer un consolón del elemento para ver qué es lo que viene hay que grabar los cambios.

A TOCAR limpiar la tocar un botón y tengo cada uno de los elementos de la lista ordenada.

Les voy a pedir que por favor marquen como completados varios unpar y toquemos el botón y van a ver

que si tenemos completed y todo esto nos puede indicar a nosotros o nos va a servir para saber si este

está completado o no Ok sigamos trabajando por acá.

Eso es lo que teníamos con el elemento algo que vamos a tener que hacer cada vez que hacemos clic en

uno de los elementos algo que vamos a tener que hacer es quitar esa clase given que vamos a colocar

eventualmente.

Por qué.

Porque puede ser que nosotros estemos cambiando dependientes a completados o viceversa entonces siempre

voy a querer limpiar esa clase o quitarla.

Para eso voy a hacer referencia al elemento apuntó.

Las Liseth punto mimó y me interesa borrar la clase given werden que esta clase quieren las personalizamos

nosotros en el archivo de esta processes.

Ahora necesito saber si el elemento actual está marcado como completado o no voy a crear una constante

llamada completado o completada.

No sé cómo se llama ponerle elemento punto Class Lisseth punto y voy a preguntar si contiene el copyright

exactamente lo mismo que hicimos aquí.

Lo que estoy preguntando si este registro o esta tarea está completada.

Ok yo tengo todas las piezas.

Ahora sólo me queda determinar si quiero mostrarlos completados o no. Entonces voy a utilizar un switch

porque quiero ser varias decisiones y voy a evaluar mediante el filtro que está actualmente que puede

ser completado pendientes o todos en el caso de que sea el caso Keys pendientes noten que estoy poniendolo

con la P mayúscula porque eso es lo que tenemos acá.

En el caso de que sean pendientes quiere decir que todos los elementos que estén completados les tengo

que agregar la clase given.

Entonces voy a preguntar si está completado este registro si está completado entonces elemento punto

clave Liseth punto a y voy a agregarle el joven y a su vez no se olviden de poner un Breach porque si

no seguiría haciendo las demás líneas.

Voy a copiar esto no voy a pegar aquí abajo y ahora hace lo mismo pero con unos completados ok y igual

nuevamente aquí tendríamos que preguntarlo puesto si no está completado.

Entonces voy a agregarle la clase ok eso es básicamente todo.

Voy a grabar los cambios.

Voy a regresar a la aplicación.

Recuerden que tengo dos completados.

Voy a tocar los pendientes.

Perfecto.

Ahora voy a tocar los complotados perfecto y voy a marcar ahora todos y se muestran todos.

Por qué se muestran todos.

Me pueden preguntar porque recuerden que el switch entra acá y como no es pendientes ni es completados.

Entonces no hace absolutamente nada y parte de mi comportamiento por defecto es que remuevan la clase

de todos los elementos.

Lo único que nos queda por hacer es que quiero cambiar este cuadrito que está alrededor del todo ese

si no estoy mal.

Se llama Selected que es este Selected que tenemos acá que de hecho la clase está repetida dos veces.

Creo que yo me equivoqué pero bueno sólo sólo ninguna eso lo es en un Selected y esto es la clase que

vamos a tener que cambiar dependiendo de lo que hacemos clic para eso les voy a pedir acá que después

de este y podríamos barrer cada uno de los han cortados perfectamente.

Vamos a hacer referencia a.

Bueno aquí tenemos aun cortas.

De hecho tienen la palabra filtro que filtro filtro filtro.

Podemos crearnos una nueva constante para hacer referencia a ellos llamada filtro o mejor para que tenga

más sentido Ancor filtros.

Lo que sí tiene más sentido es ser un poquito de espacio acá porque me gusta que esto se bien Tocoma

en punto pueden selector y vamos a preguntar por este filtro ok.

Por este filtro me voy a trabajar ahora con esta variable.

Revisemos aquí abajo y aquí vamos a tener que barrer cada uno de nuestros aun cortas y borrar esa clase

Select.

Y para eso vamos a poner punto y aquí yo voy a tener un elemento HTML y voy a remover esa clase Selected

Ok voy a remover esta clase de todos entonces del elemento punto Klaus List punto rimo y voy a remover

las clases.

Por qué.

Porque puede ser que haga clic en todos los pendientes o completados.

No me importa lo voy a barrer todo y ahora sólo le quiero poner las clases Selected a este filtro.

Entonces voy a jugar aquí y ment punto target que si quieren estar seguros podemos hacer un consumidor

de este target para asegurarnos de que sea un eloi.

Entonces voy a Generacción con su look y vamos a ver este target.

Voy a grabar los cambios voy a regresar al navegador web voy a tocar pendientes y filtros frizz no es

una función y es porque si no estoy mal le puse XLS lector y recuerden que esto sólo regresa uno tendría

que ser XLS lector o para que lo regrese como un arreglo.

OK no te puedes el lector o voy a bajar un poco y voy a dejar la pantalla acá vamos a probar de nuevo.

Voy a tocar pendientes y aquí tengo Alcorta excelente toco completados perfecto todos.

Perfecto entonces a este elemento simplemente tengo que agregarle la clase que yo quiero.

A este punto el target porque esto hace referencia al Lehi o perdonaran corta que yo acabo de hacer

click puntos Class list.

Y voy a agregarle la clase select y con eso creo que terminamos de grabar los cambios.

Voy a regresar al navegador web limpiar pendientes noten que el cuadrito se mueve completados.

Ok.

El de borrar completados no porque sólo los purgó todos.

Hago clic en todos y ahí vamos a poder observar que funciona.

Yo no he completado por qué los borré pero si Marco uno como completado entonces muestro que los completados

y ahí está funcionando mi aplicación.

Bueno prácticamente lo único que nos hace falta es subirnos aplicación a algún servidor para probarlo

a probar que funciona en la nube y ya terminaríamos.

Entonces los veo en la siguiente clase y no se preocupen que todavía más temas de JavaScript que quedan

por cubrir.

Así que los veo en la próxima clase.




## 118 Todos en la GitHub Pages 06:43
Bueno es momento de desplegar nuestra aplicación aquí Telles y esto va a ser una tarea que ustedes mismos

lo van a tener que hacer.

Yo les voy a enseñar no les voy a enseñar porque yo lo he hecho varias veces por lo menos una vez.

Pero lo que ustedes van a tener que hacer es tomar toda su aplicación subirla aquí dijo.

Obviamente va a tener que crear un repositorio crearlos dijo Telles y recuerden que tienen que crear

sus docx y esto sería nuestra aplicación anterior recuerden van a tener que volver a generar estos stocks

ponerle pellets volver a generar un móvil de producción etc. háganlo ustedes como si fuera una tarea

póngale el video en este momento y yo regreso con ustedes con la solución en breve así que pasa intenten

hacer todo este despliegue aquí.

Así que manos a la obra.

Mucha suerte.

Ok lo lograron hacer.

Espero que no haya tenido ningún inconveniente.

Voy a comenzar yo voy a crear un nuevo repositorio este repositorio se va a llamar todo menos J.V vamos

a poner algo sencillo.

Ustedes le pueden poner una descripción perfectamente.

Yo no nada más aquí todos.

Bueno tu app lospuntos Javascript Java Script le voy a dar público voy a crear un repositorio y ya lo

tengo.

Ya lo tenemos creado antes de trabajar en el repositorio voy a tener que preparar mi equipo local.

Primero que nada voy a detener todos los procesos.

Ya no estoy corriendo nada como ustedes pueden observar.

Aquí ya no funciona.

Excelente.

Lo primero que tengo que hacer es hacer un guiri init para inicializar mi repositorio.

Pero quiero que ustedes noten que como nosotros clona nuestro repositorio de bueno o usaron el mío ya

tenemos el archivo ignoré que excluye los módulos de Nott por lo cual no hay que hacer este paso.

Estamos excluyendo también el diseño y esos docks es algo que nosotros vamos a tener que generar.

Entonces antes de subirlo puedo hacer todo ese procedimiento o hacerlo por pasos que sería lo conveniente.

Como ustedes vean voy a hacerlo de la siguiente manera.

Lo primero es hacer el comité inicial entonces ya hice el Guidi MIP.

Ahora vamos con el jeep apuntó Kit commit.

Menos heme aquí.

Primer cómic Enter.

Ya tengo todos los cambios o Salleras tengo una fotografía de cómo está el proyecto ahora.

Entonces lo que sigue es generar mi archivo.

Para eso MPM ROM Bildt enter que si no estoy mal el violador vil que puse hace la versión de producción

ustedes lo van a ver lo van a poder diferenciar por el jazz que estoy agregando Yo tengo midis pero

obviamente que bueno yo tengo que reemplazar esta carpeta docx por el contenido del disco.

Entonces puede borrar este Toks renombrar este por docx y discos docx y listo.

Yo ya tengo nuevos cambios.

Entonces a punto quitad punto enter ahora Git commit menos m y con lo que haré algo como docx creado

Perfect o actualizado cualquier nombre que ustedes le hayan puesto.

El siguiente paso va a ser enlazar mi repositorio local con GIP y para eso tengo estos dos comandos

los voy a copiar los voy a pegar acá presiono Enter.

Si la primera vez que lo hacen no debería pedir su contraseña si no la ponen.

Aquí ya se subió a Kidjo por el Xataka de cargar el navegador web y deberíamos ver nuestro repositorio

aquí.

Obviamente ustedes le pueden cambiar esto si así lo desean pero yo tengo todo subido.

Noten que tenemos mi primer cómic y el docks creado excelente.

Ahora vamos a la parte de settings bajamos un poco y dopajes.

Necesito el docx folder porque ahí es donde tengo la carpeta de producción Ginjo pellets sours Soib

perfecto.

Voy a bajar un poco y hay que esperar hasta que esté en verde.

Voy a recargar nuevamente el navegador web todavía no todavía no esperemos un momento.

Esto puede demorar hasta cinco minutos nada más mientras hago tiempo.

Recuerden que el Index es un archivo que no debería tener un jazz como este de aquí abajo porque normalmente

los servidores Linux o los apaches están buscando un archivo índex punto HTML o punto.com o punto PHP

etc etc. Entonces por eso es que el Indec se tiene que llamar así.

Aquí ya sale merde quiere decir que posiblemente ya funcione.

Ahí estoy.

También quiero que no tengan errores porque no le pusieron ningún ícono.

Eso no es inconveniente.

Si vamos a la parte de aplicación local Storage no hay nada.

Voy a crear uno todo uno que se enter y ahí lo almacena también noten que aquí ya no dice el local House

aquí debería decir el nombre de su repositorio que en mi caso es Cleri .15 apuntó.

Entonces cualquier aplicación que yo despliegue en este servidor va a tener acceso a este local Storage

excelente.

Lo mismo sería con el cesion estará expuesto aquí pues así lo desea.

Pero bueno voy a cerrar esto.

Ahora vamos con él dos tres o cuatro Enter.

Voy a marcar varios Toko pendientes completados todos.

Excelente podemos ver el sours de mi explicación.

Voy a recargar nuevamente perdón.

Quiero que miremos dos Oses que yo sé que esto es nuevo pero aquí me dice que puedo pesonal controlé

o manteo y empezar con controlé.

Puedes seleccionar cualquier archivo el mail por ejemplo y noten que todo aparece minimizado y listo

para producción.

Poder leer esto es bastante difícil pero podemos con el J.S. contiene scrip saber clases que me interesa

y note que aquí está todo mi código con una función anónima auto invocada.

Si me voy al final vamos a ver el cierre del mismo.

Aquí está mi código y por eso está funcionando bien mi aplicación y si vemos nuevamente no deberíamos

de tener ninguna constante.

Tenemos una consola de consola que fue lo que nos mostró hacer const no tenemos ninguna y nuestra aplicación

debería poder correr bien en cualquier navegador web y nosotros utilizamos tecnologías y características

modernas de JavaScript.

Bueno básicamente eso es todo lo que quería cubrir en esta sección hemos hecho bastantes cosas.

Espero que hayan aprendido cosas interesantes en JavaScript.

Va a ser estos despliegues poder desplegaran dijo Telles es bastante útil.

Puede ser que ustedes lo necesiten para hacer demostraciones a clientes o bien tener sus aplicaciones

ahí algún portafolio para que miren a sus clientes o posibles jefes que ustedes tienen aplicaciones

desplegadas en la nube que lo pueden hacer.

En fin los veo en la próxima sección.


## 119 Código fuente de la sección 00:05

Código fuente de la sección
Lo pueden descargar del material adjunto o bien ir al repositorio del proyecto:

Repo: https://github.com/Klerith/todo-js

Github Pages:  https://klerith.github.io/todo-js/



Recursos de esta clase
todo-js-master.zip
