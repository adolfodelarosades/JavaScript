# 02 Conceptos Básicos :clock1: 64m

* 03 Introducción a Webpack :clock3: 9:19 
* 04 Instalación de Webpack :clock3: 10:24 
* 05 Primeros pasos: Generar un bundle :clock3: 9:33 
* 06 Nuestro primer `webpack.config` :clock3: 8:28 
* 07 ¿Cómo funciona Webpack? :clock3: 9:55 
* 08 Configuración múltiple :clock3: 5:21 
* 09 Práctica: Configuración múltiple :clock3: 10:19 
* 10 RETO: Instala y configura webpack en un proyecto personal :clock3: 1:00 

## 03 Introducción a Webpack :clock3: 9:19

### Resumen Profesor

#### ¿Qué es Webpack?

Webpack se define a si mismo como un ***Module Bundler***, pero gracias al sistema de plugins que ofrece tambien puede ser considerado como un ***Task Runner***. De tal modo que puede aunar el empaquedado de módulos y la posiblidad de ejecutar tareas como hacen otras librerias como Grunt o Gulp.

#### Sistema de módulos

En JS podemos encontrar los siguientes sistemas de módulos:

* AMD
* Commonjs
* ES2015

En Webpack podemos usarlos todos.

#### Componentes de Webpack

Web se compone de:

* Entry points
* Output
* Loaders
* Plugins

#### Configuración en Webpack

Webpack es conducido mediante ficheros de configuración. Aquí definiremos como transformar los assets, el tipo de output que vamos a generar y además configuraremos los plugins.

#### Hot Module Replacement (HMR)

Nos ofrece una interface para poder actualizar nuestros módulos sin necesidad de efectur una actualización completa de la página.

Webpack DevServer soporta HMR en hot mode.

### Transcripción

Bueno, vamos a empezar la sección de conceptos básicos y vamos a empezar viendo una introducción a Webpack, aquí vamos a ver un una visión general de todo lo que comprende Webpack. 

![03-01](images/03-01.png)

Vamos a ver el índice de los temas que vamos a tratar, vamos a ver que es Webpack evidentemente, hablaremos también de los sistemas de módulos y porque tienen relación con Webpack. Hablaremos de los componentes que tienen Webpack, de cómo se hace la configuración en Webpack y finalmente mencionaremos que es Hot Module Replacement - Reemplazo de Módulos en Caliente y como Webpack soporta esta técnica. 

![03-02](images/03-02.png)

Vamos a empezar con decir que es Webpack, **Webpack es un es un *Module Bundler* o un Empaquetador de Módulo, principalmente es es la tarea que hace**, pero gracias a los plugins, donde la comunidad puede ir desarrollando plugins y tú también puedes desarrollar tus propios plugins, hace las veces de ***Task Runner*** con lo cual puede hacer las mismas tareas que antes tenías que hacer con *Grunt o Gulp* o con librerias similares. 

![03-03](images/03-03.png)

Webpack básicamente funciona de la siguiente forma, con este gráfico vamos a explicar qué es lo que realmente resuelve Webpack. Cuando tenemos una aplicación en el front, tenemos muchos módulos, tenemos módulos en javascript, podemos tener de archivos SASS, archivos CSS, archivos de imágenes, videos, fuentes son muchas cosas que tenemos que empaquetar de alguna forma, entonces aquí en donde entra Webpack. Webpack va recorriendo todos estos módulos a partir de unos unos puntos de entradas que nosotros especificamos, y a través de aquí, va generando un ***árbol de dependencias*** para ir empaquetando todos estos módulos y al final generar ***asserts*** que el navegador puede entender, como pueden ser archivos JS, archivos CSS, imágenes en las diferentes extensiones JPG, PNG, pasando del esquema de la izquierda que son todos los módulos con todas las dependencias, a un esquema que el navegador intérprete y pueda ejecutar. 

![03-04](images/03-04.png)

Ahora vamos a hablar de los sistemas de módulos, Webpack al ser un empaquetado de módulos tienen que soportar diferentes sistemas de módulos, entonces qué sistemas de módulos existen, cuales son los más comunes, los que se utilizan en javascript.

![03-05](images/03-05.png)

El principal, el que se ha utilizado durante mucho tiempo ha sido **AMD** que es una definición de módulos asíncrona, y la librería que implementaba este sistema de módulos y qué más se ha utilizado ha sido **RequiredJS** que hasta hace muy poco todavía se utilizaba. 

También teníamos **CommondJS** que es otro sistema de definir módulos, que es el que utiliza **NodeJS** y luego tenemos la nueva definición de la última especificación **ES2015** que personalmente es la que yo utilizo en mis proyectos. 

![03-06](images/03-06.png)

Aquí, vamos a ver un ejemplo de cómo sería un módulo definido por **AMD** donde definimos el módulo, aquí estamos utilizando la implementación de **RequiredJS**, es muy similar porque la especificación de AMD especifica que los módulos se define así, y abajo se usaría, definimos un módulo y lo estaremos usando como dependencia. 

![03-07](images/03-07.png)

En **CommondJS**, pues es similar, pero utilizamos el `require` esto es como, como funciona NodeJS y cómo se van trayendo las dependencias.

![03-08](images/03-08.png)

Y en el sistema de módulos de la nueva especificación **ES2015**, es como exportábamos una función y aquí la estamos importando hasta esta ruta y luego pues podemos usarlas. 

![03-09](images/03-09.png)

El Webpack soporta todos los sistemas de módulos, podemos ir alternando entre ellos, utilizan solo 1, realmente todo esto es transparente y Webpack es el que se va a encargar de procesarlo y de transformarlo a algo que el navegador puede entender, porque estos sistemas de módulos, el navegador por defecto no los entiendo, hay algunas implementaciones ya que los últimos navegadores ya empiezan a soportar todas las funcionalidades que ofrece ES6 ya empiezan a soportar, pero AMD y CommonJS no son soportadas por defecto por el navegador, con lo cual Webpack cómo lo soporta podemos utilizarlo en nuestros proyecto y se va a encargar de transformarlos.

![03-10](images/03-10.png)

Vamos a hablar ahora de los de los Componentes que tiene Webpack.

![03-11](images/03-11.png)

Empieza todo con los **Entry Points** que son los puntos de entrada donde vamos a especificar nuestro Bootstrap de la aplicación por así decirlo y aquí donde vamos a ir importando los diferentes módulos que vayamos necesitando y aquí es donde Webpack empezara a construir ese grafo de dependencias para generar lo que se conoce como un **Output** que es simplemente el resultado de empaquetar todos esos módulos, puede ser un fichero que comúnmente se llama `Bundler.JS` o pueden ser varios ficheros cosas más avanzadas que ya veremos. 

Después tenemos los **Loaders** que son transformaciones que vamos aplicando sobre los Entry Points o sobre los módulos. 

Luego tenemos los **Plugins** que hacen lo que los Loaders no pueden hacer, van accediendo a todos los estados de la compilación de Webpack y podemos ir haciendo tareas de cualquier cosa, de clean, de generar asserts nuevos, infinidad de cosas que antes normalmente teníamos que utilizar Grunt o Gulp y ahora podemos hacerlo con los Plugins.

![03-12](images/03-12.png)

La configuración en Webpack es uno de los apartados más importantes y es con lo que vamos a estar trabajando en este curso.

![03-13](images/03-13.png)

Webpack es ***Configuration Driver*** o sea, es Conducido por la Configuración, vamos a ver en algunos ejemplos en los que es posible ejecutar Webpack sin necesidad de utilizar la configuración, pero ***no es recomendable realmente***, esto solo se utiliza como juguete, simplemente se utiliza para trastear un poco, realmente para sacarle el poder a Webpack necesitamos utilizar la configuración. Aquí es donde vamos a definir cómo se transforman los ***assets**, el tipo de ***output*** que se va a generar, y nos permite configurar los ***plugings. 

![03-14](images/03-14.png)

Aquí vemos un ejemplo de un archivo de configuración, empezamos a ver cosas interesantes que hemos estado hablando, tenemos los ***Entry Points*** definidos, tenemos los ***Output***, estamos cargando unos ***Loaders***, esta síntesis ya la iremos viendo y ya nos sonará a medida que hagamos todos los ejemplos y bueno también cargamos ***Plugins***. 

![03-15](images/03-15.png)

Finalmente vamos a hablar de **Hot Module Replacement(HMR)**, no es un concepto de Webpack, simplemente que Webpack lo implementa y nos permite sacar las ventajas de el.

![03-16](images/03-16.png)

Básicamente es una de las características más útiles porque nos permite actualizar nuestros módulos en tiempo de ejecución sin necesidad de tener que efectuar un refresco total de la página, esto es muy útil porque nos ayuda a conservar todo el estado de la aplicación sin necesidad de tener que actualizarlo entero. 

![03-17](images/03-17.png)

Las ventajas que nos aporta nos mantiene el estado de la aplicación, nos ahorra tiempo, ya que solo se actualiza lo cambiado, no tenemos que volver a actualizar y a generar toda la aplicación de nuevo, las modificaciones en JS y CSS tienen efecto inmediato en el navegador, es como si estuviésemos programas en la consola de desarrolladores.

![03-18](images/03-18.png)

**Webpack DevServer** soporta HMR en Hot Mode ya veremos cómo activar este modo y aprendemos a configurarlo en este curso. 

![03-19](images/03-19.png)

En resumen Webpack es un empaquetador de módulos y además puede ser usado como ejecutor de tareas como un ***Task Runner***, hace las veces de otras librerias como Grunt o Gulp.  También pasa a través de todo el código para crearse el grafo de dependencias. Soporta los módulos de dependencias de AMD, CommonJS y ES2015. Es Configuration Driver por fichero de configuración, se compone de Entry points, Output, Loaders y Plugins. Soporta HMR mediante DevServer.

## 04 Instalación de Webpack :clock3: 10:24 
## 05 Primeros pasos: Generar un bundle :clock3: 9:33 
## 06 Nuestro primer `webpack.config` :clock3: 8:28 
## 07 ¿Cómo funciona Webpack? :clock3: 9:55 
## 08 Configuración múltiple :clock3: 5:21 
## 09 Práctica: Configuración múltiple :clock3: 10:19 
## 10 RETO: Instala y configura webpack en un proyecto personal :clock3: 1:00 
