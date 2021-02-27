# 08 Módulos y Webpack • 16 clases • :clock1: 1h 56m

* 81 Introducción a la sección 03:30
* 82 Temas puntuales de la sección 00:15
* 83 Introducción a Node, Npm y Webpack 07:48
* 84 Creando un proyecto de Node 06:46
* 85 Exposición del problema y necesidad del Webpack 08:33
* 86 Instalación y configuración de Webpack por defecto 12:25
* 87 Archivo de configuración del Webpack 12:34
* 88 Webpack Dev Server 07:51
* 89 Importando estilos de forma dinámica 09:13
* 90 Creando un archivo de estilos de forma global en la aplicación 10:43
* 91 Nota de actualización 00:17
* 92 Manejo de imágenes 10:13
* 93 Webpack - Production Mode 08:51
* 94 Instalación y configuración de Babel 11:58
* 95 Limpiando la carpeta Dist 04:30
* 96 Código fuente de la sección 00:08

## 81 Introducción a la Sección :clock3: 03:30

Estamos entrando a la sección 8 del curso al fin, y por que digo al fin es que ya es momento de que comencemos a trabajar con Webpack. Esta es una de las secciones que posiblemente más de uno de ustedes de las personas que ya sabían JavaScript quieren entrar y por qué, bueno el qué es Webpack y por qué usarlo y otro montón de cosas hay videos dedicados sólo a eso aquí en el curso, ya van a ver eso y van a ver el porqué es conveniente utilizar algún tipo de herramienta parecida a Webpack, pero sólo quiero hacer una buena pregunta, disparar un pensamiento.

Imagínense que hay compañías gigantescas como Adobe, los que crearon Photoshop, Ilustrador y todo, que ha dejado una cantidad absurda de dinero a la gente de Webpack, solo para que sigan trabajando en Webpack, para que lo sigan impulsando, que lo sigan desarrollando, ¿es extraño no?, ¿Por qué? Porque será eso, pero también hay otras compañías como Slack, como Shopify, como Discure y otro montón, Airbnb, en fin muchas compañías, les da dinero a la gente de Webpack para que sigan desarrollando este paquete y que les sigan dando a ustedes todas esas herramientas para que lo usen de manera gratuita y para que la gente lo siga utilizando y por alguna razón será. 

Otra pregunta que quiero tirar al aire es ¿Por qué Facebook con su librería de React utiliza Webpack y por qué Google con Angular utiliza Webpack, esta interesante no.

Ok así de poderoso es Webpack para que estas compañías gigantescas lo utilizan y ustedes van a aprender a utilizar Webpack en esta sección, es bastante importante que ustedes los conozcan, van a ver es por qué. Espero que quede bastante claro en esta lección porque ustedes deberían de utilizar Webpack o algún tipo de gestor que les ayude a ustedes a realizar tareas automáticas. Sólo quiero hacer un pequeño paréntesis, sólo quiero comentarles una experiencia, es muy posible que ustedes hayan tenido este panorama, crean toda su aplicación y funciona perfecto en su computadora, pero de ahí la despliegan a un servidor de producción, le dicen al cliente, "mirá fulano ya está mi aplicación y ya está tu aplicación lista puedes probarla", llega el fulano, agarra su celular se pone a probarla y no le funciona nada, los llamo a ustedes y les dicen, "Mira Fernando tu aplicación no funciona o no sé qué pasó, es una cochinada", qué sé yo, entonces de ahí ustedes dicen "bueno pero todo está funcionando en mi computadora", pero por qué aquí en la computadora no funciona y cuando ustedes le dicen al cliente que les mande alguna fotografía del error o hacen las pruebas en lo que él tiene, se dan cuenta de que él está ejecutando un navegador web que tiene como ocho, 9, 10 años de no actualizarse y ustedes dicen "ay Pucha y todo mi código yo lo hice con una versión actual de JavaScript utilizando constantes clases y todas las cosas", importación de módulos, que eso es algo que vamos a ver en esta sección también, pero ahora tengo que rehacer toda mi condenada aplicación para poder darsela a esta persona que usa un navegador web muy viejo y esos son casos sumamente comunes especialmente en América Latina, tengan por seguro de que si no les ha pasado les va a pasar. Entonces aquí vamos a aprender cómo hacer y resolver ese problema sin que ustedes tengan que hacer una refactorización de todo su código por que eso sería un verdadero dolor de cabeza. Yo sé que si ustedes ya experimentaron eso espero no haberles traído muy malos recuerdos, pero bueno aquí vamos a aprender cómo modificar y trabajar con eso, utilizando Webpack.

Espero que tenga más o menos una idea de por qué utilizar Webpack.


## 82 Temas puntuales de la sección :clock3: 00:15

En esta sección tocaremos los siguientes temas:

* Más sobre módulos
* Webpack y su beneficio
* ¿Quienes usan Webpack?
* ¿Qué es Webpack?
* Webpack y su configuración
* DevServer
* Hot Reload
* Babel
* Minimización automática
* Crear aplicación para producción
* Optimizaciones para producción
* Manejo de imágenes

Al final, crearemos una configuración estándar para la mayoría de aplicaciones de JavaScript puro, que nos permitirá iniciar proyectos rápidamente sin tener que pasar por toda la configuración de Webpack de nuevo.

## 83 Introducción a Node, Npm y Webpack :clock3: 07:48

Nosotros hasta el momento hemos estado trabajando en JavaScript en nuestros archivos y todo ha estado funcionando relativamente bien aunque nuestro código todo está siempre en el mismo archivo.

Va a llegar un punto donde nuestra aplicación va a crecer y necesitamos poder separar la lógica en varios módulos o en varios componentes que nos ayuden a que sea fácil darle mantenimiento después.

Adicionalmente vamos a llegar a un punto donde ocuparemos tareas automáticas como por ejemplo imagínense que ustedes tengan dos monitores y ustedes no quieren grabar los cambios y tener que ir a la otra pantalla del navegador web, refrescarlo manualmente y ver si se aplicó todo y al mismo tiempo poder ver si sucede algún error para que lo tengamos rápidamente en pantalla sin perder el cursor donde nosotros estamos trabajando en el código.

También puede ser que al final del día ustedes ya necesiten subir su aplicación a producción y hay que

minimizar el código y obviamente uno va a querer ir a la página que le facilite originalmente pegar el archivo y copiarlo regresar a su carpeta de JavaScript pegarlo y eso no es eficiente.

Sin contar que cuando ustedes hacen cambios es recomendado que le pongamos un código diferente o un Hash a los archivos para prevenir el caché de los navegadores web, eso ya lo vamos a ver también. No digamos si ustedes lo quieren ofuscar o algo más crítico que es incrementar la compatibilidad con otros navegadores web pero a dónde quiero llegar.

Posiblemente ustedes han escuchado hablar de NAT y si no han escuchado nada no se preocupe pero si están aprendiendo JavaScript tienen que saber que no existe lo que se maneja popularmente es que no nos permite a nosotros correr código de JavaScript en el lado del servidor lo que nos habilita que nosotros podamos crear aplicaciones tanto del Front como el Backen todo escrito en JavaScript es decir, con JavaScript nos pegamos a la base de datos con JavaScript, grabamos archivos en el sistema o hacemos las modificaciones respectivas en ellos pero también con nosotros podemos trabajar en nuestra computadora como si fuera un servidor de desarrollo y poder realizar tareas automáticas que nosotros no queremos hacer ya que le podemos decir a Ud. o mejor dicho a JavaScript que no se Gute ciertas tareas de forma automática por nosotros.

Pongamos un ejemplo imaginemos que terminamos nuestra aplicación perfecto esta bonita funciona bien y la vamos a probar en nuestra computadora porque nuestra computadora es medio moderna. 

Estamos corriendo en un ambiente controlado todo funciona la aplicación se ve excelente y terminé pero cuando nosotros se lo mostramos a otra persona esa persona está corriendo la aplicación en un navegador web muy viejo o en un entorno muy viejo y nos damos cuenta de que la aplicación no funciona o no funciona como nosotros esperábamos.

Entonces aquí llegamos a un punto donde nos sentamos y ponemos a revisar el código y nos damos cuenta de que estamos utilizando características de ECMAScript6, ECMAScript7, 8 o ECMAScript aún más nuevo que no son soportado por los navegadores web de nuestros clientes.

Y ahí es donde decimos cuerpu y no decir la mala palabra va a haber que volver a programar esto y obviamente nadie quiere estar en esa situación pero créanme a mí me ha pasado y ha sucedido donde hemos tenido que pensar qué diablos hacemos ahora.

Pero para nuestra suerte y la desgracia de otras personas alguien más ya tuvo ese problema antes que nosotros. Hablemos un poco sobre cómo solventar este problema. Ustedes pueden tomar su código de aplicación de JavaScript moderna y pasarlo por una librería llamada Babel el cual también está escrito en JavaScript y les va a convertir todo su código moderno y te permite convertir de manera automática la aplicación tuya para que pueda trabajar en navegadores web viejos así como probaste tu aplicación originalmente y eso fue posible gracias a noted.

También nos permite a nosotros desarrollar de manera local en nuestro equipo.

Babel es uno de los muchos paquetes que están creados para que ustedes simplemente los utilicen. Es gratis. Hay aproximadamente 350 mil paquetes hoy en día en el repositorio de Nott para que ustedes los consuman, los utilicen que están probados.

La mayoría sirve muy bien y el objetivo es que ustedes no necesiten reinventar la rueda simplemente instalen la dependencia necesaria y ustedes están listos para trabajar.

Si ustedes necesitan alguna forma de reconocimiento de caras en las imágenes ya existe un paquete para eso, si quieren hacer videollamadas ya existe un paquete para eso, si ustedes necesitan trabajar con archivos en un servidor ya existe. Si se quiere conectar a bases de datos ya sea SQL o SQL Server ya existe. Entonces esto es algo que muchos lenguajes de programación anhelan tener y gracias a que la comunidad de JavaScript que es gigantesca, posiblemente lo que ustedes necesiten ya existe como paquete y ustedes simplemente lo tienen que consumir.

Ahora se van a preguntar. Bueno yo vi el título de la lección que hablaba algo sobre Webpack pero que es Webpack, en pocas palabras **Webpack es un Empaquetador de Módulos**. Uff bueno eso no me dice nada, me quede exactamente en las mismas, que es Webpack.

En otras palabras Webpack básicamente nos va a ayudar a nosotros a realizar muchos trabajos de manera automática como por ejemplo gestionar las dependencias de nuestra aplicación, y ¿Qué son las dependencias? bueno imagínense que ustedes necesitan sé yo algo que muestre unos mensajes de alerta en pantalla.

Pero ustedes vieron en internet y encontraron un paquete de NodeJS que hace exactamente lo que ustedes necesitan.

El Webpack junto con NodeJS paquetes mãnager instalarlo y manejarlo de manera casi automática y ustedes simplemente se dedican a realizar el código para utilizar dicho paquete.

También les va a permitir a ustedes montar rápidamente un servidor de desarrollo y servidores de pruebas con objetivo de acelerar el proceso de producción para que ustedes no pierdan tiempo en grabar los cambios y ese navegador web refrescarlo.

Algo salió mal al regresar.

No eso es bastante útil a la hora de desarrollar.

Les va a permitir a ustedes también cargar módulos de manera que ustedes puedan segmentar su aplicación en diferentes archivos para que les quede fácil darle mantenimiento y soporte al mismo.

Les permite convertir diferentes formatos en pocas palabras le permite tomar su aplicación y convertirla a otra cosa junto con otros plugins pasar su código de ECMAScript 8 por ejemplo a una versión compatible estándar del ECMAScript 5 por ejemplo, también les puede ayudar a minimizar el código de forma automática.

Ustedes simplemente ejecutan un comando ya lo tienen todo minimizado y listo para producción.

Si ustedes conocen SASS que básicamente es un nivel más alto de CSS para manejo de variables entre otras cosas ustedes cuando hagan cambios en SASS pueden ver los cambios directamente de forma automática en su aplicación.

Lo mismo si ustedes están trabajando con Skype y quieren verlo directamente reflejado en JavaScript.

Pero lo más importante de todo es que nos permite trabajar con JavaScript moderno y preocuparnos de que nuestra aplicación no va a funcionar en navegadores web viejos entre otro montón de cosas.

Ahora el Webpack apasionara que es la octava maravilla del mundo pero también tiene sus inconvenientes y obviamente también hay competencia hay otros gestores que les va a ayudar a ustedes a hacer esto mismo pero Webpack es uno de los más populares en lo personal hay dos cosas principales que no me gustan de Webpack y se las voy a decir una de ellas es que la configuración inicial puede ser un verdadero dolor de cabeza. La ventaja es que cuando ustedes ya la hacen una vez la suben agitprop y ustedes simplemente lo descargan y en fracciones de segundos ya están listos para trabajar y otra cosa es que puede ser algo complicado detectar problemas cuando algún paquete falla.

Pero créanme esto vale la pena cuando ustedes se ven obligados a que su aplicación tiene que correr en navegadores web viejos o tienen que hacer alguna tarea de manera automática que si ustedes lo hacen manualmente les puede llevar horas días semanas o meses si decidieran hacerla manualmente.

Entonces en esta sección voy a aprovechar el tema del Webpack para combinar varias cosas que nosotros ocupamos saber como por ejemplo los módulos que es como importar paquetes como utilizarlos y cómo crear una aplicación básica para que nosotros podamos decidir al día de mañana o que quiero crear una nueva aplicación ya que podría copiar el cascarón que ya tengo de CPAC y en cuestión de cinco o segundos ustedes ya van a poder empezar a trabajar con todo de Wapa previamente configurado por ustedes mismos.

## 84 Creando un proyecto de Node :clock3: 06:46

Es momento de comenzar a realizar la configuración inicial de Webpack y también me va a permitir a mí explicarles los beneficios de un modus Voddler a un generador de paquetes se podría ser así o de módulos y porque ustedes debían de usar alguno.

Les voy a pedir que abramos la carpeta de JavaScript de nuestro proyecto click derecho nuevo folder oponerle 03 Webpack Webpack inicial inicial enter.

La idea de este web inicial es que nosotros creamos el cascarón que nos permite a nosotros poder tomar rápidamente esta carpeta colocarla y luego comenzar a crear aplicaciones que utilicen todo lo que vamos a configurar acá con el objetivo de que esta configuración sólo lo hagamos una vez a la menor cantidad de veces posible.

Ok entonces van a tomar esta carpeta lo vamos a dejar caer dentro de Visual Studio con el editor de texto que ustedes estén  utilizando y tenemos obviamente la carpeta vacía.

Harán la obra terminada la línea de comandos que tenía aquí Visual Studio o puede ser la PowerShell Selden Windows o cualquier otra cosa.

De hecho todo lo que ustedes hacen ahí lo pueden abrir desde la terminal a la ventana de comandos hacer un CD y navegar hacia la carpeta dejarla caer acá Enter.

Enter ya cerramos se aseguran de que estén en la carpeta 03 Webpack inicial eso es todo lo que yo necesito.

Recuerden todo lo que yo hago acá ustedes lo pueden hacer en la terminal en la PowerShell de comandos de Windows y en eso no hay ningún inconveniente pero sí pueden Shiga módulo emisores su Decoud es más cómodo hay un par de cosas que yo necesito que ustedes confirmen que tengan si no los tienen.

Por favor regresen a la parte de las instalaciones iniciales de este curso porque por esos por eso la dejé ahí porque no quiero volver a realizar instalaciones en la parte de cosas que usted debería de tener en su equipo una de ellas Raisa que tengan Nott.

Para eso voy a escribir no espacio menos menos versión y presionan entre ustedes deberían de tener una versión superior a la mía igual o superior a la mía pero si están en la versión 8 para arriba no hay ningún inconveniente es también otra cosa que ocupo que ustedes confirmen que eso se instala con los instala no es el MPM menos versión.

Personalmente ustedes van a ver que deberían de tener ese número o superior al mío pero arriba del 3 estamos bien recuerden el MPM no paquete manager nos va a permitir a nosotros poder gestionar cualquier paquete de Nutt que nosotros queramos nos va a ayudar especialmente a que las instalaciones sean sumamente sencillas de hacer.

Una vez dicho eso borramos esto les voy a pedir que escribamos el siguiente comando tiene espacio INIT y presionar ENTER.

Eso les va a llevar a ustedes a subir un poco y a ver si lo puedo hacer más grande para que ustedes lo puedan ver bien.

Básicamente todo esto les va a guiar a ustedes a crear un archivo llamado el paquete punto Jayson el cual es primordial y todas las aplicaciones en Nott tienen un paquete apuntó Jayson el cual le va a decir a ustedes mismos y a Nott cómo funciona la aplicación.

Qué dependencias son necesarias para pasar a esa producción qué cosas tengo que descartar cuando lo quiero pasar haya producción cosas que sólo necesito en desarrollo entre otro montón de cosas.

Entonces aquí me está preguntando cuál es el nombre del paquete por defecto está tomando el nombre del directorio y si quieren o dejan así se puede cambiar si quieren le pueden poner web pág. web pack inicial o el nombre que ustedes quieran darle.

Eso no importa mucho y ustedes lo pueden cambiar en cualquier momento presiona Enter la versión por defecto de la versión 1.0 .0 ustedes pueden dejarlo así presionar enter.

La descripción puede poner lo que quieran o simplemente presionar ente ésta es bueno.

Este es un cascarón de un proyecto de Webpack que ustedes quieran presionar enter.

Cuál es el punto inicial de su aplicación el Indec.

JS Lo pueden dejar así no importa mucho si hay algún comando para realizar pruebas automáticas.

Lo pueden definir acá.

Por momentos no lo voy a definir voy a presionar enter.

Cuál es el repositorio de GIT que para las personas que no saben qué les va a ayudar a ustedes a mantener su repositorio o su proyecto de manera de que puedan retroceder en el tiempo puedan ir haciendo como fotografías de cómo va su proyecto en base a los cambios.

Les permite a ustedes trabajar de manera colaborativa con otros desarrolladores.

En fin muchas cosas todavía no tengo ningún proyecto de Git para esto.

Entonces voy a pesar gente keywords.

Esto les ayudaría a ustedes cuando lo suban al repositorio de paquetes de Node en el caso de que ustedes estuvieran creando así lo cual les ayudaría a otras personas a poder encontrar su aplicación o su proyecto.

Yo no lo voy a subir ahí entonces simplemente lo dejo personalmente el autor o ustedes pueden poner su nombre o dejarlo en blanco como quieran.

La licencia para usar esto podemos dejar la que está por defecto no hay ningún inconveniente presionan enter.

Básicamente al terminar esto les va a crear este archivo tal cual como está.

Si ustedes quisieran pueden decirle que no pero no tiene sentido porque todo eso se puede cambiar manualmente entonces simplemente vuelven a presionar enter perfect.

Cuando termina voy a limpiarla la terminal acá les va a crear este archivo que ustedes imagino que ya notaron que es el paquete Jayson.

Todavía no hemos hablado sobre los archivos Jayson eso está un poco más adelante cuando hablamos sobre el HTTP peticiones para traer información posteos todo eso.

Ahí vamos a ocupar bastante los archivos Jayson pero como ustedes observarán es muy muy muy muy muy muy muy casi ético pero es muy parecido a un objeto literal en JavaScript.

Tenemos el nombre y tiene un string tiene la versión y tiene otro string tiene la descripción y es otro extremo.

Son pares de valores y aquí en los scripts tiene otro objeto que tiene adentro un test que es otro o otro string y así sucesivamente.

Realmente no son idénticos porque por ejemplo en JavaScript es opcional de que ustedes pongan las llaves del objeto sin comillas pero en un archivo punto Jayson es obligatorio que usen comillas dobles se ponen comillas sencillas.

Eso no es válido y les va a marcar un error.

Entonces comilla doble pero si se preguntan un archivo Chausson prácticamente nació de los objetos literales dijeron o Puchades los objetos literales ves que son bastante eficientes porque hay poca información.

Vamos a crear un tipo de documento que respete esos estándares por decirlo así pero ya veremos más sobre Jayson un futuro por momentos.

Esto es todo ok dejemos la clase hasta este punto aunque ustedes entiendan que no avanzamos mucho por lo menos quería que esta base fuera sólida y que ustedes comprendieran que acabamos de hacer el papel de Jayson.

En pocas palabras cuando empezamos a trabajar y a instalar paquetes va a ser necesario para que yo pueda saber qué paquetes son necesarios para que mi aplicación funcione.

Qué paquetes no voy a ocupar en producción.

Cuáles son los comandos que necesito hacer para crear la aplicación final o el paquete final.

En fin muchas cosas pero eso lo vamos a ver en los próximos videos por momentos dejemos el paquete apuntó Jayson.

Lo dejamos así quedarán los cambios y los veo en la próxima clase.


## 85 Exposición del problema y necesidad del Webpack :clock3: 08:33

En la clase pasada nosotros creamos nuestros paquetes apuntó Yeison que todavía no tengo la menor idea para qué me va a servir.

Y también hemos estado hablando de WEP que tampoco tengo la menor idea para qué me va a servir.

Llegaremos a ese punto y no se preocupen.

Como ya he mencionado en videos anteriores hay alternativas pero una de las principales que ustedes tienen que conocer es que existe esta cosa llamada Wolfpack que la usan compañías como Google como Facebook entre otros lugares como Hervi EMI como Shopify como otro montón.

Si ustedes bajan un poco más en la documentación van a ver que hay patrocinadores van a ver qué bueno que Trivago les deja les ha dejado 350 mil dólares.

Bueno eso es lo que he aportado les ha dado vamos a ver 32000 dólares.

Adobe les ha dejado 12000 dólares y por algo es antes de empezar a utilizar el pack.

Déjenme mostrarles un problema les decimos avisó el estudio.

Cerremos todos los archivos que tengamos.

Voy a pedirles que creamos un nuevo directorio aquí en la raíz del proyecto llamado SRC o sours.

Por favor pónganle ese nombre porque eventualmente el web pack va a verificar esta carpeta por defecto.

Entonces pongámosle Source a quien dentro del short vamos a crear un índex HTML y vamos a crear un nuevo directorio llamado J.S. dentro de JS voy a crear un archivo llamado saben que todavía no lo creamos.

Vamos a hacerlo más sencillo todavía.

Borremos el índex y dentro de Source vamos a crear un archivo llamado índex JS también recuerdan que el nombre no es tan importante por los momentos pero soy siguiendo una convención que usa Wolfpack pero no se preocupen olvídense que existe una simple función aquí en ese archivo índex que es bastante sencilla aunque creamos una constante llamado saludar.

Bueno esto va a ser igual a una función que recibe el nombre de la persona que quiero saludar.

Función de flecha ahora cero llaves y voy a crear un consolón que diga creando etiqueta H1.

Ya lo vamos a ver funcionando lo voy a hacer algo rápido pero no es nada complicado lo que estoy haciendo es algo que ya hemos hecho antes.

De hecho Tocumen excluir elementos voy a crearme una etiqueta H1 en la cual voy a decir que el H1 punto Inaip text nártex va a ser igual a el nombre pero vamos a colocarlo en Baketik que diga hola Koma interpolar Mosse hagamos la interpolación de Strait con el nombre perfecto.

Ahora hagamos referencia al documento punto Goody punto.

Vamos a añadir el H1 que acabamos de crear.

Nada del otro mundo bastante sencillo ya vemos la función para que se pueda ejecutar saludar y vamos a mandar el nombre de ustedes pueden poner aquí Fernando.

Obviamente no sé el nombre del que está viendo el video pero bueno ustedes tienen voy a grabar los cambios en el índex y en el Index apuntó J.V.

Y ahora vámonos al HTML toquen el signo de admiración Tapp y eso les debería de crear un como por decirlo así llamar un estipe que les crea este HTML por defecto.

Déjenlo así en el título pongámosle Wolfpack o el nombre que ustedes quieran y para poder utilizar ese archivo que nosotros hicimos ocupamos importar ese script y eso lo tenemos en blindex apuntó Jota.

Eso sí yo grabo los cambios voy a regresar a la carpeta del proyecto vamos a abrirla aquí en el sol se haga doble clic en el índex.

Ustedes van a poder observar que aquí aparece Fernando Perfecto.

Usemos las herramientas de desarrollo y aquí tenemos creando etiquetas H1.

Ok todo funciona perfectamente no hay ningún inconveniente y ahí vamos.

Ok voy a regresar al código blindex y crearme una nueva constante o variable que ustedes quieran ponerle nombre igual a Fernando y vamos a mandar acá el nombre que pueda grabar los cambios.

Lo único que hizo fue Raimunda constante y mandarlo acá.

Entonces recargó navegador web y ahora yo tengo el acceso al nombre de manera global y eso es un problema es que para eso se habían utilizado los módulos o las funciones auto invocadas o que para evitar esto también tengo acceso a saludar y puedo mandar.

Y esto a crearme bueno volver a llamar a Función que lo vuelva a crear y ya empezamos a ver un par de problemas.

Eso no podría ser posible y deberíamos de controlarlo.

Ok está bien Fernando.

Muy fácil simplemente hacemos el patrón módulo hacemos la función o invocada y se acabó el asunto.

Sí pero qué pasaría si yo dentro de la carpeta sours voy a crearme un nuevo archivo con un nuevo directorio que se llame JavaScript.

Ahora sí lo vamos a hacer y dentro de este directorio vamos a crear un nuevo archivo que se llame pongámosle componentes o el nombre que ustedes quieran o funciones o lo que sea.

Entonces la verdad es que no es conveniente que Udes en un único archivo tengan toda su lógica porque lo hace muy difícil de mantener lo hace muy difícil de leer lo hace muy difícil de encontrar errores y al fin del día o al final del día no es conveniente que ustedes tengan algún montón de archivos.

De esta manera pueden hacer que tengan hasta 30 40 archivos de scripts y recuerden que cada uno de estos archivos va a hacer una petición HTTP hacia su servidor donde tienen la aplicación corriendo.

Entonces no es lo mismo que la computadora sólo lea un archivo grande a que haga un montón de lecturas a diferentes espacios de disco para recuperar la información.

No es lo mismo es más eficiente que sólo lo hagamos con un único archivo pero aquí espero que vayan viendo por donde va el asunto.

Si nosotros nos ponemos a pensar esta función de saludar no debería de estar en el Index.

La quiero tener separadas.

Voy a cortar y la voy a pegar aquí en los componentes que la quiero pegar aquí en los componentes me grabo los cambios en archivo componentes y también voy a grabar los cambios en el archivo índex.

No he hecho nada más simplemente me moví por donde funciona acá y ya no están ni índex pero si ahora recargo navegador web tengo un problema porque me dice que saludar no está definida pero no sé tal vez ustedes han escuchado que en jabas que ahora existe una forma de importar módulos se podría decir que para importar un módulo o un módulo sería un archivo independiente que contiene cierta funcionalidad que yo necesito en otro archivo.

Por ejemplo en este índex yo necesito esta función saludad entonces para eso podemos hacerlo de la siguiente manera.

La palabra reservada import voy a poner llaves para indicar qué es lo que yo necesito importar pero tengo que especificar Frome de qué paquete quiero importarlo.

En este caso voy a poner puntos las J.V las componentes puntico coma estoy haciendo referencia a este archivo.

Noten que estoy en el Indec si estoy acá necesito entrar a la carpeta J.V y dentro buscar archivos componentes.

Si ustedes no le ponen el punto JBS eso está bien.

Es normal porque por defecto va a buscar un archivo con extensión J.V así que no importa si ustedes tuvieran un archivo HTML HTML siempre va a buscar un archivo apuntó J.S.

Pero si son paranoicos no hay problema pueden dejarlo con el punto J.V y aquí adentro podemos buscar la función saludar y noten que aquí ya me lo está encontrando avisó el estudio.

Las elecciones y en teoría ya debería de funcionar mi aplicación.

En teoría voy a grabar los cambios pero recuerden que en el Indec yo sólo tengo importado el Indec apuntó J.V.

Es decir este archivo está chivó es el que está requiriendo o está solicitando que por favor me traiga esta información.

Si yo regreso navegador web cargo tengo un problema por qué me dice de que yo no puedo usar importaciones si estoy fuera de un módulo.

No tengo la menor idea de qué diablos era eso.

Lo único que estoy viendo es que no está funcionando mi implicación como yo esperaba.

Entonces aquí es donde nosotros ya empezamos a ver la necesidad de poder trabajar de alguna manera un poco más eficiente por ejemplo de que yo tuviera los diferentes archivos de llaves que necesito por ejemplo mis clases o mis modelos lo sé las funciones que modifican el HTML entre otras cosas entonces espero que vean la necesidad de poder trabajar de alguna manera más ordenada.

Poder importar módulos podrá importar lo que necesito cuando lo necesito y algo muy importante poder utilizar librerías de otras personas en mis propios proyectos.

Y vale la pena decir que tecnologías como Kubiak y angular ya tienen incorporado el WEP pack por defecto.

Entonces cuando ustedes crean una aplicación ya sea real o angular por defecto hace toda la configuración que nosotros vamos a ver y otras cosas obviamente algo especializado a cada una de esas tecnologías.

Si ustedes no saben que es vía angular no se preocupen hay cursos especializados en esos temas pero son tecnologías que les ayudan a ustedes a crear aplicaciones utilizando javascript modernas.

Pero lo que quiero que vean es que tecnologías que son muy demandadas hoy en día o programas que son muy grandes o aplicaciones móviles muy grandes hoy en día utilizan Wolfpack.

Para qué.

Eso es lo que vamos a ver en los próximos videos.

## 86 Instalación y configuración de Webpack por defecto :clock3: 12:25

Bien en la clase pasada nos quedamos en el punto donde teníamos una aplicación rota que no me permite a mí importar mi función saludar y utilizarla en otro archivo o que vamos a intentar resolver eso pero para eso trabajaremos con Huapaya.

Les voy a pedir que puede ser que la documentación cambie.

No sé si eso cambiará o no será un poquito diferente.

Hagamos clic en la documentación podemos hacer clic en gadgets y luego en Guérin Start.

Igual yo les dejo a ustedes en el material adjunto el R.L que los lleva directamente a esta página.

Pero recuerden no se asusten si el estilo cambia los comandos que vamos a ejecutar ustedes los pueden escribir directamente en la consola para realizar las instalaciones.

Básicamente lo que quiero que ustedes vean con esto es que aparte de que Wolfpack podría ser un curso independiente porque hay muchas cosas acá hay bastante bastante que hablar sobre Wolfpack pero lo que yo quiero es que nosotros empecemos a trabajar de aquí en adelante en nuestras futuras aplicaciones de JavaScript utilizando un empaquetadora como Wolfpack que nos va a ayudar a que podamos desarrollar más rápido aunque la configuración inicial sea un poquito dolor de cabeza como les había mencionado originalmente.

Es bastante conveniente y útil tener algo como web que nos respalde o que vamos a ver esta parte de la instalación.

Ya tenemos el comando bueno aquí no un comando para crear la carpeta simplemente se me Qadir como crear Directory y Hueyapan demo nos movemos a esa carpeta como ya lo hicimos MPM init menos y griega.

Eso prácticamente ejecuta el comando del MPM INIT y decirle que sí a todo esto nosotros ya lo hicimos eso fue eso es para crear nuestro paquete apuntó Jayson.

Ok aquí sí ya viene la instalación.

Y ojo que tienen que estar en la carpeta del proyecto donde está el paquete apuntó Jayson.

Es decir para los usuarios de Windows se van a la terminal estudios y escriben Dir. para usuarios de Linux y o SX escriban L.S. y presionan entre ustedes deberían de ver ahí el paquete apuntó Jayson.

Eso quiere decir que estamos en el directorio ideal para ejecutar los comandos de MPM porque tiene que ser capaz de poder encontrar este archivo directamente.

Si ustedes estuvieran en la carpeta sours por ejemplo se dé ese enter y hacen un L.S. o hundir en Windows.

Ustedes no ven aquí el paquete apuntó Jayson.

Por consecuencia si ustedes intentaran ejecutar este comando les va a fallar ok entonces eso es una pequeña nota.

Voy a hacer un CD punto a punto para regresarme y noten que estoy en la carpeta del web inicial y si hago el Dir o el L.S. aquí puedo ver mi paquete apuntó Jayson.

Eso es algo un error bastante común que yo veo cuando se intenta hacer un paquete de noveno usando MPM y no me encuentra en el directorio correcto.

Una vez dicho eso voy a cerrar todo que voy a cerrar todo ahoran para 8.10 y eso me suena necesario sólo quiero que vean la modificación de lo que va a pasar acá cuando ejecute este comando lo van a copiar lo vamos a pegar acá bueno ahí no aquí abajo ok lo pego aquí abajo y noten que estoy ejecutando varias cosas estoy diciendo MPM como de Nott paquetes mãnager.

Por favor haz la instalación o instala.

Vale la pena decir que sólo pueden poner y eso sería lo mismo instala el huev Pack que básicamente está escrito en JavaScript ya vamos a ver qué es lo que pasa.

Adicionalmente también instala o instala el web Bacci el Heyt que es el Cumandá interfaz y luego viene esta otra bandera que es menos menos Soib menos de presionar enter porque esta instalación puede demorar un poco y me agachas a de explicarles algo.

Básicamente lo que sucede acá le estoy diciendo a mi aplicación en náhuatl que necesito instalar Wolfpack no necesito instalar este Ciela también y que esto lo ponga como una dependencia de Desarrollo.

Por qué.

Porque el web es algo que no va a ir a producción es algo que no va a ir al servidor una vez termina.

Esto puede demorar dependiendo de su conexión a Internet puede ser que demore más puede ser que demore menos.

Aquí ustedes van a poder ver que se instala lo que se parcela en los paquetes que yo quise instaló adicionalmente 457 otros paquetes.

Dios mío eso parece absurdo pero ya lo vamos a ver no vamos a ver todos los paquetes sólo vamos a generar.

Y también hay tres paquetes que parece que no te vas a encontrar.

Eso puede ser el MPM faraon pero no hace falta.

Eso está bien.

No se preocupen.

Lo importante es que tenemos los paquetes que nosotros queríamos que se sepan y el pack Seeley.

No hay vulnerabilidades perfecto desperfectos algo que ya se corrigió antes aparecían un par de cosillas pero ya terminamos.

Voy a cerrar esto ustedes van a notar ahora que en el paquete punto Jayson se crearon estas dependencias de desarrollo.

Como les dije el web pack sólo va a servir para que yo creé aplicaciones locales aquí en mi equipo pero también creó este directorio bastante famoso llamado módulos.

Si ustedes abren esta carpeta se van a ir de espaldas porque aquí está todo lo que necesita para correr o bueno todo lo que yo le dije a mediante el enemistó que instalará y eso también instala las dependencias de otros paquetes que son una cantidad absurda.

O sea son un montón.

Pero todo esto es necesario de alguna otra manera para que funcione correctamente el Wolfpack en el equipo y si ustedes hacen más instalaciones posiblemente se vayan agregando más paquetes.

No se asusten porque esta carpeta puede ser muy grande de hecho si regresamos aquí a la carpeta de los módulos de Nott que se creó si lo miramos es de 22 megas.

Obviamente Sub22 megas.

Yo no los voy a desplegara en la carpeta de producción son sólo para desarrollar lo que me ayuda a desarrollar.

Ustedes se preocupan de eso.

Si nosotros revisamos ahora a la documentación de Wolfpack vamos a ver un poco y nos pide la creación de los archivos esto no lo voy a hacer de esta manera porque puede variar y vamos un poco a está cargando deudas que es muy parecido a Londres.

Déjenme revisar si hay algo adicional acá parece que parece que viene con una configuración.

No eso es todo lo que voy a ocupar.

Voy a cerrarlo pero si ustedes necesitan más información sobre el huev Park pueden ver en la documentación oficial por si acaso quieren saber más.

Casualmente me detuve en el lugar donde quería llegar aquí quería buscar.

Y es que en el paraíso pronto Yeison se está creando un video Wolfpack.

Vamos a ver qué es esto.

Regresemos al paquete apuntó Yeison.

Dentro de los scripts aquí al final de los test a poner una coma.

Creamos un método llamado Bildt Bildt pero lo escribimos bien por el amor de Dios.

Veo dos puntos y lo que vamos a ejecutar aquí adentro es Wolfpack.

De esta manera entonces lo copiamos lo pegamos aquí adentro y eso va a ser todo por los momentos grabar los cambios en el paquete puntillazo.

Con esto lo que yo le estoy indicando a mi aplicación es que cuando yo ejecute el comando Bildt dispara Wolfpack con su configuración por defecto en mi proyecto y por defecto va a buscar esta carpeta sours ver los archivos de JavaScript y los va unificarlos va a comprimir y los va a dejar listos para producción.

Ok vamos a ver si eso es cierto.

Para ejecutar este comando vamos a abrir la terminal siempre recuerden que tienen que ser capaces de ver el paquete apuntó Jayson.

Siempre tiene que ser así.

Aquí voy a escribir MPM no Package Manager Ron Bildt.

De esa manera lo van a escribir y presionan enter.

Esto va a ejecutar el comando de web pack con la configuración por defecto porque no hemos hecho nada.

Aquí vamos a ver un Warden que dice Bueno la configuración por defecto se dice que está en producción habría que cambiarlo a desarrollo.

Bla bla bla bla bla bla.

Pueden ver más información aquí.

Bla bla bla bla bla no importa.

Cerremos esto lo importante es que no tiro a ningún error y tenemos varias cosas que realizó leyó dos archivos encontró componentes puntos JS encontró el Index hizo el Bill y podemos cerrar esto.

Ahora ustedes notarán que aparece una carpeta disto o una carpeta que ustedes no crearon esta carpeta la creó fue por nosotros.

Si lo abrimos y abrimos el mail van a ver algo bien extraño aquí.

Lo primero que ustedes deberían de notar es que se está creando una función para encapsular mi código.

Tenemos otras cosas que ya se nota que eso está ofuscado.

Puede ser que tuviera otro nombre pero aquí ya todo el código está ofuscado y si nos vamos al final al final del archivo aquí ya tenemos nuestro código.

Quiero que noten que estamos usando el Yussef Street creó la función aquí se está llamando a la función que es bueno saludar y estamos mandando el nombre que da Fernando y básicamente aquí me tradujo mi código a algo más estándar.

Pero a su vez hay varias cosas aquí que dicen bueno esto es demasiado código para todo lo que es bueno para las pinches dos líneas de código que yo escribí.

Sí pero aquí está cargando todo lo que ustedes van a necesitar para importar módulos para trabajarlos de manera segura para protegerlo entre otras cosas.

El mail punto Jota ese es su Bondone.

Así se conoce es su aplicación de JavaScript tal cual con todos sus archivos javascript en una única importación.

Yo voy a cerrar ese mail y voy a cerrar el paquete apuntó Jayson.

Ahora si yo abro el Index punto HTML.

Yo no quiero hacer referencia al indiscutido HTML o hice referencia a este mail para ver si funciona entonces.

Noten que estoy en la carpeta es en ese entonces punto.com Slash.

Pude irme a la carpeta ADIS y a seleccionar el mail.

Voy a grabar los cambios.

Voy a regresar al navegador web.

Busquemos ese archivo.

Creo que ya lo tengo aquí abierto.

Voy a recargarlo y tenemos un error.

Ok este error que tengo acá no es algo que yo estaba esperando que sucediera pero mejor que me sucedió.

Por qué me va a ayudar a explicar algo muy importante y es que gracias a que estamos trabajando con módulos es decir haciendo estas importaciones nosotros podemos decirle a JavaScript qué cosas quiero exportar y qué cosas no. Es como crear propiedades privadas por decirlo así.

Puede ser que yo en mi archivo de componentes yo no quiera que nadie afuera de este mismo archivo o este módulo por decirlo así o alguien fuera de ese archivo pueda ejecutar la instrucción saludar que casualmente si yo no especificó nada.

Esto es lo que sucede está bloqueando de que otros archivos puedan acceder eso y por eso tengo el error acá que me dice que el Gobierno es una función para indicar que yo puedo utilizar esta función fuera de este archivo.

Lo único que tengo que poner aquí es la palabra Export espacio y grabar los cambios.

Ok entonces nada más sólo para que ustedes vean voy a escribir aquí saludar.

Y ahora si aparece ya en azul eso me habría parecido raro que no aparecía como una propiedad o algo que yo podría importar de ese archivo.

Entonces noten que apareció más o voy a grabar los cambios y voy a tener que volver a ejecutar el comando de MPM round Bildt pueden tocar la flecha direccional arriba para ejecutar erróneamente el comando anterior presionar enter hace nuevamente todo el proceso.

Voy a regresar a mi navegador web recargó y aquí todo funciona.

Interesante excelente pero hay algo que quiero que ustedes noten.

Qué pereza tener que estar haciendo los cambios tocaré DPM Rockville volverlo a compilar para producción y tenerlo listo y ese guarda me estorba y tener que hacer modificaciones aquí en el índex.

Si yo tuviera más archivos sin HTML mezclarlo.

Qué pereza qué dolor de cabeza no quiero hacer eso.

Ok entonces nosotros mediante la configuración una configuración que le podemos decir al CPAC podemos decirle que índex lo mueva también que automáticamente asigne el archivo y otra cosa también que me gusta mucho qué hace el web es ponerles a ustedes como por ejemplo poner acá y especificar su número aquí algo así raro con varias letras y otras cosas el cual es muy útil si ustedes quieren prevenir que su aplicación sea almacenada en el caché del navegador web de un cliente.

Es decir si ustedes hace algún cambio en su aplicación entonces al utilizar hojas como éste el navegador web va a notar que el archivo cambió entonces hay que volver a hacer la petición de todos un nuevo código.

Entonces es bastante interesante eso ya lo vamos a ver cómo hacerlo de forma automática pero por momentos quiero que ustedes observen que ya pudimos importar información o en este caso una función de otro archivo en nuestro índex punto JBS o sea en otro archivo de JavaScript lo que hace que mis componentes o sea sólo se dedique a hacer la tarea que yo le dije y en mi INDC simplemente lo estoy utilizando.

Ok en teoría mi Index es el punto inicial de mi aplicación por los momentos vamos a dejar esta clase a este punto y los veo en el próximo video.

## 87 Archivo de configuración del Webpack :clock3: 12:34

Ok nosotros ya vimos una pequeña ventaja de trabajar con Wolfpack pero todavía hay cosas que tenemos que configurar.

Bueno de hecho no hemos configuro nada todos estos comportamientos por defecto del pack.

El objetivo también de esta carpeta dista y ustedes pueden borrar perfectamente y pueden ejecutar erróneamente el comando de MPM Rodil y eso la vuelve a generar.

El único inconveniente que tenemos es que el disco usualmente debería de ser lo que yo voy a subir a mi servidor eso lo vamos a hacer después.

No se preocupen si lo vamos a subir a un servidor.

Pero la cosa es que esta carpeta DayZ así como está solo tiene el main que es la combinación de todos mis archivos de así como lo tengo.

El problema es que también debería de estar el archivo índex HTML acá y no sólo eso también el índex debería tener el pack correcto a este archivo.

Entonces yo tampoco quiero tener que hacer la manipulación de este archivo directamente por varias razones porque es muy fácil olvidarlo y cuando yo ponga hojas para cambiar o prevenir el caché un Jarillo aquí ya lo van a ver.

Entonces tampoco quiero modificar nada manualmente eso es algo bien interesante que tiene web que nos permite a nosotros poder gestionar tareas automáticas por nosotros.

Entonces voy a cerrar todo esto.

Para comenzar me voy a enfocar en crear un nuevo archivo Wakka ese nuevo archivo tiene que tener este nombre PAC Punto confi punto J.

Ese no es un archivo de JavaScript pero el icono que aparece aquí es esa que estoy utilizando material icons que es una excepción de Visual Studio que me pone ese icono indicando que es el archivo de configuración de Wolfpack.

No es que sea obligatorio se puede poner cualquier nombre que quieran pero tendríamos que especificar Roca cosa que posiblemente hagamos un poquito más adelante cuando queremos una configuración específica para producción pero por el momento si ustedes dejan este nombre esa es la configuración por defecto que web va a buscar cuando ejecutemos el MPM rompibles.

Ahora sí vamos con la configuración de web y se recomienda que lo hagas módulo punto export.

Esto va a ser igual a un objeto literal o lo vamos a hacer de esta manera.

Así está la documentación y es bueno así se recomienda Hay varias configuraciones que vamos a poner acá.

No sé si ustedes se acordarán pero vamos a ver si lo tengo acá si hago el N.P me rompí.

Eso si quieren no lo hagan solo quiero ver un error aquí está bueno un error un warning que dice que el modo como está establecido entonces lo está haciendo en modo de producción por defecto cuando se hace en modo producción pasan varias cosas importantes como por ejemplo remover comentarios de Jarkko de Olimpio simplificarlo muchas cosas pero cuando estamos desarrollando yo necesito mis comentarios yo necesito ver las cosas así como están entonces aquí especificamos una propiedad llamada Mod que tiene como nombre development.

Ok que lo pueden copiar de acá o lo copian literal.

Si esto estuviera mal mal escrito entonces nos daría un error.

Asegúrese de que esté escrito de esta manera.

Cómo.

Luego viene el módulo lospuntos el módulo es donde empieza a tener la configuración del web pateé cerrar esto para tener espacio dentro del módulo.

Nosotros podemos definir reglas aquí dos puntos abren y cierran llaves.

Y aquí es donde ya se piensa poner un poquito fea la cosa pero no se preocupen recuerden que eso sólo se hace una o dos veces en la vida y luego simplemente ustedes copian un archivo de configuración de la que ya hicieron anteriormente que funciona.

Se acabó el asunto.

Las reglas sirven para decirle al web qué hacer con ciertos tipos de archivos o que haga en ciertas o en ciertas ocasiones.

Es una regla si el objetivo literal de una regla es lo personal yo quiero que cuando haga el Bildt también me mueva índex punto HTML a la carpeta de distribución.

Por eso es el nombre Tiz y para eso voy a ocupar e instalar un par de paquetes Ok voy a hacer esto un poco más grande limpiar la consola y vamos a hacer un MPM instó espacio recuerda que sólo podían ponerla ahí sería lo mismo menos menos de menos de que también perdonase y de esa manera que también todo eso se puede resumir simplemente poniendo el dash de mayuscula de Development espacio.

Son diferentes formas de hacerlo.

Pueden hacer lo que ustedes quieran y vamos a importar dos módulos.

Miren bien cómo lo escribo.

Uno es el HTML menos louder.

Si lo escribiéramos mal y al intentar ejecutarlo nos daría un error pero mire como está escrito espacio y el otro es HTML menos web pack menos plugin.

Ok.

Esos dos paquetes me van a permitir a mí hacer dos cosas 1 mover el archivo HTML acá y el segundo también me va a permitir a mí decirle a Webb pa que incrusta automáticamente el fondo en el Invex.

Ya lo vamos a ver funcionando.

Presionamos Enter.

Asegúrese que esto haga la instalación.

No diría que tarda mucho pero depende su velocidad de Internet.

Aquí están los dos paquetes que se instalaron.

Perfecto.

Voy a cerrar vámonos al punto Jayson.

Y aquí deberíamos tener el HTML Louder y el HTML Wolfpack plug in genial.

Simplemente con hacer eso ya tenemos a nuestra disposición dichos archivos o dichos paquetes que también nos podrían encontrar en la carpeta de todos.

Si ustedes quieren buscarlos entonces en las reglas voy a especificar una nueva y se comienza a definir como un objeto literal el cual tiene que tener un test que es la condición que Wolfpack tiene que hacer cuando esté evaluando archivo por archivo y esta condición se va a aplicar si el archivo cumple la siguiente expresión regular que yo sé que no hemos hablado de expresiones regulares pero una expresión regular me permite buscar coincidencias de lo que yo sea que especifique aquí adentro en un string.

Pero para no aburrirlos mucho con eso voy a ponerlo de esta manera.

Esto le dice a Webb Pak que aplique esta regla si es un archivo con extensión punto HTML y eso es todo ok aquí vamos a poner una coma enter y si es un archivo HTML.

Voy a decirle que use lo siguiente.

Nuevamente abrimos otro objeto y yo sé que eso ya se empieza a poner un poco bizarro pero bueno eso es lo que les mencionaba originalmente.

Pero la verdad cuando ya se entiende esto no va a pasar de ser más complejo que esto.

Qué es lo que quiero que haga cuando agarre o encuentro un archivo HTML.

Bueno primero usé el Louder lospuntos y el HTML menos Louder que eso fue lo que importamos.

Como también hay algunas opciones que podemos configurar pero vamos a dejarlo así por los momentos.

Una pequeña nota de actualización así como lo acaban de hacer ustedes es como se hacía hace un par de días pero desde equilibraron la versión 1.0 del HTML Louder ahora tenemos que hacer la configuración de esta manera.

Pero todo lo demás es igual.

Es decir cambian el código que acaban de escribir y déjenlo como están viendo ahora y continúe con el video.

Eso sería todo el cambio.

Por ahora también vamos a ocupar el plugin que instalamos.

Voy a quedarme una constante que se llame HTML Wolfpack plugin que va a ser igual a recurriré HTML Web.

De esta manera si ustedes se preguntan qué es esto.

Es una manera que tiene Ud. para cargar estos archivos para cargar archivos de otros paquetes.

Eso es normal pero eso es todo lo que estoy requiriendo.

Ese paquete en esta aplicación y como en el fondo cuando ejecutamos el Wolfpack lo está ejecutando.

No no reconoce ese comando y no le batirán ningún error porque este plugin generará una constante que es igual a ese paquete pero en donde voy a poner este paquete antes de que se cierre esta llave.

Justo después de esta que tengo acá voy a poner una coma enter y voy a escribir plugins.

Dos puntos abren y cierran llaves pero las llaves cuadradas y voy a especificar los plugins que yo quiero en este caso sólo tengo uno y creo que sólo con uno bastará por los momentos.

Voy a decir DIW HTML WEP plugin que es lo que yo acabo de importar acá.

Parentesis abren cierran llaves yo sé que todo esto sonará un poco raro y que cómo se van a memorizar todo esto.

No sé no se preocupen realmente simplemente ver la documentación y ahí explica cómo se utiliza y ahora viene la configuración de ese plugin que es bastante sencillo.

Tiene el temple que básicamente le dice a Wolfpack qué archivo es el que quiero tomar este caso quiero tomar el SRS Slash índex punto HTML y hacia donde quiero colocarlo.

Entonces Filey lo voy a colocar en el punto índex punto HTML.

Básicamente esto es toda la configuración y no hay ir más complejo de esto Ok voy a poner una coma aquí pero es opcional.

Voy a grabar los cambios y vamos a ver qué pasa ahora si quieren pueden borrar el disco que logramos el disco.

También podrían borrar los módulos de Now pero para eso ocuparemos otro comando del enemistó para que lo reconstruya pero no lo borremos por ahora.

Esto no es un curso tan orientado a nada solo quiero que lo usemos y que tengan los conceptos y borré el disco.

Ejecutamos nuevamente el comando asegúrense grabar los cambios en el Wolfpack del RPM Ron Bildt presionar enter un flash pero vamos a ver qué pasa.

Vamos a ver si el Taltal encontró el índex esto es buena señal que pesa tanto que también hizo el main tal cosa que en un resumen de lo que hizo.

También se pueden ver en Trípodi en donde fue igual índex.

Vamos a ver qué pasó ahora en la carpeta Adis todo parece estar bien.

Aerodisco y cerramos esto ya tenemos nuestro índex HTML acá lo voy a abrir tenemos dos importaciones Alamein.

Ustedes pueden observar y por qué creen que sucede.

Con la configuración que yo le acabo de decir a CPAC le estoy diciendo que tome HTML y como es es el archivo principal de mi aplicación.

Entonces adjunta el mail que es que tendríamos acá este otro realmente no va a servir.

Por consecuencia lo voy a borrar aquí de El Index puntuó HTML porque aquí no lo ocupo yo sé que el web PAC cuando lo haga o sea cuando haga el Bildt va a colocar esa importación por mí y para las personas que están acostumbradas a trabajar con angula esta es la razón por la cual no hay otras importaciones adicionales de Scripps aquí porque el web Pak lo hace por ustedes.

Entonces vamos a ver si esto es cierto.

Nuevamente voy a ser MPM.

Run Run fight enter hace la configuración nueva.

Bueno nuevamente construye el diseño y aquí tenemos la importación en el.

Por consecuencia yo puedo cerrar todo esto abrir el archivo de inicial dis abrir el Index puntu HTML.

En otra ventana y ven que todo funcionó sin hacer ninguna configuración en la parte de HTML ya lo hizo todo por nosotros y básicamente eso es todo lo que vamos a ocupar por ese lado.

Pero antes de terminar la clase Déjenme mostrarles algo interesante que también tiene el HTML Louder pudiera ser que cuando ustedes lo generen para producción también quieren que el índex y los HTML estén simplificados o minimizados en una sola línea.

Eso le ayuda al navegador web a que cargue menos información menos información basura como por ejemplo si lo dejáramos así empieza a cargar estas líneas en blanco docentes y la verdad no son necesarios para nada.

Y si tuviéramos comentarios esos comentarios también tienen cierto peso en la página web por ejemplo.

Este es un comentario en HTML y si ustedes tuvieran mil comentarios HTML en su aplicación eso sería algo que el cliente también va a cargar entiéndase el cliente.

El usuario final de nuestra aplicación entonces pudiera ser que ustedes no necesitan todo este montón de comentarios entonces para reducir eso para borrar todos esos comentarios podemos poner unas opciones Options los puntos encierran llaves voy a colocar aquí Minimoys mi país su escribirlo bien Tru graba los cambios vamos a ejecutar nuevamente MPM Brondby al presionar enter.

Perfecto.

Ya lo hizo.

Miremos el Index ahora en nuestro la carpeta de distribución y observar que tenemos ahora todo en una sola línea y no hay ni un solo comentario.

Pero si ejecutamos esto en el navegador web sigue funcionando exactamente igual.

Por los momentos les voy a pedir que la configuración del Wolfpack lo dejemos como falso porque si quiero ver ciertas cosas en mi archivo índex de producción.

Entonces nuevamente r.p.m ROM Bildt miremos nuestro índex y este no es este de acá y aquí sí van a ver que respeta todos los comentarios y lo dejó tal cual teníamos nuestro índex aquí pero con excepción de que está añadiendo a del JavaScript.

Espero que esta clase les haya interesado bastante todavía hay más configuraciones que tenemos que hacer pero lo dejamos así por ahora los veo en la próxima clase.

## 88 Webpack Dev Server :clock3: 07:51

Qué viene en nuestra aplicación está funcionando o estamos pudiendo importar módulos tenemos el Wattpad quien nos está ayudando de cierta manera pero a mí ya hay algo que me está estorbando y ya no quiero volver a ser que es que cada vez que yo necesito generar este edits para probar mi código imaginémonos que yo abramos el componente de etiqueta H1 por ejemplo en el HTML por ejemplo si yo grabo los cambios son precaucion y recargo yo no veo ese cambio aplicado acá.

Por qué.

Porque yo tendría que venir acá ejecutar la flecha direccional arriba o el MPM Bildt presionar enter.

Esto lo vuelve a compilar regreso al navegador web recargó y ahí sí tengo los cambios.

Pero qué pereza hacer esto.

Entonces eso es lo que nos vamos a enfocar en esta clase ya el huapango o mejor dicho algún desarrollador tuvo ese inconveniente y de ahí surgió la necesidad de este paquete que les voy a enseñar.

Entonces vamos a instalar algo en nuestra aplicación que ãramos la terminal y esa es la ventaja de los paquetes de Nott que es bastante sencillo hacer instalaciones.

Vamos a hacer un MPM instó o simplemente menos para que lo haga como una dependencia de desarrollo.

Si ustedes no especifican eso es una dependencia de producción entonces podemos poner menos CPD o menos de espacio y vamos a escribir web menos de menos Server y presioné enter eso es el servidor de desarrollo de web básicamente eso es todo.

La instalación puede demorar unos minutos dependiendo de su conexión a internet así que esperemos que esto termine ya casi hasta que lo hizo nueve segundos aquí so when the observer perfecto lo instalo y listo.

Cerremos abramos el paquete apuntó Jayson.

Y aquí lo deberíamos de tener aquí.

Que lo deberíamos de tener si quieren que piense esto por qué lo vamos a ocupar escribir que lo copiamos bien que nos permite hacer ese server.

Hay dos cosas que hay bastantes inconvenientes por los momentos.

Hasta el momento nosotros hemos venido trabajando en nuestras aplicaciones ya que usando el protocolo FEIL que estamos viendo acá pero debería ser normalmente algo como HTTP 2.2 HTTP 2.6.

Las islas y algo por el estilo o HTTPS.

Por qué no estas aplicaciones usualmente van a correr en la web y nuestro protocolo tendría que ser algo parecido o similar a como nuestra aplicación va a funcionar cuando esté desplegada en la web sin contar que ciertas importaciones que nosotros tenemos no van a funcionar si lo hacemos usando el protocolo Feil.

También peticiones HTTP pueden fallar traer información de algún servidor.

Hay ciertas cosas que pueden fallar por lo cual tenemos que correrlo en algún servidor entonces con solo hacer la instalación de este paquete.

Nosotros ya automáticamente configuramos para nuestra aplicación un servidor de desarrollo y cómo lo usamos.

Voy a crearme acá un nuevo script vamos a ponerle el START que por defecto ese es el nombre que se le da pero pueden ponerle como ustedes quieran y vamos a pegar este sea prácticamente el nombre del paquete Web Server espacio y pongan menos menos Open eso le dice apenas se levante el Web Server ábrelo okey voy a grabar los cambios y tenemos un nuevo comando acá y vamos a escribir MPM Start me van a preguntar Oh Fernando pero yo pensé que iba a ser MPM Ronstadt sí pero lo que pasa es que él está su nombre bueno importante o especial que se puede ejecutar de esta manera sin él.

Eso es básicamente todo.

Presionamos Enter y esperamos un momento en que me lo levantó.

Pero regresemos acá y aquí hace varias cosas sumamente útiles por nosotros va a estar pendiente de los cambios de los archivos que nosotros tendremos definidos en nuestras reglas y los va a compilar y hacer todo el proceso del MPM rompibles por nosotros de manera instantánea.

Esta terminal ustedes no la van a cerrar.

No usen este basurero porque si no bajarían el proceso que teníamos corriendo.

Entonces revisemos nuestra aplicación déjenme cerrar esta muestra las herramientas de desarrollo y ahora aquí tenemos el web Klip server o web developer Server corriendo con la evítalo y neighbors.

Esto significa que cualquier cambio que yo haga en mis archivos van a ser automáticamente compilados o traducidos a mi nuevo Bondone y se va a cargar de manera automática.

Vamos a ver si eso es cierto no cierren esto por favor no vayan a cerrar todavía no si quieren minimizar esto porque les estorba.

Usen esta X y a este proceso se sigue corriendo.

Vamos a ver si eso es cierto.

Abramos.

Qué les parece si abramos los componentes aquí.

Ahora voy a decir hola o les voy a decir qué tal vamos a escribir el nombre.

Hola Fernando cómo estás o qué.

Cualquier cosa voy a grabar los cambios.

Noten que aquí sucedió algo con piloteó justo cuando yo grabé regreso acá y ya se refrescó de manera automática.

Genial.

Vamos a ver si es cierto voy a borrar esto.

Borro grabo los cambios se volvió a compilar y aquí ya se hizo el cambio nuevamente super.

Eso también se va a aplicar al índex.

Voy a poner aquí Wolfpack server o web pack básico y básico grabo los cambios se dispara la acción regresa un navegador web y aquí lo tenemos sin el título en el html genial.

Entonces básicamente eso es todo lo que quería hacer en esta clase.

Cierto que hay más cosas que podríamos hacer con la configuración del Wolfpack server pero esto es más que todo lo que yo voy a necesitar para poder estar trabajando rápidamente.

Entonces ahora sólo me voy a enfocar en crear mis archivos y automáticamente el web me va a mostrar el producto final corriendo en el local Ouest que es otra cosa que les quiero mencionar.

Si ustedes tuvieron algún error porque dice que el puerto 80 80 note que después de estos dos puntos viene un puerto es posible que su máquina tenga ocupado el puerto 80 80 porque están corriendo un Apache o algún otro servidor y tengan ocupado este puerto pueden cambiarle el puerto muy fácilmente para que use otro en caso de que esté bloqueado el 80 80 que es uno por defecto podemos ponerle menos menos Port igual y pongámosle el 80 81 o el puerto que ustedes tengan libre o no que ustedes quieran el 3000 4200 eso los usan otras aplicaciones por ejemplo.

Bueno voy a grabar los cambios.

Entonces aquí tendría que bajar el servicio para eso a presionar control.

Sé que puedo seguir escribiendo y nuevamente MPM es Stadt.

Esto lo abre y noten que ahora que arriba está corriendo en el puerto 80 81 las posibilidades hay de que también el 80 81 ustedes lo tengan ocupado es muy raro pero bueno no creo que en el basurero también terminan el proceso de la terminal por consecuencia y si ustedes ven la consola van a tener errores acá porque el navegador web tiene instalado una comunicación por sockets que está pendiente de los cambios que sucedan o los mensajes que les diga el server para ver si navegador web que se recarga automáticamente por eso son estos errores cuando ya bajé el servicio en este momento yo soy simplemente lo voy a dejar en el puerto 80 80 pero voy a dejar este comando acá para que ustedes lo tengan como referencia.

Nuevamente les repito y esto va a ser de las pocas veces que les vuelvo a decir voy a levantar el proceso de mi servidor de desarrollo usando el MPM Stack pero básicamente lo que le estoy diciendo es que ejecute esta línea de código que sería lo mismo que ustedes llegaran aquí es que Irán Wolfpack de server y todas las cosas pero para eso están esos scripts MPM Start.

Asegúrese de que su servidor esté corriendo y que todo esté funcionando correctamente y eso sería todo por este video.

Espero que les esté gustando esta sección es bastante educativa y básicamente así se hacen aplicaciones web modernas.

OK pero eso lo dejamos así los veo en la próxima clase.

## 89 Importando estilos de forma dinámica :clock3: 09:13

Hasta el momento hemos visto un par de cosas bien interesantes.

El Wolfpack que es que me permite comprimir mi archivo.

Ahora es posible que ustedes lo vean diferente porque voy a enseñarles porque por defecto cuando nosotros tenemos la opción de Development K y hacemos el Vilchis RPM round Bildt voy a presionar enter.

Volvamos a abrir el main para notar que el archivo ya está como comentarios y me dice que está haciendo en cada uno de los pasos y eso está bien pero cuando nosotros trabajemos en producción production Production Naveros cambios vuelvo a ser el Bildt.

Ustedes van a notar que su main ahora está minimizado y son Tretiak quinqui todo lo que ocupábamos etcétera etcétera.

Yo les voy a enseñar cuando terminemos o estemos al final de la sección les voy a enseñar exactamente un par de cosas que vamos a hacer producción pero por lo menos dejemoslo el modo de developer y vamos a empezar a trabajar acá.

Como ustedes vieron en el título de la clase nosotros vamos a tener que trabajar con estilos.

Yo les voy a enseñar dos formas las dos más comunes que hay para trabajar con estilos uno es cargar estilos de manera dinámica y la segunda es tener unos estilos globales.

Voy a hacer clic derecho en el sours voy a quedar con una carpeta llamada CSS en la cual voy a quedarme otro archivo pero déjeme ver que le puse componentes.

Entonces voy a crear un nuevo archivo llamado componentes apuntó J.S.

El CCC el noveno es importante pero de esta manera yo voy a notificar de que este es el estilo de este componente.

Eso es todo lo que quiero hacer pero pude poner pueden poner el nombre que ustedes quieran puede poner componentes menos uno o simplemente components o como ustedes quieran pero lo Bejar componentes para identificar que este es el archivo de CSS de éste y esa es una de las ventajas que tiene web no está por defecto pero yo puedo cargarse CCS dependiendo del componente que quiero o que estoy requiriendo en ese momento.

Aquí voy a hacer un CSS bastante básico voy a poner que voy a tener un H1 para apuntar a los geles tipo 1 voy a poner el color color voy a ponerlo Red por momentos para que quede bastante claro voy a grabar los cambios.

Obviamente este CSS no lo tengo importado en ningún lugar y les voy a pedir que ejecutemos el comando de MPM Start.

Esto debería lanzar su aplicación modo desarrollo.

Poner loca eso fue lo que hicimos en la clase pasada y aquí lo tenemos pero obviamente el color no está siendo aplicado con mucha razón porque si miramos aquí los elementos voy a ocultar esta barra que me estorba mucho si miramos aquí aquel que no estás el CSS que tenemos en nuestro Main y por eso se ve esto de alguna manera nosotros.

Voy a cerrarlo con esta X no con el basurero porque quiero mantener el servidor abierto.

Voy a tocar esta X de alguna manera yo tengo que decirle al web Pact que por favor mueve este archivo de CSS y colócalo en el fondo de mi aplicación.

En este caso como les dije lo voy a hacer de dos maneras voy a ser el primero que es que importe este CSS cuando estamos requiriendo este archivo de componentes y para eso les voy a pedir que abramos la terminal si quieren que esté más o ténganlo con control sea porque tenemos que hacer un par de instalaciones entonces quedémonos acá y vamos a hacer la siguiente instalación MPM instó menosde para que lo haga en las dependencias de desarrollo o menos menos menos.

Como ustedes quieran ponerlo voy a poner una menosde y hay que hacer dos instalaciones ocupamos uno llamado hicieses menos Louder que es el que nos va a permitir leer el archivo y a su vez inyectarlo y minimizarlo para colocarlo en nuestro blondo espacio y también vamos a colocar él está menos Louder que entre los dos hacen ese trabajo ok lo dejamos así presionamos ENTER.

Dejemos que esto haga la instalación no debía tardar mucho porque los paquetes son algo pequeños perfectos que ya lo instalo y ustedes lo van a poder observar casquista como dependencias de desarrollo si es Louder y el estilode perfecto.

Una vez hecha esa instalación voy a cerrar acá.

Regresemos al componentes y en el momento en que yo importe esa función o necesito trabajar con este archivo o el momento que se haga esa importación voy a poner aquí por espacio y voy a ocupar mi archivo de CSS que usualmente algunos frameworks ustedes lo van a ver que este archivo de J.S. Y el CSS está en el mismo lugar entonces sólo sería poner punto flash pero en mi caso tengo mi CSS en otro directorio entonces tendría que moverme una carpeta atrás dentro de CSS y luego apuntar a componentes .60.

Entonces vamos a hacer eso punto.com las CSS las y vamos a buscar componentes punto CSS fíjense bien cómo lo escriben porque si no puede llevar unos errores raros de que no encuentre este archivo pero asegúrense viendo los nombres o con hacer esto le estoy diciendo a mi archivo de componentes que va a requerir importar este archivo de Senses y UEP va a ser algo bien interesante con esto ya lo van a ver pero pero lamentablemente no es así nada más de importar esos paquetes y ocupamos configurarlos entonces vamos a configurar eso abriendo el web pa config y vamos a implementar un par de reglas entonces acá voy personalmente a abrir y cerrar llaves y poner una coma.

Voy a hacer la configuración respectiva a los archivos de CSS entonces el 3 va a ser un doces las voy a hacer.

Les voy a escapar el punto y necesito que sea puntos ss. todos estos archivos.

Entonces vas a usar exactamente como lo que tenemos aquí abajo y necesito usar esos dos paquetes que es el estilo menos Louder Koma y también el CSS louder.

Esto es básicamente todo voy a grabar los cambios en el wapa confit punto J.V creo que eso es todo lo que es lo que ocuparía hoy y vamos a ver esto antes de que lo prueben en producción.

Voy a pedirles que borren la carpeta disto y vamos a ejecutar el comando MPM Rong Bildt.

Ya le voy a explicar por qué lo estoy haciendo de esta manera y no estoy levantando el servidor.

Ya lo vamos a ver pero MPM Rowntree.

Personalmente esto hace el video de producción ya crea la carpeta de distribución.

Todavía hay optimizaciones que tenemos que hacer acá no se preocupe pero ustedes van a notar que mi índex no hay nada del CSS y eso es normal no se preocupe sólo tenemos mi mi mail apuntó Jota.

Si abrimos el mail aquí tenemos mucha información pero es un poquito difícil de encontrar.

Qué cosa en particular se acuerdan que nosotros en el CSS le pusimos color.

Entonces en el mail va a presionar controlé o como NF y busquen Read ok van a ver que aquí los lleva a un punto en el archivo de JavaScript en el cual está haciendo esa importación del color.

En pocas palabras está requiriendo el archivo como si fuera cualquier otra librería de JavaScript en el momento que yo necesite trabajar con este componente.

Va a cargar ese CSS y eso es genial.

No se preocupen por estos errores porque bajé el servidor.

Entonces voy a pedirles que abramos acá web inicial dice Hagan doble clic en el Index y en otra pantalla iban a notar que las letras están rojas excelentes así lo aplicó de manera dinámica en el momento que requería ese archivo.

Voy a cerrar esto y ahora vamos a hacer algo más interesantes creamos MPM Stark para que levante mi servidor de desarrollo otra vez en el otro monitor disculpen por esto y aquí ya lo tengo que está corriendo el y toda la cosa.

Ahora les voy a pedir que cerremos con una X.

No terminemos este proceso porque si cerramos este proceso termina mi web termina la web Pandev Server y vamos a cambiar ese archivo de CSS cerrar todo y cambiamos esto de manera dinámica pongámoslo como Grin ok otro color graven los cambios van a regresar acá y automáticamente ya carga y aplica ese CSS es bastante útil.

Puedes poner otro color y logo por ejemplo grabemos los cambios y ha instado.

Eso me lastima los ojos pero bueno está el color amarillo dejémoslo en rojo por los momentos grabamos los cambios y regresamos acá y ahí está.

Entonces ustedes pueden crear sus propios archivos de CSS y requerirles cuando ustedes necesiten trabajar con ciertos componentes.

Eso es sumamente útil pero hay un pequeño inconveniente que posiblemente ustedes me van a preguntar o Fernando Esto está genial pero qué pasaría si yo necesito tener unos unos estilos globales en mi aplicación y que esos estilos globales también sea un archivo independiente acá que estén asociados a mi índex que estén acá porque ese estilo va a ser global a mi aplicación y puede ser que ustedes necesiten manejar ese archivo en el caché y los demás archivos de CSS de manera independiente.

Entonces antes de que ustedes me pregunten eso por favor si esa es la pregunta que me quieren hacer no se preocupen es lo que vamos a ver en el siguiente video.

Pero eso es algo que se puede hacer y esto es bastante común que ustedes lo vean que cuando ustedes requieran este archivo de CSS quieran trabajar con este componente.

Entonces lo importe.

Bueno esto es todo lo que quería hacer por esta clase.

Les voy a pedir que cerremos todo excepto el server ténganlo ahí o si quieren no cierran porque vamos a hacer instalaciones en el otro lugar entonces lo dejamos así y los veo en el próximo video.

## 90 Creando un archivo de estilos de forma global en la aplicación :clock3: 10:43

Ok comencemos con esto lo que quiero hacer ahora es crear unos archivos o un archivo CSS global a mi aplicación y que ese archivo global no esté importado en mi archivo de Index y también en mi carpeta de distribución.

Este archivo independiente de Ce6 es bastante común verlo vamos a hacerlo en la carpeta Source directamente voy a crearme un nuevo archivo llamado estaes puntos CSS el nombre que ustedes le pongan no es importante pero ese es el nombre que le quiero dar.

Personalmente no tengo este está lo tengo en el Sors.

De esta manera muchos frameworks lo utilizan para indicar que este es el archivo global de la aplicación.

Pero no importa mucho.

Ustedes van a especificar el paso y todas las cosas aquí sé que el HTML y el bodhi tengan un Bagan Colo Colo que mono de un gris que voy a grabar los campos quiero que notemos que si levantamos el MPM start si quieren presionar enter ya lo abre.

Voy a recargar.

Y bueno el color no se mira muy bien voy a ponerlo en Herring por momentos grabo los cambios y van a ver qué nos está explicando por qué creen que nos está aplicando porque así como tenemos nuestra configuración voy a cerrarlos con esta X así como tenemos nuestra configuración.

Nosotros vamos a ocupar importar este archivo ésta para poder trabajar con él para decirle OK tienes que cargar los estilos.

Entonces para eso voy a hacer clic en el índex aquí aquí en el Index y voy a importar import puntuó flash porque estoy en este mismo directorio o sea el Index y el estilo está en el mismo directorio web anarquista Helesponto Ce6 cuanto más grabo loscambios regreso navegador web y ya se aplicó el verde.

Ok bien pero también quiero que me voten que está todo manejándolo en el mismo archivo.

Dejémoslo aquí como gris que los cambios van a ver que se aplica el gris y vamos bien pero pero ahora sí vamos con lo interesante.

Voy a cancelar esto con Control C y hago el MPM Rong Bildt y para nuestra mala suerte no creó el archivo de esta semana.

Independiente sigue estando en algún lugar acá y ven y sigue estando como una dependencia.

Cuando yo necesite importar lo que es el mail entonces yo no quiero que esto lo haga de esta manera quiero que esté como su archivo independiente y que también lo coloque en el index.

Entonces para hacer eso voy a ocupar revisaron las instalaciones esas instalaciones son las siguientes MPM instó.

Simplemente ahí menosde y este sí con mucho cuidado porque si es un nombre algo feo que es mini menos CSS menos estructura menos plugin.

Ese es el nombre del paquete que necesitamos mini CSS Strogg plugin o como está escrito si ustedes lo escribieran mal que les va a tirar algún error.

Presionamos enteráramos que esperamos que toda la instalación agrietados mucho.

Perfecto cerremos.

Y como ustedes imaginarán hay que hacer la configuración y Wolfpack recuerda que cuando minen que tiene la palabra plugin quiere decir que hay que hacer algo muy parecido a esta configuración de aquí abajo.

Yo sé que le dije que ya no íbamos a ser más pero sí voy a poner una masái y ahí ya estamos porque yo tengo la tengo que hacer la importación constante.

Le voy a poner mini CSS Choc plugin el nombre que como ustedes quieran ponerlo en el recuadro paréntesis mini CSS por lo menos ahí sí me ayuda la autocompletar.

Ok entonces qué es lo que quiero hacer.

Voy a ocupar poner otra regla adicional porque aunque es otro chico de CSS voy a tener que manejarlo de manera diferente.

Voy a colocarlo aquí abajo.

Y cerró llaves Koma y eso es muy parecido a esto si quieren lo copian y lo pegan acá siempre lo vamos a aplicar con los CS6 pero sólo me interesa un hecho en particular sólo me interesa que evalué contra un archivo.

Voy a quitar ese flash estoy Stairs contra aplicã o contra las Oakes las que ustedes le digan CSS aquí no va a usar el stick Louder porque eso sería el que lo lo haga lo haga parte del fondo de mi aplicación.

Aquí voy a poner.

Voy a poner el plugin in punto Louder que de esta manera quiero que apliques esto únicamente cuando encuentres este archivo pero ustedes van a notar que este es un H2S.

Y entonces esta condición nunca se haría cuando se haga la evaluación porque siempre se haría ésta en lugar de esta porque eso es para todos los Ce6.

Entonces este test ustedes lo van a copiar justo abajo del test de arriba de que tenemos acá de las de los SS.

Vamos a excluir excluir dos puntos y van a pegar ese mismo.

Esta misma expresión regula para decirle que haga esta evaluación pero excluya este archivo en particular o los que Wachowsky coincidan con esta expresión o que pueda grabar los cambios.

Y todavía nos falta hacer una pequeña configuración porque ya tenemos esto pero ahora ocupo decirle cómo va a trabajar este mini extrapoló y necesito decirle como va a trabajar entonces aquí Niu espacio.

Hoy cierro paréntesis y ahora sí aquí adentro ponemos ves gente.

Lo interesante es que ustedes le van a poder poner el nombre que quieran y otras cosas.

Entonces Phinney dos puntos y viene el nombre que ustedes quieran darle al archivo.

Vamos a dejarlo como ni y punto.

Ese es el nombre de archivo que quiero manejar.

Aquí también voy a colocar otra propiedad que recomiendan que ignoré ordered y voy a poner.

Voy a poner fotos eso es para que no nos Silvanos warnings.

Voy a grabar los cambios vamos a ver si esto es todo.

Creo que sí y vamos a ver si esto funciona OK entonces MPM Ron vio gente y vamos a ver qué sucede acá.

Perfecto me creó gaucho de CSS.

Lo voy a abrir y sólo tiene lo que yo puse en mi archivo de estilos global lo que puse acá.

Ok excelente y si ustedes se preguntan ustedes pueden hacer otras cosas nosotros más adelante estamos trabajando con la parte de producción.

Quiero ponerle un nombre especial a este archivo para prevenir el caché algo como content.

Voy a grabar los cambios voy a ejecutar nuevamente el RPM rompió.

Eso solo es un pequeño adelanto y ustedes van a notar que ahora me creó un archivo que tiene unos números raros acá este me va a ayudar a mí a prevenir que el navegador web mantenga estos archivos en el caché y sólo los va a cambiar cuando sean necesarios.

Y si miramos nuestro Index puntuó HTML va a notar que como es un estilo está en el jet y aquí tenemos el mismo nombre.

Así que nosotros no tenemos que hacer absolutamente nada.

Por ese lado pero obviamente como estamos en desarrollo nosotros no vamos a usar este content.

Por ahora voy a grabar los cambios acá voy a borrar el disco y ejecutar nuevamente el N.P me rompí el sólo para asegurarme de que todo esté bien perfecto y probemos si eso también funciona.

Si yo ejecuto el servidor de desarrollo eso es algo importante MPM Start que ya lo abrió a descargar acá mostrar las herramientas de desarrollo Cambiemos el color del fondo recuerden que el color del fondo es el que tenemos en el está de manera global.

Pongámoslo algo como Black algún otro como cualquier otro color grabó los cambios y ahí lo tenemos.

Entonces de esta manera es sumamente útil que ustedes tengan separado lo que son sus estilos globales de la aplicación o un archivo independiente y también los humanos sus componentes también los pueden importar.

Con estas reglas que acabamos de implementar acá lo único que me hace falta.

Sé que me van a preguntar es ok eso está muy bien pero aquí el CSS debería de estar minimizado y yo lo paso a producción tienen muchos Mazzaro mucha razón me llama probarlo Production y grabar los cambios.

Voy a bajar esto MPM Ron Bill esto ejecuta el Bills y no minimizo nada.

Entonces como ustedes se imaginarán tenemos que hacer algo para minimizar este código y para eso vamos a ocupar instalar otra cosa pero esto es sólo si ustedes quieren.

No es que sea obligatorio y este paquete tiene un nombre aún más extraño entonces escribamos MPM instó.

Menos de una experiencia de desarrollo y se llama optimas menos CSS menos assets menos Wolfpack menos yo salto blogging es todo esto.

Optimas S.S. hace Duet pa blogging vamos a presionar enter esperemos que haga la instalación podría tardar mucho.

No es tan grande que ya lo hizo.

Lo tenemos que si quieren lo vamos a volver a escribir entonces cerremos acá tenemos esto e importemos el plugin constante.

Vamos a poner Optima es el doble que ustedes quieran la verdad pero se recomienda que les pongan el mismo nombre optimas CSS assets plugin y vamos a hacer esto mismo vamos a hacer required parentesis y óptima es por lo menos aquí si lo encuentras rápido.

Los seleccionamos y vamos a utilizar este plugin pero este funciona de una manera diferente.

Lo voy a poner acá dentro de Optimization que es una nueva propiedad acá.

Pongamos una coma y dentro de dos optimizaciones vamos a colocar el mini Moise.

De esta manera yo sé que todo este código similar es raro pero cuando Uds. buscan este paquete en la documentación les dice cómo utilizarlo pero de esta manera es como lo recomiendan que lo utilicemos y hay que crearse una nueva instancia de esto parentesis y ustedes pueden poner otras configuraciones aquí adentro pero la configuración por defecto cuando está en producción.

Ojo con esta producción eso lo va a hacer por nosotros.

Entonces crearemos los cambios vamos a ejecutar nuevamente el RPM rompido perfecto dejemos que esto lo haga.

Miremos el punto CCC y está minimizado.

Eso es interesante porque igual si tuviéramos comentarios acá éste es el estilo del Main.

Cualquier cosa voy a grabar los cambios voy a ejecutar nuevamente el MPM ROM BIOS lo ejecuta y no tenemos el comentario acá ustedes pueden probarlo a ver si eso es cierto voy a cerrar acá o cerrar los estilos y aquí ahora lo voy a poner en modo de desarrollo development.

Voy a grabar los cambios nuevamente flecha direccional arriba para hacer el bit nuevamente lo ejecuta.

Miremos el punto CCC y aquí tenemos nuestro comentario ok lo voy a dejar hasta este punto.

Ya hemos hecho la configuración de CSS y los veo en el próximo video.


## 91 Nota de actualización :clock3: 00:17

Nota:

En la próxima clase trabajaremos con el Webpack CopyPlugin, el cual nos sirve para copiar y mover los assets, pero la sintaxis cambió un poco:

En el video verán:

```js
new CopyPlugin([
    { from: 'src/assets', to: 'assets/' },
]),
Y ahora se recomienda:

new CopyPlugin({
    patterns: [
    { from: 'src/assets', to: 'assets/' },
],
```

Como ven, se agregó un nivel adicional de patterns, y ahí se añade lo mismo que veremos en la próxima clase.

Gracias a Klaus por señalarlo

https://www.udemy.com/course/javascript-fernando-herrera/learn/#questions/12497346/

## 92 Manejo de imágenes :clock3: 10:13

Ok ya hemos trabajado con HTML y ya hemos trabajado con J.V y econ con CSS.

Ahora nos falta trabajar con imágenes.

Les voy a pedir que creamos acá en el directorio de sours su nuevo folder llamado aceptais que aquí vamos a colocar imágenes y otras cosas pero realmente el directorio no importa mucho porque ustedes saben cómo se va a terminar evaluando todo esto.

Pero bueno de esos para que nuestro directorio tenga un cierto orden estándar y aquí les voy a pedir que vayamos a Google.

Bueno aquí tenemos esos errores no se preocupen por eso es porque el servidor de desarrollo vayan a Google búsquense cualquier imagen que ustedes quieran que no sea tan grande.

Creo que este logo me va a servir si dice este logo.

No busquemos una que sea un J un jpg o cualquier cualquier tipo de imagen que sea un hillbilly.

Vamos a trabajar con los SVG entonces click derecho vamos a guardarlo como vamos a colocarlo en el escritorio ya que en el proyecto sours assets y coloquemos le podemos dejarlo así cualquier nombre que ustedes quieran es una imagen PNG el nombre que ustedes quieran igual lo vamos a trabajar de otra forma vamos a guardar un nombre que sea sencillo de manejar por ustedes que estamos acá y aquí tenemos la imagen que tiene Wolfpack Esprit vamos a cambiarlo para que no tenga doble PNG nada más de esta manera y aquí la podemos ver la imagen no es la más bonita de todas pero está bien por ahora cómo trabajaríamos con esa imagen en el html.

Digamos que ocupamos importarla colocar acá colocar una imagen que va a tener el cierre de puntos las assets y hasta la imagen y aquí hepatólogo web CPAC logo perfecto.

Voy a grabar los cambios y echamos a andar el servidor de desarrollo MPM Start.

Yo no enter el servidor cerrar esto y no estamos viendo no estamos viendo nada.

Cambiamos el color de fondo porque es un color negro no se preocupen por ese error vamos a colocarlo de un color Gray grabar los cambios regresar acá de cargar y no tuve que recargar manualmente porque como tenemos un error y aquí lo tenemos específicamente y me dice que está dando un error HTML Web plugin.

Básicamente lo que está dando problemas es que no sabe qué hacer con este recurso de esta imagen entonces yo tengo que especificar la web qué hacer con estas imágenes.

Tal vez será un dolor de cabeza pero esa configuración es muy difícil de hacer.

Les voy a pedir que abramos el web y aquí hay que hacer una regla pero para eso hay que instalar algo que es bueno imagino que lo miraban venir y MPM MPM instó menosde con mayúsculas para que sea una dependencia desarrollo y vamos a importar el Foy Louder presionan.

Dejen que esto haga la instalación no debía tardar mucho.

Perfecto dos segundos cierro y hay que hacer una expresión regular que evalúe cualquier imagen o cualquier Accept que yo quiero simplemente mover.

Para eso lo voy a colocar vamos a colocarlo abajo del HTML abajo de ésta.

Voy a poner una coma enter abren y cierran llaves.

Vamos a hacer lo mismo test dos puntos y necesito evaluar cualquier imagen para evaluar cualquier imagen voy a ponerlo de esta manera voy a excluir el hacer que incluye el punto de estos para escapar el punto y los paréntesis me van a poder especificar.

Varios elementos al mismo tiempo como por ejemplo si son png o Cedegé un viaje o un jpg o gif y terminamos con el símbolo de dólar Ok voy a poner una coma que al final y lo que quiero que haga y use dos puntos encierran llaves y lo que quiero que haga voy a abrir las llaves.

Voy a especificar este objeto yo sé que es un dolor de cabeza pero recuerden que solo se hace una o dos veces en la vida y lo demás simplemente ustedes copia y pegan todo.

Esta configuración del web vas a colocar aquí Louder dos puntos espacio y va a cargar el menos Louder Koma y también para que no tenga unos ciertos problemas a la hora de importar unos módulos.

Voy a poner aquí options los puntos llaves y es moduló noten que la M mayúscula Phobos ahora antes de que más de uno de ustedes diga uy qué pasó que se me movió la pantalla.

Fernando hizo algo quiero que no te lo siguiente.

Esto es una actualización que estoy haciendo el curso para que siga siendo válido con las últimas versiones que ustedes podrán observar aquí está el código que ustedes deberían de tener del HTML Louder porque eso fue lo que también hice una nota actualización al respecto.

Ahora si vemos esta parte de Louder desde la versión 6 les voy a pedir que abran espacios apuntó Jayson.

Revisen aquí su versión.

Si ustedes tienen la versión 6 o superior lo que acaban de ver no va a funcionar o va a funcionar exactamente como les voy a mostrar.

Si ustedes tienen las 5 ya debería estar funcionando su aplicación.

Cuando hace un LPM start voy hacer un RPM start se levanta cerrar esto mostrarles acá y tenemos que la imagen no la cargó y así funcionaba anteriormente antes de las seis.

Esto funciona sin ningún inconveniente pero después de las seis ya no funciona.

No se preocupen si habían más paquetes ahí porque estoy trabajando con el proyecto final pero más o menos así dejaremos de tenerlo ahora.

Si nosotros hacemos esta configuración qué es lo que nos permite hacer Wolfpack ahora o por lo menos lo que es nuestro FFII Louder.

Les voy a pedir que vayamos al archivo js bueno a cualquier archivo JavaScript y si nosotros hacemos una importación por ejemplo imagen from Frog y hagamos el punto islas hacérselas y busquemos el web pack o la imagen que ustedes colocaron graban los cambios y si vuelven intentan levantar nuevamente la aplicación.

Esto todavía no les va a funcionar.

Bueno si funciona pero no como nosotros estamos esperando.

Voy a cancelar con controlé esto que el control sea perfecto pero qué hizo que hace eso cuando ustedes hacen la importación.

Entonces se está trabajando con el fair Louder y lo estamos viendo podemos aplicar toda la configuración del Feilong que se encuentra la documentación pero déjenme mostrarles acá voy a escribir Wolfpack gente entonces va a tomar la configuración por defecto de mi web pack CREAL vist y aquí tenemos la imagen.

Ok entonces al requerir la imagen entonces ahí es donde la vamos a ver pero yo no quiero hacer esto y usualmente todos mis assets que yo tengo acá todos mis assets van a ser recursos estáticos es decir quiero que estén dentro del disco la misma ubicación con el mismo directorio con todos los directorios exactamente igual.

Son recursos que yo no voy a cambiar.

Son imágenes estáticas.

Ok entonces para eso vamos a ocupar otro tipo de paquete ahora.

Anteriormente repito funcionaba bien con lo que es el Feilong de ahora nosotros ocupamos otro para ser bueno copiar y pegar todo eso en el directorio de distribución.

Vamos lo siguiente hagamos la instalación r.p.m instó.

O simplemente y espacio Kopi menos Wolfpack web pack menos plugin menos menos soy menosde.

Ok copy Wolfpack plugin.

Este paquete nos va a permitir a nosotros realizar ese tipo de movimiento muy fácilmente con una configuración muy sencilla que ya tenemos la instalación cierro voy a grabar los cambios en el Indec no hice nada si lo dejamos de tener cerramos y ahora podemos utilizar ese plugin como otros que teníamos acá.

Entonces voy a poner acá constante se va a llamar CoPy plugin y esto va a ser igual a recaudar parentesis kopi plugin copy web Wolfpack plugin.

Ok vamos a copiar esto y como cualquier otro proving de web lo vamos a colocar aquí al final voy a pegarlo acá Niu espacio copy plugin parentesis y recibe una configuración en forma de arreglo porque ustedes pueden copiar todo lo que quieran y en base a las reglas que estamos especificando acá pueden hize la documentación del copy plugin para que vean más información al respecto pero bien sencillo de utilizar.

Noten que es un arreglo y dentro viene todas las reglas que yo quiero copiar.

En este caso empezamos con el from quiere decir de la carpeta a la cual yo quiero empezar a copiar quiero que sea del Source Slash assets.

Ok Quiero que empiece a copiar todo lo que se encuentra dentro de esta carpeta y el destino por eso lo ponemos con él tú dos puntos espacio y lo quiero que lo creen.

Haces eso no a copiar en la carpeta de distribución.

Voy a grabar los cambios borren la carpeta vist por favor para que lo miremos entonces toquemos nuevamente.

MPM Start para ver si funciona.

Enter y ahí tenemos la imagen ok.

Y ahí está todo funcionando normalmente.

Estos guantes que tengo yo es porque tengo un par de herramientas ahí extensiones de Crom pero eso no tiene nada que ver con lo que estamos viendo en pantalla.

Ok entonces voy a cancelar esto y ahora puedo hacer nada más el comando de Wolfpack para que no en paquete a presionar Enter y aquí deberíamos de ver ahora la carpeta dice con sus respectivos assets con la respectiva imagen.

Ok eso era todas las notas de actualización.

Quiero hacer un pequeño paréntesis en el código fuente de la sección.

Ustedes van a encontrar la configuración completa con este copy plugin y con el HTC Louder y cualquier otra actualización.

Pero los próximos videos como siguen siendo los mismos todo y eso funciona sin ningún cambio.

Ustedes no van a ver este copy plugin.

No quiere decir que lo borren.

Manténgalo porque eso les va a funcionar sino que los otros videos.

No hace falta la actualización o sea no hace falta hacerlos para que ustedes puedan observar esto.

Eso ustedes lo dejan.

No que ya está funcionando.

Lo dejamos así y los veo en el siguiente video y recuerden esto es parte del compromiso que tengo de darles a ustedes y mantener el curso actualizado hasta que me sea posible.

Bueno eso era todo.

Espero que resuelva la mayoría de los problemas que tengo.

Recuerden esto es una actualización que hace más o menos ocho días fue que se liberó el último cambio y 8:10 ustedes ya tienen el curso actualizado.

Espero que no tenga el esfuerzo que se hace.

Y bueno eso será todo todos nos vemos en la próxima clase.

## 93 Webpack - Production Mode :clock3: 08:51

Estamos llegando a un punto donde ya ocupamos diferenciar en nuestro cascarón para hacer desarrollos de aplicaciones de JavaScript utilizando Wolfpack donde ocupamos diferenciar cuando estamos en desarrollo y hacer una diferencia en producción.

Nosotros brevemente hemos visto que si aquí paso a la producción voy a grabar los cambios voy a ejecutar nuevamente el programa Aquí MPM round Pilot y presionar ENTER.

Esto genera la versión para producción.

Si nosotros vemos ahora el diseño aquí me instalé minimizado y posiblemente aquí tengamos un error ahora de que no aparece minimizado correctamente mi código aparece minimizado cierto aspecto no está minimizado en lo absoluto.

Todas las funciones están abiertas y constantes.

Todavía estamos usando esto como ustedes pueden ver aquí hay varios errores ya vamos a resolver la minimis minimización del archivo de JavaScript pero por lo menos me interesa que eso lo tengamos minimizado o sea está más o menos preparado para producción más o menos pero todavía hay muchas cosas que no lo están.

Entonces todavía tenemos trabajo que hacer y obviamente yo no quiero estar cambiando aquí de modo de desarrollo modo developer desarrollo modo developer.

Entonces voy a quedarme un archivo de configuración especial cuando yo no necesito trabajar para desarrollo y para producción hay personas que lo que hacen es crear un archivo de configuración global que es bueno con las características que son comunes para ambos ambientes como por ejemplo yo quiero ejecutar todas estas reglas tanto para desarrollos para producción pero eso agregó cierta complejidad.

Ustedes si quieren lo pueden investigar e implementarlo pero yo prefiero quedarme un nuevo archivo llamado Wolfpack CPAC apuntó Prot punto J.V en el cual tengamos sólo la configuración de producción les voy a pedir que copien todo el contenido del Confi y lo vamos a pasar al CPAC de producción.

Esto no es obligatorio porque ustedes pueden estar cambiándolo pero yo prefiero tener un archivo independiente para producción con todas sus reglas.

Ok voy a cerrar el web config.

Obviamente cuando estoy trabajando en el modo de producción lo primero que tengo que hacer es poner Production y voy a comenzar a modificar esto un poco ok.

Lo primero que quiero hacer acá es apuntar a output dos puntos agonizaban y a veces quiero crearme el archivo de manera semi manual Filey peinen dos puntos ustedes le pueden poner cualquier nombre que quieran por defecto le estamos poniendo mail apuntó J.V.

Ese es el nombre que está poniendo Wolfpack por lo prometo lo voy a poner aquí punto a veces para poner de un cierto tipo de código que al final voy a grabar los cambios.

Voy a ejecutar nuevamente el comando de MPM Rong View presionar Enter y ustedes van a notar que no pasó absolutamente nada.

Todo está igual.

Por qué.

Porque por defecto cuando ustedes no especifican nada aquí en el Wolfpack está buscando este archivo de web CPAC.

Parece trabalenguas.

Punto Com punto J.V.

Ese es el archivo de configuración por defecto.

Pero si yo quiero que utilice esto cuando yo hago el Bill entonces le tengo que mandar aquí una Mander una bandera con menos menos Koffi que espacio web PAC Punto Prot punto J es lo que voy a grabar los cambios si quieren borrarse esta carpeta para que lo miremos correctamente ejecuto nuevamente el comando de MPM Room Viel que sería este acá y presionó enter ok perfecto y lo hace voy a abrir el test y aquí tengo mi punto abecé.

Y ahí está.

No se preocupen porque no esté minimizado eso ya lo vamos a resolver porque voy a cerrar esto.

Entonces de esa manera puedo correr ese archivo y ejecutar estas reglas de manera independiente.

Pero qué pasa si yo no quiero perder mis configuraciones por defecto porque puede ser que yo también lo quiera sé mi producción o como para pasar a un ambiente de preproducción.

Eso significaría que yo necesito mis archivos pero sin minimizar y quiero ver qué pasa entonces perfectamente puedo crearme otros que le puedo poner el nombre que yo quiera.

Puede ser o el comando que quiera pero le voy a poner videos 2.El usted tiene más sentido y aquí voy a ponerle.

Puedo quitar esto si quiero para ejecutarlo por defecto.

Pero si quieren podemos ponerle aquí config.

Ok.

CPAP punto confit punto.

JS voy a grabar los cambios y ahora voy a ejecutar este comando.

Para eso sería NP rond Viel 2.0.

Presionar Enter.

Ustedes van a notar acá que soy un poco aquí está usando el pack punto configuración por defecto ya van a notar que aquí creó el Main.

Ok aquí está mi main.

Perfecto voy a cerrar esto y ya tengo estas dos reglas implementadas ahí cierro.

Sigamos trabajando en la parte de producción porque todavía hay cosas que yo quiero hacer.

Por ejemplo yo no quiero estar modificando este seminario este código cada vez que yo hago mil de producción.

El objetivo de lo que voy a hacer es que si yo le pongo un nombre un hombre independiente a este archivo entonces cada vez que yo despliegue va a tener un código diferente acá para prevenir que los navegadores web de mis clientes almacenen en el caché este archivo por consecuencia imagínense que ustedes hicieran una actualización fuerte a su aplicación de JavaScript pero como la aplicación está almacenada en el caché del cliente el cliente jamás va a saber qué es esa actualización 6o.

Pero si yo le cambio el nombre al archivo entonces por fuerza el navegador web del cliente va a volver a hacer la petición.

Y si no ha cambiado el nombre del archivo entonces significa que ustedes no han hecho ningún cambio.

Para eso los tiene cubiertos con algo bastante sencillo que es el content ATX.

Que de esta manera revisamos bien agravarlos cambios y ahora voy a ejecutar nuevamente el MPM Room View para que lo haga de producción.

Voy a presionar Enter y ustedes van a notar que aquí va a crearse un nuevo archivo Moine que tiene ese jazz extraño.

Ustedes no se tienen que preocupar por eso porque en sus videos ustedes van a ver que aquí está importado por defecto que cierran usualmente cada vez que hacen un video.

Ustedes perfectamente pueden borrar ese directorio y volver a ejecutarlo y ahí ya se los va a crear porque ese es el objetivo de el video ahora nosotros tenemos que hacer lo mismo con el punto CCC y eso se los voy a dejar de tarea intenten hacer esto mismo pero con ese archivo del punto CCC y asegúrense de que también esté en Index importado entonces póngale pasa al video intenten hacer eso no es nada difícil.

Yo sé que lo van a poder lograr y si no yo regreso con ustedes en unos instantes con la solución póngale el video ahora intente hacer eso.

Ok entonces vamos a ver si lo lograron hacer básicamente es volver a ejecutar esta instrucción pero que abajo en el momento donde estamos creando el archivo de seises de hecho lo pusimos en su punto y ponemos el jazz a grabar los cambios a ejecutar nuevamente el MPM rompí el de desarrollo de producción y aquí tenemos ya el CCC con jazz y también está importado acá bastante sencillo no excelente.

Ahora sólo lo que acabamos de hacer eso nos ayuda muchísimo muchísimo en el desarrollo pero tenemos un inconveniente voy a cerrar todo esto si quieren borren dice eso da igual porque ellos saben que cuando quieran trabajar con el disco lo puedo volver a generar.

Voy a hacer el MPM Start y les voy a explicar el problema para comenzarlo en el comenzar a solventarlo en el próximo video.

Si nosotros levantamos el RPM estamos creando nuestra aplicación y nos vamos a sources.

Ustedes van a notar que aquí tenemos una constante nombre igual Fernando esto funciona si el navegador web soporta más que IPv6 o superior o estamos hablando de la versión de Skype del 2015.

Ustedes tienen que saber a qué objetivo van a estar trabajando su aplicación si todos sus usuarios van a trabajar con Google Chrome o versiones actualizadas de Firefox.

No hay ningún inconveniente pueden dejar esto así pero hay muchas posibilidades que cuando ustedes hagan su aplicación tengan que apuntar a versiones muy viejas de navegadores web en los cuales no soportan la constante y cuando el navegador web empiece a ejecutar estas líneas estas líneas y llega a este punto donde dice constante nombre pero yo no sé que hay que hacer con la constante dice el navegador web.

No no puedo seguir el programa y tiro mejor un error.

Entonces esto haría que toda nuestra aplicación ya no funcione porque no va a seguir ejecutando nada más de JavaScript.

Esto es algo que nosotros vamos a configurar en el próximo video en los próximos videos y también voy a resolver el problema del por qué no se está minimizando mi explicación.

Si ustedes se le está minimizando cuando lo hacen el modo de producción perfecto no hay ningún inconveniente pero en mi caso todavía no se está minimizando y tengo los comentarios y otras cosas por lo menos el DCS ese sí está funcionando porque está removiendo los comentarios todo lo demás pero él ya no está funcionando como yo espero pero ya vamos a resolver eso no se preocupe por lo menos dejemos la clase hasta este punto y nos veo en el siguiente video.

## 94 Instalación y configuración de Babel :clock3: 11:58

La mejor manera de explicar es es que ustedes miren este ejemplo que ellos tienen pueden ver en el material junto al enlace que lo lleva directamente a la página de Babel y punto.

Y básicamente lo que nos permite a nosotros es utilizar características de lenguaje scrip 6 7 8 o cualquier otra versión superior que sea compatible con la versión de Nott que ustedes están ejecutando y nos permite traducir lo que sea que ustedes escriban a código de JavaScript compatible con navegadores web viejos entonces por ejemplo aquí está usando una función de flecha y un acumulador.

Bueno yo no sé para qué hago clic porque si hago click ya deja de funcionar el demo pero eso lo hace automáticamente como ustedes pueden observar.

Pasa de este código a el código estándar de JavaScript.

Es sumamente útil poder hacer esto entonces vamos a implementar la parte de Babel en nuestra configuración de Wolfpack que tenemos acá para que cuando nosotros hagamos el video también me traduzca mi código de JavaScript a versiones compatibles de otros navegadores web entonces les voy a pedir que vayamos a qué hacer AP o a la instalación y aquí hay muchas formas de utilizar nuestro utilizar Badén.

Esta es la versión posiblemente usted ve el video hay versiones superiores puede hacer click aquí en donde dice Wolfpack y esta es la parte de la instalación.

Si el sitio web cambia de estilo o alguna forma no se preocupe simplemente que votar estos comandos de instalación.

Entonces les voy a pedir que copiemos estas líneas copiamos la instalación vamos a quien no es un navegador web pero todavía su estudio Cott costumbre y voy a ejecutar esas líneas de MPM instó.

Ustedes ya saben que podríamos hacer simplemente y en lugar de menos menos CTD podemos poner en menos de instalar el back Louder Belcorp y déjeme cortar la barra lateral.

Y si no estoy mal esto debería ser todo.

Entonces presionamos ENTER.

Esta instalación puede demorar un poquito más porque son varios paquetes pero en mi caso ya lo hizo perfecto.

Voy a cerrarlo y voy a hacer la configuración inicial de producción.

Por qué me interesa el deproducción porque obviamente ahí es donde lo voy a ejecutar el bit de producción para que me genere ya la versión lista para para todos los navegadores web pero esta configuración también la podrían implementar en el web de la configuración por defecto por si acaso ustedes lo desean.

Ok entonces vamos a probar.

Voy a agregar una nueva regla y como Babel trabaja en base JavaScript.

Esto sólo va a afectar a los archivos JavaScript.

Entonces por consecuencia Bueno de hecho si ustedes se fijan en la documentación aquí están las reglas.

Toda esta regla la voy a copiar voy a regresar a un navegador web y ellos lo tienen de esta manera pero yo prefiero tenerlo trabajarlo como lo estoy viendo porque es más me es más claro de leer más fácil de demostrar.

Y aquí está haciendo la evaluación para todos los archivos de JavaScript que tengan accesión puntos JS Va a excluir los módulos de Nott porque obviamente no queremos que revisen nada de lo que está acá.

Eso está bien que lo excluya y por último tenemos este Louder pero si no estoy mal esto es la versión anterior de cómo se usaban los lotes pero mejor acostumbrarnos a hacerlo de la misma manera para mantener la sintaxis igual aquí es lo que estábamos importando.

Ese Babel Louder que voy a pegarlo acá los cambios y en teoría esto debería ser todo pero vamos a hacer una pequeña prueba sólo para demostrar que puede ejecutar el MPM FPMR round Bildt.

Esto de usar el archivo de producción hoy ustedes pueden observar por aquí está que usó deproducción hizo la compilación de todo y si miramos el disco BO2 déjeme borrar el disco para no confundirme voy al volverlo a hacer podríamos poner un script que borra el disco también sería conveniente y si yo busco constante van a ver que aquí todavía está ahí está mi constante y eso es lo que yo quiero prevenir.

Yo no quiero trabajar en esta versión de JavaScript quiero que traduzca todo a la versión del ECMAScript por lo menos la versión más script 5 que es la versión prácticamente estándar soportada por todo el mundo.

Entonces todavía vamos a tener que hacer una pequeña configuración adicional.

Bajamos un poco bajamos un poco y esto es la configuración para hacer la configuración de Babel o podemos crear un archivo llamado Babel R.C. y mucha gente me pregunta por qué el nombre apuntó Babel se puede explicar simplemente creemos este archivo.

Punto.

Babel y aquí donde vamos a poner la configuración ahora que se le ponga un punto al inicio usualmente en sistemas operativos basados en Unix como Mac OS X y Linux al anteponer un punto se indica que es un archivo que está oculto o sea no es un archivo que todo el mundo debería de ver y manipular.

Entonces creo que por ahí va el asunto yo puedo estar equivocado pero básicamente esto es el nombre que nos está pidiendo Babel para hacer su configuración ok para hacer ciertas configuraciones podemos hacer clic en este enlace que también se los dejo en el material adjunto y aquí ustedes pueden ver cómo instalar plugins como hacer otras cosas y aquí hay otras.

Otros paquetes que ya vienen como por ejemplo minimizar o pasar de tags es también muy importante pero me interesa el de Mini.

Voy a hacer click acá.

Aquí está la instalación voy a copiar esto también les dejo.

Bueno yo estoy dejando el enlace al material adjunto voy a hacer esta instalación acopio no voy a pegar acá no tengo enemistó va a haber pressen minifalda Zaitsev dejo que esto haga la instalación.

Mientras esto sigue vamos a ver como se usa hay que colocar esto en el archivo punto Babel de configuración pero aquí ya termino los pego y básicamente esto es lo que yo necesito.

Voy a grabar los cambios voy a ejecutar ahora nuevamente.

MPM histogramas Déjeme ver si no hay nada más que una configuración manual eso sería todo entonces Ok voy a ejecutar el comando de MPM rond Bil voy a presionar enter perfectos que hace la configuración me creó el diseño miro aquí el Main y voy a buscar la palabra Const y OK miremos lo que acaba de pasar por lo menos ya tengo ofuscado el código que está en diferentes líneas pero bueno ya está ofuscado pueden ver que aquí tengo constante igualas documenté Element y ya vamos llegando al punto donde yo quería estar pero todavía necesito que esto sea una sola línea que a comentarios y a su vez que no use la que no use las características del ECMAScript 6 o superior entonces para eso vamos a ocupar todavía otro paquete y yo sé que yo sé que ya están cansados que estamos instalando paquetes pero bueno así es como se hace la parte de la congelación de la UEFA.

Pero recuerden una vez que ya tienen esto simplemente toman el proyecto y ya está todo configurado por defecto.

Entonces nos hace falta un plugin.

Vamos a ver si lo podemos encontrar aquí rápidamente Wolfpack entonces igual vamos a buscar en Internet este que dice Babel mínima mini plugin.

Entonces voy a seleccionar acá también les dejo este enlace el material adjunto por si acaso no llegan directamente.

Hay que hacer esta instalación nuevamente la vamos a copiar vimos acá voy a pegarlo enemistó Babes mini fi wapa plugin fenomenos aided el orden como ustedes pueden este Zaitsev no importa mucho.

Esperemos que haga la instalación.

Perfecto regreso acá.

Y cómo se utiliza.

Bueno primero se importa voy a copiar esta primera línea vamos a nuestro web de configuración.

Voy a pegar esto ok regresamos acá y vamos a ver tenemos el modo punto Export en la parte de los plugins hay que utilizar esto.

Aquí pueden mandar mini Options y plugin options pero esta configuración por defecto es más que lo que yo necesito.

Entonces hemos plugins y creo que ya les había les había mentido y les había dicho que ya no íbamos a poner nada más.

Pero también es importante que ustedes sepan cómo funciona esto de los plugins y también creo que voy a agregar un vídeo más donde usaremos otro plugin pero eso va a ser opcional.

Pero bueno voy a poner aquí mini plugin regresamos acá y ustedes si quieren pueden ver qué otras configuraciones pueden ponerle a este paquete.

Ok ya lo tenemos acá.

Asegurémonos de que estamos trabajando en producción y ya hemos hecho todas estas configuraciones en el de producción vamos de nuevo.

R.p.m Rong Bildt.

Vamos a esperar que lo haga.

No dio ningún error.

Ahora mi main tenemos todo en una sola línea.

Y vamos a buscar si tenemos Conget.

Y como ustedes pueden observar todavía sigue estando en una constante pero por lo menos ya lo tenemos minimizado gracias al mini film para cambiar esto y Pasarella ahora sí al estándar del scrip 5.

Entonces lo que vamos a tener que hacer yo sé que esto no les gusta pero vamos a buscar en Google Babel presets environment.

Podemos ir al primer enlace que vamos a ver.

También les dejo esto en el material adjunto y aquí está la instalación y esta va a ser la última que creo que vamos a instalar.

Ok entonces vamos a pegar esto en mis Zolder.

Yo sé que son muchas instalaciones esta parte del Babel siempre es un poquito complicada especialmente porque esto no se hace tan frecuentemente se mete con ustedes hacen la instalación del Babel.

Ya sólo lo hacen una vez y ustedes se olvidan.

Entonces tenemos aquí el Babel presen voy a cerrarlo y hay que utilizarlo.

Aquí creo que debería decir que hay que ponerlo en la configuración de Babel tenemos presencia y aquí está la configuración.

Entonces voy a irme aquí va a haber configuración y aquí lo voy a poner entre comillas dobles comillas dobles o simples porque esto se asemeja a un archivo Jayson.

Voy a grabar los cambios y si no estoy mal ya deberíamos de ejecutar nuevamente el comando en FM romboidal y esto debería de ejecutar mi pressen environment.

Ustedes también pueden ver aquí si quieren agregar configuraciones al respecto pero con esto debía ser más que suficiente y no me fijé cuál de los dos se creó.

Entonces voy a volver a hacer el bien.

Perdón perfecto vamos a abrirlo y busquemos Const y van a ver que ya no aparece la constante ya tenemos Baur a igual document y esta versión de nuestra aplicación va a ser mucho más compatible con otros navegadores web con navegadores web viejos.

Eventualmente cuando más Crips sea el estándar soportado por toda la industria entonces no hace falta hacer esta conversión.

Pero por momentos lo que acabamos de hacer con estas configuraciones es decirle que cuando yo genero para producción amplíe la compatibilidad de mi aplicación.

Lo interesante de esto es que vamos a poder utilizar funciones de flecha.

Vamos a poder utilizar promesas y otras cosas que vamos a ver más adelante y ustedes no se preocupen porque su aplicación no vaya a correr bien en un navegador web ustedes simplemente le dejan ese trabajo a Babel y también quiero que no tenga aquí algo interesante.

Se acuerda que yo tenía la interpolación de strengths teníamos como combatí y eso también es nuevo.

ECMAScript 6 entonces acá lo convirtió a su equivalente en más que cinco.

Bueno ya más que ese 5 Bueno hemos hecho toda la instalación de Babel de producción de desarrollo y lo último que falta para que quedemos bien bien con esto es hacer un backup de todo nuestro proyecto en la nube eso se los voy a mostrar en la siguiente sección porque ya esto es el fin de la misma les voy a dejar el código fuente pero a su vez yo quiero que ustedes sean capaces de poder subir esto a su repositorio para que ustedes tengan el control del mismo saber por lo menos cómo subir cosas allí dijo.

Es algo que los desarrolladores de JavaScript deberíamos de conocer por lo menos en sus fundamentos.

Pero antes de terminar esa sección quiero añadir un paquete adicional sólo para eliminar automáticamente la carpeta Viz porque como ustedes vieron es bastante tedioso.

Cada vez que hago un video tengo que acordarme de borrarla que parece mejor hagamos un procedimiento que lo haga de forma automática.

## 95 Limpiando la carpeta Dist :clock3: 04:30

Ahora como ustedes pudieron notar cada vez que yo hago un Bildt hacemos un Bildt entonces aquí ya tenemos un archivo Main y si luego hago una modificación pequeña como por ejemplo poner nombres como si no dominacion grabo cambios y vuelvo a ejecutar el rock Bildt un segundo me crea otro chivó Main y digamos que lo regreso como estaba originalmente grabo los cambios y vuelvo a ser un Bildt.

Entonces tenemos ya un montón de mains aquí creo que me dejó el mismo Fernando con doble signo de migración en su momento momento metodista tenemos tres archivos.

Y qué dolor de cabeza y puede ser que a mí se me olvide borrar esto y pudiera ser que la configuración Wolfpack demore sus usos su par de segundos.

Entonces qué pereza tener que hacer esta eliminación manualmente.

Qué les parece si hacemos algo para que se borre de manera automática por nosotros en Internet ustedes van a encontrar una gran cantidad de paquetes y plugins para web Pack.

También les sugeriría que antes de buscar digamos paquetes de terceros utilicen o busquen los propios de la web pagesos convenir en el material adjunto yo les dejo a ustedes un enlace que lo debería llevar directamente a este lugar declinen up folder o Tatis folder.

En el peor de los casos que ustedes llegaran a esta página entonces baja un poco y busquen donde dice Quina o criminal.

Entonces aquí hay que hacer una instalación.

Yo sé que más de uno dice Oh Dios santo bueno esto es opcional si quieren ustedes pueden hacerlo manualmente pero yo no quiero hacer eso cada vez que quiero generar la carpeta de producción.

Entonces copiamos esto lo vamos a pegar acá en enemistó menos menos Soib de Kling web para clothing presionó Enter.

Dejo que esto haga la instalación y por aquí abajo tenemos la configuración que es bastante sencilla y ya deberíamos de saber copiar esa línea.

Ya les explico por qué esto es un poquito diferente.

Voy a dejar todo este basurero ahí no se preocupen ya lo hablamos a limpiar de forma automática y en el de configuración de producción.

Esto si quieren también lo pueden poner en desarrollo si así lo quieren y voy a pegar esto acá me van a preguntar.

Pero esta instalación es diferente porque esta tiene llaves y qué es esto bueno cuando ustedes instalan este Clean Wolfpack plugin y usan ésta esto ya sitas que ustedes ya deberían de saber qué es eso es una desestructuración de ciertos paquetes que viene acá prácticamente con esto lo único que digo es que lo único que me interesa de todo este paquete es este esta clase o esta función Clean web plugin eso es todo.

Y por cierto aquí me di cuenta de que tengo doble comilla debería ser comilla sencilla para manejar el mismo estándar entonces luego hay que utilizar este plugin así que bien en la parte de los proving sólo se inicializar y eso sería todo.

Y ahora si esto va a ser el último plugin que vamos a usar por los momentos que bajemos los cambios en el plugin y vamos a ver si funciona les voy a pedir que hagamos no creo que con ese cambio suficiente para que lo borre voy a ejecutar nuevamente de MPM View presionó enter y debería de borrarse todo.

Vamos a ver.

Perfecto.

Se borró todo y sólo me dejó el archivo correspondiente que debería ser el que está importado.

Ok ahí está.

Ese es exactamente lo que entonces quiero que no tenga algo es que si ustedes vuelven a ejecutar Herron Bill y no hicieron ningún cambio esto va a quedar exactamente igual.

No es que se va a borrar no es que va a crear nada nuevo.

Si se mantienen los cambios entonces no vuelve a generar un nuevo Jack para este archivo hasta que ustedes hacen algún cambio.

Voy a borrar esto clavarnos cambios voy a volverlo ejecutar ahí ustedes van a notar que este cambia.

Ahí está bueno eso era básicamente todo lo que quería llegar hasta este punto.

Los voy a dejar así mi clase mi configuración del Wolfpack y les dejo en la siguiente elección este archivo para que usted ya tenga su configuración.

Iba a haber un pequeño bonus después de esta sección en la cual les voy a enseñar a que ustedes suban esto al.

En el caso de que ustedes quieran tener un control total de su repositorio ya que saber un poquito o por lo menos subir cosas aquí es un conocimiento que es necesario para cualquier desarrollador web.

Entonces lo dejamos así.

Espero que esta sección a pesar de que fue muy tediosa yo sé que realizamos una cantidad bueno todas estas instalaciones.

Lo importante es que ya tenemos configurado nuestro Wolfpack como nosotros queríamos y ustedes saben qué hace cada uno de estos plugins.

Lo dejamos así los veo en la próxima clase y sección.

## 96 Código fuente de la sección :clock3: 00:08

#### Código fuente

Aquí les dejo el código fuente por si lo llegan a necesitar en un futuro.

[Repositorio del proyecto - Github](https://github.com/Klerith/webpack-configuracion-estandar)

Espero que el curso les este gustando mucho y sobre todo que estemos aprendiendo bastante

#### Recursos de esta clase

webpack-configuracion-estandar-master.zip
