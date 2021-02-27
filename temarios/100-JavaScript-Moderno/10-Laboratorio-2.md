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

Para eso voy a escribir MPM instó Enter.

Esto tiene que hacer el procedimiento.

Esperamos un segundo debería tardar mucho y bueno claro eso depende de la velocidad suya de Internet pero no lo dejamos que haga el enemistó.

No se preocupen de estar a punto de terminar.

Perfecto termina y ahora podemos ejecutar el MPM Stadt presionar Enter para que lance y bueno ya ahora mi aplicación para que me permita a mí desarrollar de una manera rápida.

Ok siempre dejemos las herramientas de desarrollo al lado y esto es como yo necesito que esté la aplicación por lo menos para el inicio.

Voy a cerrar esto con la X no con el basurero porque esto termina el procedimiento con la X y hagamos el Source y aquí tengo índex que tiene esta información y acá no esto me va a servir entonces les voy a pedir ahora que tomemos el archivo índex lo vamos a poner aquí dentro de Visual Studio Code COPINH sé todo lo que esté aquí con controlado Cumana lo copian con control C y reemplazan todo el código que tiene el índex actual por este índex junto a HTML y graban los cambios.

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
## 111 Marcar como completado un Todo 10:24
## 112 Eliminar un Todo 04:52
## 113 Eliminar Todos completados 08:49
## 114 LocalStorage y SessionStorage 06:42
## 115 Guardando y recuperando Todos 15:03
## 116 Reconstruyendo instancias de Todos 10:13
## 117 Aplicar filtros 09:52
## 118 Todos en la GitHub Pages 06:43
## 119 Código fuente de la sección 00:05
