# 1. Introducción a Ext JS 5

* Considerando Ext JS para su próximo proyecto
* Empezando con Ext JS
    * Descargando Ext JS
    * Configuración e instalación de Ext JS 5
       * Sencha Cmd
    * ¿Por qué tantos archivos y carpetas?
       * Carpetas que cambiaron en la versión 5 de versiones anteriores
    * Mirando la imagen completa
* Nuestro primer programa
    * Escribiendo el código Ext JS
    * Añadiendo interacción al programa
* Herramientas y editores
    * XAMPP o WAMP
    * Aptana
    * Arquitecto Sencha
* ¿Qué hay de nuevo en Ext JS 5?
* Resumen

Al aprender una nueva tecnología como Ext JS, algunos desarrolladores se enfrentan a dificultades para empezar, por lo que este libro le brindará la mejor manera posible de comenzar a comprender esta tecnología más que cualquier otra fuente. Tenemos que ir de la documentación de la library a blogs y foros en busca de respuestas, tratando de averiguar cómo funcionan juntos la library y todos los componentes. Aunque hay tutoriales en el centro de aprendizaje oficial, sería genial tener una guía para aprender la library desde lo básico hasta un nivel más avanzado; este es el objetivo principal de este libro.

Ext JS es un framework de vanguardia para crear **Rich Internet Applications (RIAs)**. El framework nos permite crear aplicaciones entre navegadores con un poderoso conjunto de componentes y widgets. La idea detrás del framework es crear aplicaciones fáciles de usar en ciclos de desarrollo rápidos, facilitar el trabajo en equipo (MVC o MVVM) y también tener una capacidad de mantenimiento a largo plazo.

Ext JS ya no es solo una library de widgets; la nueva versión es un framework lleno de nuevas y emocionantes características con las que podemos jugar. Algunas de estas características son el nuevo sistema de clases, el loader, el nuevo paquete de aplicaciones, que define una forma estándar de codificar nuestras aplicaciones, y cosas mucho más asombrosas.

La compañía detrás de la library Ext JS es Sencha Inc. Trabajan en excelentes productos que se basan en estándares web. Algunos de los productos más famosos que también tiene Sencha son **Sencha Touch** y **Sencha Architect**.

En este capítulo, cubriremos los conceptos básicos del framework de la versión 5. Aprenderá cómo configurar la library o SDK y crear nuestro primer programa, conocerá las herramientas disponibles para escribir nuestro código y echar un vistazo en algunas de las nuevas funciones de Ext JS 5.

* Considerando Ext JS para su próximo proyecto
* Introducción a Ext JS: nuestro primer programa
* Herramientas y editores
* ¿Qué hay de nuevo en Ext JS 5?

## Considerando Ext JS para su próximo proyecto

Ext JS es una gran biblioteca para crear RIAs que requieren mucha interactividad con el usuario. Si necesita componentes complejos para administrar su información, entonces Ext es su mejor opción porque contiene muchos widgets como grid, forms, trees, panels y un gran paquete de datos y sistema de clases.

Ext JS es más adecuado para aplicaciones empresariales o de intranet; es una gran herramienta para desarrollar una solución de software CRM o ERP completa. Uno de los ejemplos más atractivos es la muestra de escritorio (http://dev.sencha.com/ext/5.1.0/examples/desktop/index.html)-(https://examples.sencha.com/extjs/7.3.0/). Realmente se ve y se siente como una aplicación nativa que se ejecuta en el navegador. En algunos casos, esto es una ventaja porque los usuarios ya saben cómo interactuar con los componentes y podemos mejorar la experiencia del usuario.

Ext JS 5 salió con una gran herramienta para crear themes y templates de una manera muy simple. El framework para crear temas está construido sobre **Compass** y **Sass**, por lo que podemos modificar algunas variables y propiedades y en unos minutos podemos tener una plantilla personalizada para nuestras aplicaciones Ext JS. Si queremos algo más complejo o único, podemos modificar la plantilla original para adaptarla a nuestras necesidades. Esto puede llevar más tiempo dependiendo de nuestra experiencia con Compass y Sass.

Compass y Sass son extensiones para CSS. Podemos usar expresiones, condiciones, variables, mixins y muchas cosas más increíbles para generar CSS bien formateado. Puede obtener más información sobre Compass en su sitio web en http://compass-style.org/.

El nuevo sistema de clases nos permite definir clases de una manera increíblemente sencilla. Podemos desarrollar nuestra aplicación utilizando el paradigma de programación orientada a objetos y aprovechar las herencias únicas y múltiples. Esto es una gran ventaja porque podemos implementar cualquiera de los patrones disponibles como **MVC**, **MVVM**, Observable o cualquier otro. Esto nos permitirá tener una buena estructura de código, lo que nos lleva a tener un fácil acceso para el mantenimiento.

Otra cosa a tener en cuenta es la creciente comunidad alrededor de la library; Hay muchas personas en todo el mundo que están trabajando con Ext JS en este momento. Incluso puede unirse a los grupos de reuniones que tienen reuniones locales con frecuencia para compartir conocimientos y experiencias; Te recomiendo que busques un grupo en tu ciudad o crees uno.

El nuevo sistema de carga es una excelente manera de cargar nuestros módulos o clases a pedido. Podemos cargar solo los módulos y aplicaciones que el usuario necesite justo a tiempo. Esta funcionalidad nos permite arrancar nuestra aplicación más rápido cargando solo el código mínimo para que nuestra aplicación funcione.

Una cosa más a tener en cuenta es la capacidad de preparar nuestro código para la implementación. Podemos comprimir y ofuscar nuestro código para un entorno de producción utilizando Sencha Cmd, una herramienta que podemos ejecutar en nuestro terminal para analizar automáticamente todas las dependencias de nuestro código y crear paquetes.

La documentación es muy importante y Ext JS tiene una excelente documentación, que es muy descriptiva con muchos ejemplos, videos y código de muestra para que podamos verlo en acción directamente en las páginas de documentación, y también podemos leer los comentarios de la comunidad.

## Empezando con Ext JS

Entonces, ¡comencemos con Ext JS! Lo primero que debemos hacer es descargar el framework del sitio web oficial, http://www.sencha.com/products/extjs/. La versión disponible al momento de escribir este libro es 5.1.1. (*Yo descargue la 7.3.0*)

Hay tres tipos de licencia:

* **The open source license**(La licencia de código abierto): si está creando o desea desarrollar una aplicación de código abierto compatible con la licencia GNU GPL v3 (http://www.gnu.org/copyleft/gpl.html).

* **The commercial license**(La licencia comercial): debe comprarla si planea/desea desarrollar un proyecto de código cerrado y desea mantener el código fuente como propiedad suya. Usualmente utilizado por corporaciones, bancos o empresas.

* **The commercial OEM**(El OEM comercial): si desea usar Ext JS para crear su propio SDK comercial o creador de aplicaciones web, o usarlo como interfaz para algún dispositivo integrado, entonces esto entra en juego. Como este tipo de licencia puede variar, se personaliza para cada cliente.

Puede ver información más detallada sobre este tema en http://www.sencha.com/products/extjs/licensing.

### Descargando Ext JS

Si descarga Ext JS directamente desde http://www.sencha.com/products/download/, esta será una versión de prueba de 30 días de Ext JS y también se le pedirá que ingrese cierta información personal para obtener el trial. Para obtener la versión GPL, puede obtenerla en http://www.sencha.com/legal/GPL/. También podemos usar **Content Delivery Network (CDN)** disponible, como se muestra en la siguiente tabla, para que no necesitemos almacenar la biblioteca en nuestra propia computadora o servidor:

Theme   | Links
--------|------
Classic | * Archivo CSS: http://cdn.sencha.com/ext/trial/5.1.1/packages/ext-theme-classic/build/resources/ext-theme-classic-all.css * Archivo JavaScript: http://cdn.sencha.com/ext/trial/5.1.1/build/ext-all.js
Neptune | * Archivo CSS: http://cdn.sencha.com/ext/trial/5.1.1/packages/ext-theme-neptune/build/resources/ext-theme-neptune-all.css * Archivo JavaScript: http://cdn.sencha.com/ext/trial/5.1.1/build/ext-all.js * Theme JS Overrides: http://cdn.sencha.com/ext/trial/5.1.1/packages/ext-theme-neptune/build/ext-theme-neptune.js
Crisp   | * Archivo CSS: http://cdn.sencha.com/ext/trial/5.1.1/packages/ext-theme-crisp/build/resources/ext-theme-crisp-all.css * Archivo JavaScript: http://cdn.sencha.com/ext/trial/5.1.1/build/ext-all.js * Theme JS Overrides: http://cdn.sencha.com/ext/trial/5.1.1/packages/ext-theme-crisp/build/ext-theme-crisp.js

### Configuración e instalación de Ext JS 5

Después de descargar la biblioteca Ext JS (archivo ZIP), extraiga el contenido a una carpeta de trabajo. Por primera vez, probablemente se sentirá abrumado por el tamaño del archivo ZIP y por la cantidad de archivos y carpetas, pero no se preocupe, el propósito de cada archivo y el contenido de cada carpeta se explicarán en breve.

#### SENCHA CMD

Además de la biblioteca Ext JS, necesitamos descargar Sencha Cmd (herramienta de comando). Esta herramienta está destinada a ser una piedra angular para la creación de aplicaciones, la creación de espacios de trabajo y nuevos temas, y la capacidad de minimizar e implementar nuestras aplicaciones en un entorno de producción.

Descargue esta herramienta en http://www.sencha.com/products/sencha-cmd/ y también verifique que se cumplan los siguientes requisitos para que Sencha Cmd funcione correctamente:

* JRE Sencha Cmd requiere **Java Runtime Environment** versión 1.7 para admitir todas las funciones, sin embargo, la mayoría de las funciones funcionarán con 1.6 (la versión mínima admitida).
* Ruby difiere según el sistema operativo:
   * Windows: descargue Ruby desde http://rubyinstaller.org. Obtenga la versión del archivo `.exe` del software e instálelo.
   * Mac OS: Ruby está preinstalado. Puede probar si Ruby está instalado con el comando `Ruby -v`.
   * SO basado en Linux: use `sudo apt-get install ruby 2.0.0` para descargar Ruby.

Ejecute la configuración de Sencha Cmd, siga las instrucciones y, después de instalar Sencha Cmd, debemos verificar la instalación. Proceda a abrir la línea de comando y escriba el siguiente comando:

```sh
sencha
```

> TIP
>En entornos Windows, se recomienda que reinicie el sistema después de la instalación para que se apliquen las variables de entorno adecuadas.

Después de escribir el comando `Sencha`, deberíamos ver el siguiente resultado:

![01-01](images/01-01.png)

### ¿Por qué tantos archivos y carpetas?

Esta es una pregunta natural cuando miras los archivos y carpetas descargados por primera vez, pero cada archivo y carpeta tiene un propósito y ahora lo vas a aprender:

* La carpeta `build` contiene archivos compilados del SDK y está lista para usarse. Esta carpeta es muy útil para comenzar en Ext JS sin la necesidad de usar Sencha Cmd. A partir de la versión 5, esta carpeta también contiene ejemplos y temas Ext JS listos para usar ubicados en paquetes (carpeta).

* La carpeta `examples` contiene el código fuente de los ejemplos. Estos ejemplos están diseñados para mostrar lo que podemos hacer con la biblioteca. Sin embargo, un cambio significativo en la versión 5 es que esta carpeta debe compilarse usando Sencha Cmd para poder ser deployed/compiled en la carpeta build.

* La carpeta `overrides` contiene archivos JavaScript que se utilizan para agregar funcionalidad y comportamiento adicionales a componentes y widgets y también se utilizan cuando se compila una aplicación o código.

* La carpeta `packages` es donde se encuentran los estilos y las imágenes; también podemos encontrar los archivos Sass para crear nuestro tema personalizado aquí. Sass es una extensión de CSS3 para mejorar el lenguaje; podemos usar variables, mixins, condicionales, expresiones y más con Sass. A partir de la versión 5, esta carpeta también contiene más carpetas, que son `Locales`, `Ext JS Core`, `Charts`, `Aria` y muchas más.

* La carpeta `src` contiene los archivos de código fuente que forman parte del framework. Cada archivo representa una class/object para que podamos leerlo fácilmente, y cada carpeta corresponde al espacio de nombres asignado a la clase. Por ejemplo, la clase `Ext.grid.Panel` está en un archivo llamado `Panel.js`, que en una carpeta llamada `grid (src/grid/Panel.js)`.

* La carpeta `welcome` contiene los estilos e imágenes que se muestran cuando abrimos el archivo `index.html`  en la carpeta `root`.
   
   Si observa la carpeta `root`, también puede ver otros archivos JavaScript. Básicamente, son las versiones comprimidas, depuradas y de desarrollo de la library.

* Los archivos `bootsprap-*.js` contienen información sobre el framework; Estos archivos son utilizados por archivos `ext*.js` para cargar los archivos requeridos (la carpeta `src` o la carpeta `packages`).

* El archivo `ext-all.js` carga la biblioteca completa con todos los componentes, utilidades y clases.

* El archivo `ext-all-debug.js` es el mismo que el archivo `ext-all.js`. La diferencia es que este archivo mostrará los registros de la consola y podemos usar este archivo para depurar nuestra aplicación.

* El archivo `ext.js` es la capa principal y base de Ext JS. Si usamos este archivo, no cargaremos toda la library; este archivo contiene solo el sistema de clases, el loader y algunas otras clases. Podemos usar la clase `Ext.Loader` para cargar solo las clases requeridas y no todo el framework.

#### CARPETAS QUE CAMBIARON EN LA VERSIÓN 5 DE VERSIONES ANTERIORES

Los desarrolladores que usan versiones anteriores de Ext JS pueden encontrar confusa la nueva estructura de carpetas y pueden notar que algunas de las carpetas desaparecieron en la versión 5. Los cambios significativos en las carpetas se enumeran a continuación. La carpeta `builds` ya no existe; en su lugar, deberíamos usar la carpeta `build`.

* La carpeta `locale` se ha movido a la carpeta `packages/ext-locale`. En la versión 5, Locales tiene una estructura de carpetas más compleja y ahora también tenemos el archivo `ext-locale-language.js` y el archivo `ext-locale-language-debug.js`. De forma predeterminada, los componentes se muestran en inglés, pero puede traducirlos a cualquier otro idioma.

* Se eliminó la carpeta `jsbuilder`, ahora en la versión 5 usaremos Sencha Cmd para compilar y comprimir nuestro código fuente.

* El archivo `ext*-dev.js` se eliminó en la versión 5, ya que, según Sencha, había mucha confusión sobre el uso de estos archivos. En Sencha Touch, estos archivos se fusionaron y siguieron el mismo patrón que Sencha Touch en Ext JS. Los archivos `*-dev.js` y `ext*-debug.js` se fusionaron en uno.

* La carpeta `resources` se eliminó, por lo que ahora necesitamos usar la carpeta `packages`.

* La carpeta `docs` se eliminó, por lo que a partir de la versión 5, los desarrolladores deben consultar la documentación y las guías en http://docs.sencha.com/. Además, existe una alternativa para descargar la selección de documentación sin conexión (documentos sin conexión) desde el enlace en el menú de documentación:

![01-02](images/01-02.png)

