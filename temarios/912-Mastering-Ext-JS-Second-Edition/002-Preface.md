# Prefacio
Si es un desarrollador de Ext JS, probablemente le tomó un tiempo aprender el framework. Sabemos que la curva de aprendizaje de Ext JS no es corta. Una vez que hemos aprendido los conceptos básicos y necesitamos usar Ext JS en nuestros trabajos diarios, surgen muchas preguntas: ¿cómo puede un componente comunicarse con otro? ¿Cuáles son las mejores prácticas? ¿Realmente vale la pena utilizar este enfoque y no otro? ¿Hay alguna otra forma en que pueda implementar la misma función? Esto es normal.

Este libro fue escrito pensando en estos desarrolladores.

Entonces, de esto se trata este libro: ¿cómo reunimos todo y creamos aplicaciones realmente agradables con Ext JS? Vamos a crear una aplicación completa, desde la maqueta de las pantallas hasta su puesta en producción. Vamos a crear la estructura de la aplicación, una pantalla de bienvenida, una pantalla de inicio de sesión, una capacidad multilingüe, un monitor de actividad, un menú dinámico que depende del permiso del usuario y módulos para administrar la información de la base de datos (información simple y compleja). Y luego, aprenderemos cómo construir la aplicación para producción, cómo personalizar el tema y cómo depurarlo.

Usaremos ejemplos del mundo real y veremos cómo podemos implementarlos usando componentes Ext JS. Y a lo largo del libro, también hemos incluido muchos consejos y mejores prácticas para ayudarlo a mejorar su conocimiento de Ext JS y llevarlo al siguiente nivel.

## Que cubre este libro

El Capítulo 1, ***Descripción general de Sencha Ext JS***, presenta Sencha Ext JS y sus capacidades. Este capítulo proporciona referencias que puede leer antes de sumergirse en los otros capítulos de este libro. Esto se hace teniendo en cuenta la posibilidad de que este sea su primer contacto con el framework.

El Capítulo 2, ***Introducción***, presenta la aplicación que se implementa a lo largo del libro, sus características y la maqueta de cada pantalla y módulo (cada capítulo cubre un módulo diferente), y también demuestra cómo crear la estructura de la aplicación usando Sencha Cmd. y cómo crear una pantalla de presentación.

El Capítulo 3, ***La Login Page (página de inicio de sesión)***, explica cómo crear una página de inicio de sesión con Ext JS y cómo manejarla en el lado del servidor y también muestra algunas capacidades adicionales, como agregar el mensaje de advertencia de bloqueo de mayúsculas y enviar la página de inicio de sesión al presionar la tecla Enter.

El Capítulo 4, ***Logout y Capacidad Multilenguaje***, cubre cómo crear la capacidad de cierre de sesión y también el tiempo de espera del monitor de actividad del lado del cliente, lo que significa que si el usuario no usa el mouse o presiona ninguna tecla en el teclado, el sistema finaliza la sesión automáticamente y cierra la sesión. Este capítulo también proporciona un ejemplo de capacidad multilingüe y muestra cómo crear un componente para que el usuario pueda usarlo para cambiar la configuración regional y de idioma del sistema.

El Capítulo 5, ***Menú dinámico avanzado***, trata sobre cómo crear un menú dinámico que depende del permiso del usuario. Las opciones del menú se representan dependiendo de si el usuario tiene permiso o no; de lo contrario, la opción no se mostrará.

El Capítulo 6, ***Administración de usuarios***, explica cómo crear una pantalla para listar todos los usuarios que ya tienen acceso al sistema.

El Capítulo 7, ***Administración de datos estáticos***, cubre cómo implementar un módulo donde el usuario puede editar información como si estuviera editando información directamente desde una tabla MySQL. Este capítulo también explora capacidades como la búsqueda en vivo, el filtro y la edición en línea (usando los complementos de Edición de celdas y Edición de filas). Además, comenzamos a explorar problemas del mundo real cuando desarrollamos grandes aplicaciones con Ext JS, como la reutilización de componentes en toda la aplicación.

El Capítulo 8, ***Administración de contenido***, explora más a fondo la complejidad de administrar información de una tabla de la base de datos y todas sus relaciones con otras tablas. Por eso, cubrimos cómo administrar información compleja y cómo manejar asociaciones dentro de cuadrículas de datos y FormPanels.

El Capítulo 9, ***Adición de capacidades adicionales***, cubre cómo agregar funciones, como la impresión y la capacidad de exportar a PDF y Excel, que no son compatibles de forma nativa con Ext JS. Este capítulo también cubre gráficos y cómo exportarlos a imágenes y PDF y también cómo usar complementos de terceros.

El Capítulo 10, ***Enrutamiento, soporte táctil y depuración***, demuestra cómo habilitar el enrutamiento en el proyecto; también se trata de depurar aplicaciones Ext JS, incluyendo lo que debemos tener cuidado y por qué es muy importante saber cómo depurar. También hablamos rápidamente sobre la transformación de proyectos de Ext JS en aplicaciones móviles (diseño receptivo y soporte táctil), algunas herramientas útiles que pueden ayudarlo en su trabajo diario como desarrollador, y también algunas recomendaciones sobre dónde encontrar complementos adicionales y de código abierto. para usar en proyectos Ext JS.

El Capítulo 11, ***Preparación para Producción y los Temas***, trata sobre cómo personalizar un tema y crear interfaces de usuario personalizadas. También explora los pasos necesarios y los beneficios de empaquetar la aplicación en producción.

## Que necesitas para este libro

La siguiente es una lista del software que necesitará tener instalado antes de ejecutar los ejemplos del libro. La siguiente lista cubre el software exacto utilizado para implementar y ejecutar los ejemplos de este libro, pero puede utilizar cualquier software similar que ya haya instalado y que tenga las mismas funciones.

Para un navegador con una herramienta de depuración, use lo siguiente:

* Firefox con Firebug: https://www.mozilla.org/firefox/ y http://getfirebug.com/
* Google Chrome: http://www.google.com/chrome

Para un servidor web con soporte PHP, use lo siguiente:

* Xampp: http://www.apachefriends.org/en/xampp.html

Para la base de datos, use lo siguiente:

* MySQL: http://dev.mysql.com/downloads/mysql/
* MySQL Workbench: http://dev.mysql.com/downloads/tools/workbench/
* Base de datos de muestra MySQL Sakila: http://dev.mysql.com/doc/index-other.html y http://dev.mysql.com/doc/sakila/en/index.html

Para Sencha Cmd y las herramientas necesarias, utilice lo siguiente:

* Sencha Cmd: http://www.sencha.com/products/sencha-cmd/download
* Ruby 1.8 o 1.9: http://www.ruby-lang.org/en/downloads/
* Sass: http://sass-lang.com/
* Compass: http://compass-style.org/
* Java JDK (versión 7 o posterior): http://www.oracle.com/technetwork/java/javase/downloads/index.html
* Java environment variables: http://docs.oracle.com/javase/tutorial/essential/environment/paths.html
* Apache ANT: http://ant.apache.org/bindownload.cgi
* Apache ANT environment variable: http://ant.apache.org/manual/install.html
Y, por supuesto, Ext JS: http://www.sencha.com/products/extjs/

Usaremos Ext JS 5.0.1 en este libro.

## Para quien es este libro

Si es un desarrollador que está familiarizado con Ext JS y desea mejorar sus habilidades para crear aplicaciones web aún mejores, este es el libro para usted. Se requieren conocimientos básicos de JavaScript/HTML/CSS y cualquier lenguaje del lado del servidor (PHP, Java, C #, Ruby o Python).

