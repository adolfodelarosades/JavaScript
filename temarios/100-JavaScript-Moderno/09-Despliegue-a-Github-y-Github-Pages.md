# 09 Despliegue a Github y Github Pages • 6 clases • :clock1: 33m

* 97 Introducción a la sección :clock3: 02:10
* 98 Temas puntuales de la sección :clock3: 00:13
* 99 ¿Por qué debo de saber Git? :clock3: 06:03
* 100 Configuración de Git en nuestro equipo :clock3: 08:46
* 101 Desplegar el proyecto a Github :clock3: 08:53
* 102 Github Pages :clock3: 07:10

## 97 Introducción a la sección 02:10

Estamos entrando a esta sección 9 es bastante corta pero aquí vamos a ver algo que no tiene absolutamente nada que ver con JavaScript y ustedes van a decir bueno porque no quiso meter esta sección y es porque ustedes deberían de conocer sobre Github al menos por lo menos lo básico.

Por qué.

Imagínense que toda la configuración que nosotros hicimos en la sección pasada la tengan que volver a hacer. Uf. Hay que volver a ver todos esos videos de Fernando para ver cómo era la configuración para recordarlo o bien copiar y pegar. Mi proyecto anterior y borrar todo lo que no necesito. 

En fin eso puede ser un verdadero dolor de cabeza y el objetivo de que ustedes tengan un sistema de control de versiones es que simplemente tomen su repositorio o Satomi su proyecto así como lo dejamos en el anterior ejecuten un comando y ya estén listos para empezar a trabajar y ustedes se preocupen de toda la configuración que hicimos de Webpack y simplemente empecemos a crear nuestra aplicación y enfocar el tiempo en lo que realmente importa que es las características de nuestra aplicación que necesitamos hacer.

Así que el objetivo de esta sección es enseñarles a ustedes por lo menos la manera más básica de que ustedes puedan tomar su código y respaldarlo en la nube para que el día de mañana cuando usted necesite volver a tomar toda esa configuración de web porque necesitan crear alguna aplicación simplemente lo toman ejecutamos cuando ya están listos para seguir trabajando entonces esa es la idea.

Si ustedes ya saben perfectamente lo pueden saltar simplemente haga un backup de su repositorio a la nube y si no pues los invito a que hagan esa sección es bastante corta que vale la pena decir que nosotros vamos a utilizar este proyecto básico o nuestro estar de vuelta que acabamos de crear en cada una de las secciones que vienen.

Por qué.

Por qué me interesa que estemos trabajando con importación de módulos con el estándar moderno y poder realizar los despliegues.

No es la aplicación a la web.

Adicionalmente les voy a enseñar un tip para que puedan tomar su aplicación en JavaScript y subirla a la nube a un Host gratuito de GitHub Pages para que le puedan hacer demostraciones a sus clientes sin importar en qué parte del mundo se encuentren.

Bueno eso es básicamente todo lo que quería cubrir o lo que quiero cubrir en esta sección lo veo en el próximo video.

## 98 Temas puntuales de la sección 00:13

En esta sección tocaremos los siguientes temas:

* Comandos básicos de Git
* Configuración inicial de Git
* Crear repositorios
* Desplegar nuestro código a Github
* Desplegar el sitio web a GitHub Pages

Esta sección se la pueden saltar si ya saben git, por eso es de las secciones más cortas del curso, pero lo considero indispensable para cualquier desarrollador.

## 99 ¿Por qué debo de saber Git? 06:03

Como les mencioné en el video introductorio esta sección habla sobre GitHub y aunque no tienen nada que ver con JavaScript es importante que ustedes los comprendan.

También es que recibo muchas preguntas y me dicen Fernando cómo haces para subir esto aquí a GitHub y para qué me pueden servir entre otras cosas.

Bueno imagino que ustedes ya vieron la utilidad porque es muy fácil ayudarles a ustedes mi código fuente y ustedes lo descargan al utilizá y esto se queda aquí en la nube respaldado por los servidores de GitHub y a su vez también deben decirle que aquí Microsoft tiene sus proyectos Nasa tiene proyectos en GitHub en fin muchas empresas lo utilizan para mantener y darle seguimiento a sus proyectos pero bueno no nos vamos a enfocar mucho en GitHub porque como les dije esto no es un curso de GitHub pero sí quiero darle los principales beneficios.

Miren ustedes si están en la universidad si están trabajando en algún proyecto o en cualquier cosa ustedes deberían tener un repositorio utilizando Quip primero porque es gratuito.

Segundo porque es el más popular y tercero porque no es muy común que cuando ustedes estén trabajando en algún proyecto digamos que voy aquí a componentes y llego yo y cambia algo accidentalmente toqué algo así nomás déjenme explicarles que algo así salvé los cambios cerré el archivo y cuando entro nuevamente al mismo hijueputa veo este desmadre y ya tengo un problema y aquí ustedes van a tener que acordarse como estaba aquí pueden pasar dos cosas 1 ustedes pueden ser que hayan hecho backups les voy a enseñar cómo ustedes puede ser que hayan hecho un backup copiando esta carpeta.

Entonces ustedes irían a esa carpeta a buscar en el archivo copian y pegan los cambios y ahí podrían recuperarlo pero es muy probable que ustedes no hayan hecho un respaldo de eso pero si ustedes están acostumbrados a trabajar con GIT eso es tan fácil lo bueno recuperar este archivo es tan fácil como escribir el siguiente comando.

Esto no lo hagan porque obviamente no lo tienen configurado pero sería tan fácil como hacer esto.

GIT Checkout menos menos puntos enter y ya reconstruí el archivo tal cual lo tenía y me va a funcionar todo mi código de nuevo.

Inclusive en casos más extremos puede ser que ustedes querían borrar la carpeta estilos CSS y terminaron borrando la carpeta J3 y todavía para ser más extremos voy a borrarlo de la papelera de reciclaje aquí tengo varias cosas que borrar de la papelera que lo borré de la papelera de reciclaje y usted dice Ay Dios santo burlé me volé la carpeta y necesito recuperar el archivo y ahí es donde GIT también los tiene cubiertos con el mismo comando super sencillo se escriben eso y ya reconstruí mi carpeta J.V nuevamente esa es una de las muchas ventajas que tiene GIT y manejar su proyecto como un repositorio que es básicamente repositorio es el nombre que se le da a un proyecto que ya es protegido o seguido por Guilt entonces esto es algo que yo les quiero enseñar a ustedes por lo menos de las generalidades para que ustedes sean capaces de tomar su código respaldarlo pueden hacer ese check out y a su vez también poder desplegarlo aquí en la web de GitHub y poder reconstruir su proyecto así como está como ustedes pueden observar aquí no está los archivos de El directorio de los módulos de Mahut ni tampoco está el disco porque yo no quiero que estos dos directorios se suban o que les de seguimiento porque no vale la pena es decir si yo necesito reconstruir los módulos de Nott perfectamente los puedo borrar borrar los módulos de Nott y aunque yo haga.

Ups perdón yo aunque yo haga el check out nuevamente con esta instrucción no se van a reconstruir porque no le está dando seguimiento y más de uno a decir Fernando pero eso es crucial porque ahora mi aplicación no va a funcionar efectivamente si yo hago RPM start personalmente y me ha dado un montón de errores porque no existen esos paquetes en los módulos de Nott Bueno de hecho ni existen.

Entonces en ese caso lo que tendríamos que hacer es el comando NPM instó a no presionar Enter y esto va a realizar toda la instalación de todos los paquetes que nosotros tenemos configurados en nuestro paquete apuntó Jayson.

Todos todos todos.

Tal cual estaba el proyecto y optimizados también obviamente al sistema operativo donde ustedes están corriendo su aplicación.

Esto no debería de tardar mucho aunque depende de qué tantos paquetes son.

En mi caso ya terminó tardo 15 segundos pero puede ser por la velocidad del internet entonces nuevamente puedo intentar el comando NPM start van a ver que ya pasa todo me abrió mi explicación y así lo habíamos dejado.

Por eso es que no se le da seguimiento a los módulos de Nott porque este directorio se puede construir en base al paquete punto Jayson.

Eso es básicamente y lo mismo pasa con la carpeta disco.

Usted ya sabe por qué no le hacemos un seguimiento porque eso es producto del NPM Rong Bildt Biot presiona Enter y esto vuelve a construirme y por eso esos dos directores no se les acostumbra a dar seguimiento porque son directorios que se pueden construir con comandos de nuestra aplicación.

Entonces eso es básicamente lo que quiero hacer quiero enseñarles a ustedes a poder tener su repositorio a poder hacer fotografías o comics de cómo se encuentra su proyecto en ese momento y poder desplegarlo aquí en este enlace.

No se preocupen lo vamos a ver en la próxima clase porque hay que hacer una instalación pero bueno eso es básicamente y también les quiero enseñar cómo subirlo acá para que ustedes lo puedan descargar.

Y también voy a llevarlos un pasito más adelante para que podamos desplegar este directorio Tissot en ellos que es un hosting gratuito que les da dibujo para que puedan desplegar aplicaciones que son puramente HTML JSE y CSS perfectamente nuestra aplicación de JavaScript compresor requisitos y por lo cual podríamos desplegarla en la web de Kidjo para que nuestro sitio web sea HTTPS y su nombre de usuario bueno lo voy a dejar hasta este punto.

Espero que por lo menos haya despertado un poquito de interés en lo que es GIP y los veo en la próxima clase.

Recuerden que si nada de lo que está en esta sección les interesa saltársela y vayamos a la siguiente sección donde vamos a hacer una aplicación de un todo utilizando el Webpack y otros comandos de JavaScript.


## 100 Configuración de Git en nuestro equipo 08:46

Que vamos a comenzar.

Y para este ejercicio vamos a trabajar con la carpeta 03 pack inicial que este es el proyecto que yo quiero mantenerlo en gibt y también en mi hijo pero ya vamos a ver. 

Por cierto Git y GitHub son cosas totalmente diferentes es como Java y Javascript.

Las dos cosas son totalmente diferentes son compañías independientes en fin pero GitHub es el nombre que tiene para que suene familiar y la gente diga ok bueno bueno lo asocien con que es lo mismo que hizo pero son son empresas diferentes.

Bueno dicho eso nosotros vamos a trabajar con esta carpeta.

Si ustedes no la tienen terminada pueden descargarlo del código al final de la sección anterior y pegarlo acá ok.

Obviamente ustedes en el video anterior si ustedes hacen esa descarga no tienen los módulos de Nott ni la carpeta Boyz pero ustedes ya saben cómo reconstruirlo porque sólo vimos en el video pasado Ok voy a trabajar con la carpeta 03 inicial y así ya habíamos dejado el proyecto.

Lo primero que les voy a pedir es que se descarguen del material adjunto dos cosas 1 tienen este PDF que lo vamos a empezar a ver en las en breve.

Es un documento oficial de GitHub que les ayuda con todas las instalaciones y configuraciones que van a necesitar para trabajar con GitHub.

También ustedes van a notar acá que hay más información que yo no voy a cubrir. Pero aquí hay términos interesantes. Disculpen que esté en inglés pero no lo encontré en español. Pero bueno aquí vamos a seguirlo por lo menos los conceptos básicos para que nosotros podamos hacer todo el trabajo que yo necesito. Tenga la vía abierta. También en el material adjunto ustedes tienen un enlace que lo debería llevar a la página oficial de GIT que es SSM puntocom bajamos un poco y vamos a realizar la instalación es súper fácil para los usuarios.

Dependiendo el sistema operativo aquí este botón va a cambiar. Voy a tocar downloaded puede ser que aquí aparezca ya automáticamente la instalación o sea se empieza la descarga y si no lo haces entonces hacé click acá que aquí lo lleva a SourceForge y esperemos un segundo. Perfecto. Ahí ya empieza a hacer la descarga y Podemos. Bueno no lo voy a abrir y podemos cerrar este archivo.

Ahora la instalación depende mucho del sistema operativo les voy a pedir que sigan los pasos dependiendo de la instalación de su sistema operativo para inoxidables X. Básicamente es casi quedarles NEXT NEXT NEXT aquí voy a darle Open Open Me está apareciendo esto y aquí sólo de darle Next Next Next y darle Next Next Next y hasta que se termine la instalación no hay que 
hacer nada en OS X prácticamente y en Linux para los usuarios de Windows es prácticamente lo mismo solo que también les ayuda a configurar el gripas ustedes con la configuración por defecto en Windows siemplemente de la conexión a Internet hasta que se acaba el mundo y ya tienen instalado que no hace falta ninguna configuración especial y si lo necesitáramos pues se puede hacer después de la instalación.

Ok yo tengo instalado Git de recuerden que otra cosa independiente pueden confirmarlo abriendo la terminal la ventana de comandos lo que sea que ustedes utilicen. Y aquí pueden escribir Git menos menos versión presionan gente iban a ver que aquí tenemos esta versión la versión que ustedes tienen hoy.

Ok dejen la terminal abierta ustedes perfectamente pueden usar mi base que es algo que se instala cuando instalan Guida en Windows que yo les recomendaría que lo utilizaran si van a trabajar con Kit es más parecido a lo que es la terminal de Linux la cual aunque Uds. no les guste Linux aunque no quieran trabajar en linux pues básicamente el 90 por ciento de los servidores en Internet están basados en Linux antes de empezar a trabajar con quietecitos hacer estas configuraciones.

Voy a ser un poco más grande para que podamos verlo porque necesitamos hacer esas configuraciones si quieren pueden copiarse. Esto lo voy a pegar acá y en el User Name ustedes van a colocar su nombre y presionan ok.

Normalmente Enguita si no les aparece ningún mensaje quiere decir que lo hizo correctamente. Aquí me aceptó mi comando. Luego voy a hacer la configuración del email. Voy a copiar esto no voy a pegar acá y aquí vamos a cambiar por su correo electrónico en mi caso Fernando apuntó Herrera 85 arroba gmail.com perfecto presionã gente y aquí eso se lo quieren hacer para que pongan los colores y que sea más claro si quieren lo hacen bueno yo se lo recomendaría pero yo ya lo hice pero no voy a hacer por qué no que ya lo hice perfecto yo tengo configurado Git.

Así de sencillo fue lo siguiente que voy a hacer es inicializar mi repositorio. Recuerden que un repositorio es básicamente su carpeta del proyecto esto es mi repositorio. Aquí podemos usar la terminal integrada de Visual Studio Cott perfectamente para hacer estos comandos inclusive esto los pude haber hecho ya pero bueno es para que ustedes vean que se puede hacer el comando 
que me pide hacer para inicializar mi repositorio es el GIP init.

Entonces voy a pegar aquí INIT y presionó enter esto inicializar mi proyecto y ese mensaje A ustedes no les no le presté atención porque es que yo ya había hecho los cambios acá es decir había trabajo con este repositorio para desplegarlo anteriormente entonces reseteo todo. Pero bueno entonces este comando inicializar su repositorio para que ustedes estén listos para realizar todos los cambios.

Pocas palabras le dice Ustedes están diciendo que OK GIT preparate porque yo voy a empezar a trabajar en mi proyecto y este es mi repositorio. Vamos a ver el segundo comando de clones por si acaso ustedes quieren tomar un repositorio que esté en otro lugar y hacer una copia. No voy a utilizar nada de esto porque no voy a utilizar esto. Vamos a ver si tenemos más información aquí que pueda servir y por el momento lo voy a dejar así. Voy a cerrar este archivo ustedes lo pueden leer es importante pero ahora yo ya tengo mi repositorio visualizado algo que se acostumbra inmediatamente hacer cuando ustedes hacen GIT init es crearse un archivo de configuración llamado GIT ignoré. De esta manera unpunto GIT ignoré. Recuerden que el punto básicamente en Linux es el que le va a decir que su archivo oculto para que no sea tan fácil de manipular el archivo Kit ignoré.

Básicamente le dice qué carpetas y qué archivos ustedes no quieren que esté pendiente de los cambios porque imagínense que estuviera pendiente de este montón de directorios porque son un montón son un montón y ustedes no quieren que le dé seguimiento a eso porque es código que ustedes no hicieron y se puede reconstruir muy fácilmente con el paquete apuntó Jayson.

Entonces es bien común que ustedes escriban aquí Nott modus Slash graban los cambios llegan a ver cómo se pone en gris eso significa que ahora ya no le está dando seguimiento.

Lo mismo voy a hacer con la carpeta list. Por qué.

Porque la carpeta Adis puede ser bueno se genera en base a un comando de El Paquete apuntó Jayson.

Este comando que teníamos acá de MPM Bill y Wílder perfecto ahora antes de terminar este video quiero dejar funcionando eso de poder recuperar los archivos en el peor de los casos.

Entonces voy a cerrar esto voy a abrir la terminal nuevamente y necesito ejecutar el siguiente comando get a punto enter lo que hace este comando es que le dice aquí ok.

Necesito que todos los archivos que yo modifiqué. 

Todo lo que yo he trabajado desde que hice mi último comic pero como todavía no he hecho ninguno entonces está diciéndole que todos los archivos que tengo en mi proyecto preparate para tomarle una foto.

Esa fotografía les va a ayudar a ustedes a poderlas recuperar en un futuro o poder indicar cómo estaba su proyecto en este preciso momento y punto del tiempo.

Ustedes eventualmente podrían regresar a ella ver los cambios compararlos hacer muchas cosas entonces seguir a lo que hace es decir la que se prepare para tomar una fotografía de cómo está mi proyecto o mi repositorio en este momento ahora para tomar la fotografía es el siguiente código Git commit van a poner un menos C.M. para colocar un mensaje y entre comillas van a escribir un mensaje significativo como primer comic o inicialización de mi proyecto o como ustedes quieran ponerle iban a presionar enter.

Después de realizar ese comando recuerden Guitá y luego el comic ustedes van a ser capaces de recuperar su repositorio tal cual estaba en este momento y por ejemplo yo podría borrar el Sors completamente borré toda mi carpeta sours y podemos hacer el comando quick check out menos menos espacio Punto presionar personalmente iban a ver que la reconstruye no se preocupen si ustedes me ven aquí que tengo esto en verde u otros colores ustedes deberían tener ya todo en blanco.

Pero es que como yo he estado jugando con este repositorio para hacer estos videos esto es por eso que se está confundiendo con los corales. No se preocupen que eso es básicamente lo que quería cubrir en esta clase.

La instalación que fue bastante sencilla y también estamos viendo de qué manera podemos recuperar nuestro proyecto en caso que borremos algo que lo dejamos así y continuamos con la siguiente clase.

Acerca de este curso Webpack, Clases, Propiedades privadas, ESNext, Node, Npm, Babel, Hot Reaload, CRUD, Carga de archivos y más!

## 101 Desplegar el proyecto a Github 08:53

Para desplegar nuestro repositorio aquí aquí lo único que vamos a ocupar es tener una cuenta. Es totalmente gratuito. No tienen que pagar nada. Hay ciertas características de pago ustedes los pueden ver las pueden investigar de hecho pueden hacer click aquí dice Frayssinet y tener en cuenta los diferentes planes que tiene. Ok pero para lo que vamos a hacer pueden trabajar de manera gratuita se crean usuarios y ustedes ya tienen uno pues perfectamente pueden hacerlo comence sigan estos pasos y al final van a llegar a una página muy parecida a esta.

Bueno no tan igual va a ser va a salir vacía pero es porque yo tengo varios proyectos con esta cuenta y también la que utilizo para fines educativos entre otras cosas.

Entonces hay que crearse un nuevo repositorio. Hay varias formas de hacerlo pueden buscar este botón verde o aquí en el símbolo más nuevo repositorio hacen clic ahí y vamos a ponerle el nombre Wolfpack o el nombre que ustedes quieran Wolfpack menos el starter o el nombre que ustedes quieran ponerle. Pero la única condición es que este proyecto tiene que ser como con el nombre único dentro de su cuenta de Kidjo le puedes dar una descripción como éste es el cascarón de mis aplicaciones que usen web. Ok ok.

La ventaja de esto es que ustedes ya no van a tener que volver a hacer toda esa configuración que hicimos en la sección pasada porque son dolor de cabeza y al tenerlo acá usted simplemente lo descargan y ya están listos en segundos para empezar a trabajar con este proyecto. Si ustedes quieren pueden dejarlo como público o privado es indiferente con la única diferencia que si ustedes lo ponen en privado solo ustedes lo van a poder trabajar y si lo hacen público todo el mundo lo va a poder ver.

En mi caso yo lo voy a dejar público si quieren ustedes lo pueden hacer privado pero como ustedes quieran público o privado ustedes van a poder trabajar de la misma manera.

Yo lo voy a dejar público y no voy a inicializar ni voy a agregar nada más. Crear repositorio ahora les va a aparecer unos pasos para poder realizar el despliegue. Hay dos formas si ustedes ven esto de parte de Eco web para starter y lo que crea es un archivo y punto.

MB que es de Mark Down. Esto lo vamos a hacer manualmente. No se preocupe que hicimos nuestro init aquí ya agregaba este archivo al repositorio es muy parecido al kit apuntó pero especificando el archivo ya hicimos nuestro primer cómic y básicamente los dos comandos que ocupamos son estos dos es seguir Behemoth a lo que hace es agregar un origen remoto a nuestro repositorio.

Es decir nosotros vamos a querer desplegar nuestro repositorio todos sus cambios todos los que nosotros hagamos a este lugar. Entonces esa es la instrucción la voy a copiar voy a regresar a mi proyecto. Recuerden que para eso yo ya tuve que haber hecho el YIP a punto y el comic pero ustedes si quieren saber pueden hacer un blog y presionar ENTER y se van a dar cuenta que aquí tenemos nuestro primer cómic.

O sea ya estamos listos para explicar esto. Entonces vamos a pegar el comando de Guillemot Origin. Obviamente ustedes usen el de ustedes no van a poder hacer despliegues a mi repositorio van a presionar enter.

Voy a regresar acá y ahora voy a copiar la segunda línea acopio el quipus. Básicamente lo que dice es sube todo mi repositorio. Los últimos cambios hacia el origen o el origen que va a hacer este repositorio.

El origen es una manera de identificar a este repositorio. Entonces básicamente le digo que sube todo al origen que sería éste y el Master es el nombre de la rama. Nosotros no vamos a ver ramas en este curso pero entiendan que el master sería la rama principal o sea el proyecto como tal hacia donde estoy.

Es decir puedo crear una rama o una separación o bifurcación de mi aplicación como una versión alternativa o una dimensión alterna en la cual ustedes pueden hacer cambios a su proyecto sin afectar el código original.

Y si funcionan los cambios ustedes lo pueden unir o pueden desechar todo y no pasó nada bien interesante.

Entonces básicamente lo que estoy haciendo acá es decirle que suba todo a este lugar y este menos porque también nos preguntan bastante lo que hace es establecer el origen como mi repositorio en la nube por defecto es decir después de haber hecho esto yo no voy a tener que volver a escribir toda esta sintaxis.

Simplemente tendré que hacer el quipus para que use toda esta configuración por defecto. Eso es básicamente entonces voy a copiar esto lo voy a pegar acá lo voy a presionar ahora aquí pueden pasar varias cosas.

En mi caso yo purgue todo pero me está pareciendo acá este mensaje es muy posible que a ustedes esto les aparezca en la consola y voy a darle Howes al lado.

Puede ser que esto se les está pareciendo en la consola ustedes van a tener que poner su usuario y contraseña de Kidjo cuando ustedes lo ponen van a ver que empieza a subir todo regresamos a nuestro proyecto.

Aquí en el sitio web voy a recargar y ustedes van a observar que aquí ya tenemos nuestro repositorio tal cual lo teníamos en nuestra computadora pero ya lo tenemos en la nube y en el caso de que nosotros perdiéramos toda la carpeta inclusive borramos hoy el kit.

Ya no me pueda responder o para recuperar mis archivos.

Entonces yo ya lo tengo aquí en la nube y lo puedo clonar.

Lo puedo descargar y seguir trabajando como si nada hubiera pasado antes de terminar esta clase después de haber hecho ese Hoppus.

Entonces después de haber hecho eso lo que quiero hacer ahora es subir un nuevo archivo vengo aquí dice que por favor agrega un ritmo ni un ritmo ni en la raíz de mi proyecto básicamente le indica Ajit que Kiprop qué es lo que quiero desplegar acá.

Es como para información de qué es lo que hace este repositorio. Cuando estamos en este nivel. Entonces vamos a crearlos de una vez.

Voy a hacer click derecho nuevo archivo y voy a escribir o le voy a poner el nombre de Read mi punto punto. MB No tiene la sintaxis el Rainy es todo en mayúscula.

Así es el estándar para poner este archivo acá y la extensión puntuamos de Smart Down es muy parecido al HTML pero muy simplificado.

Voy a poner un signo numeral y escriba web pack starter el nombre que ustedes quieran de su proyecto. Ahora les voy a pedir que seleccionemos lo siguiente. Esto ya viene instalado en estudio. Por defecto vamos aquí a Viu comand palet y busquen algo como el Mark Down Open preview este de acá lo seleccionan lo toman y lo voy a poner aquí en un costado.

De esta manera ustedes van a poder ver el resultado de lo que estamos haciendo en Markham aquí entonces pongamos algo como este es el proyecto inicial para crear aplicaciones utilizando Wolfpack utilizando Wolfpack punto voy a poner un par de notas entonces con triple numeral notas 2 puntos y coloquemos las instrucciones para inicializar nuestro proyecto para que no se nos vaya a olvidar recuerden reconstruir los módulos de.

Y para eso voy a poner RIP Baketik Dios mío se perdió. Triple-A Baketik.

De esta manera MPM instó y a su vez para construir el Bild y para construir construir el Bild recuerden los puntos nuevamente con Mataix para colocar el pm. Rong Bild.

Eso es básicamente todo esto es lo que yo acabo de escribir.

Voy a cerrar voy a grabar los cambios en el ruindades punto M.D y ahora tengo que subir este archivo entonces aquí se lo voy a dejar de tarea.

Ustedes tienen que hacer lo mismo tienen que hacer el a tienen que hacer el jeep commit y tienen que hacer el quipus.

Eso es básicamente todo en ese orden para que ustedes lo vean acá.

Después de revisar el bus van a recargar un navegador web y ustedes van a ver que se subió el Redmi y debería de aparecer aquí.

Por favor no utilicen este botón porque si no va a ser diferente el procedimiento.

Entonces hagámoslo de esa manera.

Suban este archivo para que al refrescarlo aparezca aquí abajo.

Recuerden que le tienen que poner exactamente este nombre y yo regreso con ustedes unos instantes con la solución.

Así que ahora intenten desplegar este archivo. Ok lo lograron hacer.

Espero que no haya o no haya tenido ningún inconveniente o hacer esto juntos. Lo primero es GIP a punto.

Luego el jeep commit menos cm para poner un mensaje y el mensaje va a ser Redmi Redmi creado.

Ahora podemos hacer quipus y pues no hace falta poner al menos su porque como ya lo hicimos entonces al hacer un quipus se va a utilizar mi repositorio que yo tengo configurado en el origen por defecto.

No sé por qué me pierdo otra vez pero voy a poner a Westland y listo.

Ya perfecto lo sube.

Voy a regresar a cada recarga navegador web y deberíamos de ver nuestro Reni desplegado acá también lo dejamos acá pero lo interesante es que como ustedes le ponen ese nombre Guijo lo va a leer y eso es la descripción que va a poner aquí abajo bastante útil para enseñarle a otras personas cómo funciona su repositorio cómo trabaja etcétera etcétera.

Ok lo voy a dejar hasta este punto y nos veo en el siguiente video.

Acerca de este curso

## 102 Github Pages 07:10

Dijo nos ofrece una opción de tener un hosting gratuito para proyectos que solo sean HTML CSS y JavaScript.

Qué quiere decir que si ustedes suben archivos de PHP eso no va a funcionar si suben archivos eso no va a funcionar soy choose not no va a funcionar a lo que me refiero es que nos va a permitir desplegar aplicaciones no digamos básicas sino aplicaciones que sólo tengan tecnologías HTML J3 y Ce6.

Por ejemplo si ustedes hacen una aplicación en redacten angular u otro framework básicamente lo van a poder desplegar Ginjo copetes. 

Para eso voy a irme aquí a Settings. Voy a bajar un poco y por aquí dice Celles hay varias formas de hacer esto vamos a seleccionar acá y hay dos opciones interesantes Una es desplegar el master Branch pero antes de que hagan clic aquí.

De hecho de ahí no le van a dar clic solo quiero mostrarles aquí el master Bridge es básicamente todo este repositorio es decir intente desplegar todo esto como si fuera un sitio web y eso no va a funcionar. 

Me regresan aquí dos reyes por qué no va a funcionar porque recuerden que nuestra aplicación usan Nott para crear lo que es la carpeta de distribución para unificar el Indec importando módulos entre otras cosas entonces éste no es el proyecto que yo necesito que se despliegue directamente lo que yo necesito hacer es desplegar la aplicación de producción es decir este diseño pero yo no estoy subiendo aquí y no debería de subirlo a Ginjo porque es el producto del video.

Entonces qué puedo hacer si ustedes regresan aquí a la parte de Guijo pellets también tienen una opción de subir o desplegar una carpeta docx.

Esto es bueno no se puede cambiar.

Este es el nombre que Guijo va a pedir o que va a buscar en sus repositorios para desplegar eso como dijo paisos a como para desplegarlo en Internet entonces vamos a crear esto e nuestro repositorio.

Voy a ejecutar el siguiente comando bien sencillo que ya lo conocen.

MPM Rohn Bildt Enter.

Esto ya genera la aplicación de producción que logra cerrar voy a abrir acá aquí tengo mi main aquí tengo todo esto pero recuerden que como lo pusimos en el kit ignoré esto no se va a subir pero yo necesito subir una carpeta llamada Docs Kidjo.

Entonces lo que voy a hacer es bien sencillo voy a re nombrarlo y lo voy a poner docx presionar enter. Eso es básicamente todo. Ustedes van a notar que ya cambio de color.

Ahora ya no es el mismo directorio. Ahora este se llama docx que contiene mi aplicación desplegã. Ahora lo que voy a hacer acá es abrir nuevamente la terminal puedo hacer un kit de status y van a presionar enter este comando lo que les va a decir a ustedes es que tenemos un nuevo directorio llamado docx el cual no se le está dando seguimiento y nos recomienda que hagamos el kit App para darle seguimiento al mismo.

Entonces eso es lo que vamos a hacer. A punto de apresar enter y después de hacer la tengo que tomar en la fotografía para poderlo subir aquí entonces nuevamente GIT comi menos cm y el mensaje va a ser docks creado presiona Enter.

Ok entonces aquí lo que hace es añadir toda esta aplicación a mi repositorio y lo tengo aquí listo listo para subirlo.

Ahora vamos a subirlo con el comando guipur presionó enter y esto debería de subirlo esperemos que termine listo.

Voy a recargar aquí mi navegador web en el repositorio y ya tengo la carpeta Docs el cual contiene si la aplicación que yo necesito desplegar con sus hojas con sus Ag7 CSS y vamos a ver si esta carpeta funciona o si esto no lo puedo desplegar a Internet.

Recemos acá a la parte de la serie donde dice Guijo pellets y ahora voy a seleccionar Master brunch docx fólder lo seleccionamos.

Bueno puede ser que no les aparezca porque ese folder no existía en el momento en que yo lo cree o mejor dicho en esta página entonces voy a refrescar el navegador web en esta pantalla.

Bueno si ya lo hizo ni me di cuenta en el momento que os referís pero voy a volver a abrir y seleccione Master branches las docx folder experencia un segundo va a decir Guijo pellet sorts Soib vamos a bajar un poco y aquí hay que tener un poquito de paciencia. Ok.

Note que dice que tu sitio está listo para ser publicado en este R.L.

Por favor usen el Udes y todavía no le den click no le den click porque todavía lo está configurando esto Guijo está preparando su sitio web lo está levantando está preparando todo y van a refrescar nuevamente el navegador web y hasta que aparezca en verde ustedes lo van a poder ver.

Entonces voy a hacer click en él y van a ver que ya está mi aplicación tal cual puedo verla aquí la consola no se preocupen por este error este FAP hoy es el hito que se le pone acá y se quedó lo logró encontrar.

Pero bueno eso no es problema aquí tenemos nuestra etiqueta y se carga nuevamente el navegador web ya no tienen ese rol.

Ok lo interesante de esto es que si ustedes se fijan en el R.L es el R.L desplegado en Guijo con su certificado de HTTPS y esta es su aplicación de JavaScript desplegada en un Jasen de ustedes pueden dársela a algún cliente para que lo revise puede montar sus aplicaciones aquí siempre y cuando cumplan la condición de que sólo sean HTML CSS y JavaScript.

En fin esto es sumamente útil por los momentos. Esto es lo que yo quiero que lo dejemos.

Si ustedes necesitaran hacer algún nuevo cambio en el sitio web despegados lo que tendría que hacer es hacer un nuevo diseño y desplegar los cambios en este folder o en su directorio y volverlos a subir.

Eso es básicamente todo ok.

Espero que esta introducción de lo que es GIT y Guijo le sirva de verdad créeme que ustedes tienen que saber utilizar algún sistema de control de versiones porque no sólo es buena práctica sino que les va a ayudar a ustedes a prevenir problemas como lo que les mencioné de que ustedes pierden código y ya a estas alturas del partido con sitios como Guijo o tecnologías como GIT deberían de impedir que ustedes pierdan código.

Yo he tenido gran cantidad de compañeros de trabajo que dice ay pero yo no tengo el código fuente del programa y por qué no tienes el código fuente del programa porque no tiene un seguimiento o un repositorio en el cual él haga sus despliegues y Guijo gratuitos.

Prácticamente no hay razón o justificación para perder código. Hoy en día.

Entonces por favor acostúmbrese a estar haciendo comics cada vez que ustedes terminaran de hacer algún cambio en unos archivos cuando las cosas funcionen ustedes campus aquí Joop se hagan los comics suban o Guijo y acostúmbrese a trabajar de una manera ordenada y sobretodo segura para que ustedes no tengan o no se vean en la dolorosa situación de perder código.

Entonces eso es básicamente todo lo que quería cubrir. Si ustedes quieren saber más sobre Guidi y tengo un curso especializado en esos temas pero por momentos esto es lo básico que Uds. deberían de conocer a la hora de trabajar con Kit y Kidjo.

Eso es todo. Los veo en el siguiente video obviamente aquí no hay código fuente de la sección porque no tiene sentido pero lo voy a dejar así y los veo en la próxima sección donde vamos a continuar trabajando en JavaScript.

Acerca de este curso
Webpack, Clases, Propiedades privadas, ESNext, Node, Npm, Babel, Hot Reaload, CRUD, Carga de archivos y más!
