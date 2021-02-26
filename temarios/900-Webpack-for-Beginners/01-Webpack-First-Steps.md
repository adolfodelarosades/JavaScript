# Chapter 1: Webpack: First Steps

* Installing Webpack
* Webpack 4 Zero Config
* The Bundling Command
* Summary

En este primer capítulo, comenzaremos por sentar las bases de nuestro trabajo instalando las herramientas que necesitamos para ejecutar webpack en nuestra máquina local. Luego hablaremos un poco sobre la configuración predeterminada que ha introducido webpack con la versión 4, llamada "configuración cero". A continuación, escribiremos nuestro primer ejemplo de “hola mundo”, que como ya sabrá, es un estándar obligatorio cuando se comienza a aprender algo nuevo. Finalmente, hablaremos muy brevemente sobre el comando de empaquetado del paquete web que usaremos para construir nuestros archivos de salida finales.

## Instalación de Webpack

En primer lugar, debe tener Node JS instalado en su máquina porque webpack se basa en él. Si no tiene Node instalado, puede ir a https://nodejs.org/en/download/ y seguir las instrucciones según su sistema operativo.

Para verificar si tiene Node JS en su sistema, abra la terminal y escriba lo siguiente:

```sh
$ node -v
```

El siguiente paso después de asegurarnos de que Node JS esté instalado en nuestra máquina es crear nuestro directorio/carpeta de trabajo, que llamaremos "webpack_beginners". Dependiendo de su preferencia, es posible que lo haya creado manualmente o mediante un terminal como el siguiente:

```sh
$ mkdir webpack_beginners
$ cd webpack_beginners
```

Una vez que esté en la carpeta webpack_beginners, use el siguiente comando para iniciar un archivo JSON básico:

```sh
$ npm init -y
```

Esto creará un archivo llamado package.json que guardará referencias a nuestros módulos instalados.

A través de `npm`, la opción `-y` es responder sí a todas las preguntas solicitadas; no es tan importante para nosotros en esta etapa, así que simplemente diremos que sí a todo.

Si abre el archivo `package.json` generado, verá algo similar a lo que se muestra en el Listado 1-1.

```js
{
  "name": "webpack_beginners",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC"
}
```
***Listado 1-1*** `package.json`: Un archivo JSON básico generado 

El archivo `package.json` servirá para que NPM identifique nuestro proyecto (nombre, versión, autor, archivo de entrada principal ...) y maneja las dependencias de terceros necesarias para que sea completamente funcional. Suponiendo que está creando una biblioteca JS que desea compartir en GitHub, etc., es posible que le interese cambiar el nombre y la versión anteriores, y tal vez escribir una descripción también. Pero ese no es nuestro enfoque aquí, para ver más de lo que este archivo `package.json` hará por nosotros, instalemos webpack usando nuestra línea de comando:

```sh
$ npm install webpack webpack-cli --save-dev
```

Tenga en cuenta que, ya sea que esté en Linux, Mac o Windows, el comando es básicamente el mismo, asumiendo que ya tiene NPM instalado en su máquina, lo que ocurre principalmente si siguió la instalación de Node JS correctamente. La opción `--save-dev` es decirle a NPM que necesitamos esto solo para nuestros propósitos de desarrollo, lo que significa que estos paquetes se instalarán solo en nuestra máquina local.

El comando anterior nos instalará webpack con su propia CLI (interfaz de línea de comandos). Una vez que finalice el comando de instalación, abra el archivo `package.json` y debería ver algo similar a lo que se muestra en la Figura 1-1.

![01-01](images/01-01.png)

***Figura 1-1*** El archivo json del paquete después de instalar webpack y webpack-cli

Observe que webpack y webpack-cli se agregaron con la versión de cada uno en `devDependencies`. También observe que se creó una nueva carpeta llamada `node_modules`, así como otro archivo llamado `package-lock.json`.

Entonces, por un lado, además de las propiedades básicas generadas (que hemos visto anteriormente) como el nombre del proyecto, versión, autor, etc., `package.json` enumera todos los paquetes de los que depende directamente su proyecto, lo que significa que siempre instalas un nuevo paquete desde tu terminal, ese nombre de paquete y número de versión se agregarán a `package.json`. El `package-lock.json`, por otro lado, es la representación completa del árbol de dependencias de su proyecto, incluidas las dependencias indirectas. Por ejemplo, cuando instala webpack, también se instalarán otros paquetes de los que depende. `Package-lock.json` también contendrá la versión específica de cada módulo, de modo que si alguien tomó su proyecto más tarde y ejecutó `"npm install"` en su máquina, obtendrá exactamente las mismas versiones que usted instaló. De esa manera, no habrá fallas en la aplicación (es decir, debido a un paquete que se actualizó y tiene algunos cambios de ruptura).

Ahora que tenemos nuestro paquete web instalado, intentemos abrir la carpeta `node_modules` y ubicar nuestro paquete webpack. La Figura 1-2 muestra la ubicación exacta, que se encuentra en `"node_modules/.bin"`.

![01-02](images/01-02.png)

***Figura 1-2*** El archivo `"node_modules/.bin/webpack"` responsable de ejecutar el comando webpack

El archivo `"webpack"` de arriba (en `"node_modules/.bin"`) es de donde viene el "comando Webpack", así que cada vez que necesitemos compilar nuestro JavaScript, llamaremos a este archivo desde nuestra terminal. Sin embargo, hay una mejor manera de hacer esto (que veremos en la siguiente sección) creando un comando de alias que llamará a ese archivo por nosotros en lugar de especificar la ruta. Con eso en mente, es hora de escribir un código básico y comenzar a explorar el poder de webpack.

<hr>

## Webpack 4 Zero Config

Si alguna vez usó webpack 3 antes, sabe que debe crear un archivo de configuración llamado `webpack.config.js` para indicarle a webpack dónde están sus archivos, qué hacer con ellos y dónde generar el resultado. Webpack 4, por defecto, ahora tiene configuración cero, aquí está la cita del sitio web oficial de webpack:

> *Configuración*

> *Fuera de la caja, webpack no requerirá que uses un archivo de configuración. Sin embargo, asumirá que el punto de entrada de su proyecto es `src/index` y generará el resultado en `dist/main.js` minificado y optimizado para producción.*

> Fuente: https://webpack.js.org/configuration/

Lo que esto significa es que webpack espera que cree un archivo de entrada llamado `index.js` dentro de la carpeta `src`, y luego creará y generará el resultado en `dist/main.js` por usted, sin la necesidad de crear el archivo de configuración usted mismo o hacer cualquier otra cosa.

Asumiré que siempre está dentro de la carpeta que creamos en primer lugar (la que llamamos "webpack_beginners"). Así que ahora creemos una carpeta llamada `src` y también un archivo `index.js` dentro de ella. En la Figura 1-3, puede ver una captura de pantalla de cómo se ve mi árbol de carpetas.

![01-03](images/01-03.png)

***Figura 1-3*** Nuestro árbol de carpetas `"webpack"` después de agregar una carpeta `"src"` y un archivo `index.js`

En `index.js`, escriba un primer alert de saludo:

```js
alert('Hello Webpack World !');
```

Guarde el archivo y, en su terminal/consola, ejecute:

```sh
$ node_modules/.bin/webpack
```

Lo que hicimos aquí fue decirle a webpack que agrupe nuestro JS. Si se pregunta qué es un node_modules / .bin / webpack, es solo la ruta a nuestro comando webpack, que es básicamente un archivo JavaScript. Hay una mejor manera de llamarlo con seguridad, y lo veremos en unos momentos.

Después de decirle a webpack que agrupe nuestro JavaScript, `node_modules/.bin/webpack` y comenzará desde allí, después de ejecutar el comando webpack en su terminal. Obtendrá una salida similar a la que se muestra en la Figura 1-4.

![01-04](images/01-04.png)

***Figura 1-4*** Salida del terminal de ejecutar el comando `“node_modules/.bin/webpack”`

Como puede ver en la salida, webpack especifica lo que se creó para nosotros como resultado (un archivo llamado `main.js`); También observe una advertencia en la parte inferior que dice lo siguiente:

* WARNING in configuration.

* La opción "mode" no se ha configurado, por lo que el paquete web recurrirá a "production" para este valor. Establezca la opción "mode" en 'development' o 'production' para habilitar los valores predeterminados para cada entorno.

* También puede configurarlo en 'none' para deshabilitar cualquier comportamiento predeterminado. Obtenga más información en https://webpack.js.org/configuration/mode/

Esto simplemente significa que aún no le hemos dicho al paquete web en qué modo estamos trabajando (desarrollo o producción), como resultado, el respaldo se establece automáticamente en producción, por lo que decide que nuestro JavaScript debe minimizarse. Para deshacernos de esa advertencia anterior, agregaremos una bandera `--mode=production` cuando llamemos al comando webpack de esta manera:

```sh
node_modules/.bin/webpack --mode=production
```

Una vez finalizada la compilación, echemos un vistazo a nuestro editor de texto (o IDE, según lo que utilice) y veamos lo que tenemos en la Figura 1-5.

![01-05](images/01-05.png)

***Figura 1-5*** `main.js`: el archivo generado por webpack en la carpeta `dist`

Webpack creó un archivo `dist/main.js` para nosotros y también comprimió nuestro código, ¡pero espere un minuto! ¿No ve que nuestro `alert ('Hello Webpack World !')` Se transformó en un código extraño? Quiero decir que se le agregan más cosas. Envuelva el código en nuestro editor de texto y observemos con zoom, como se muestra en la Figura 1-6.

![01-06](images/01-06.png)

***Figura 1-6*** Nuestro `“Hello webpack world”` envuelto en su propio módulo

Si se dio cuenta, nuestra alert está en la parte inferior, pero puede ver que hay un montón de código que la precede, por lo que no tiene que preocuparse ni comprender porque es específico de webpack y cómo hace que los módulos requieran funcional.

El siguiente paso es crear un archivo HTML y hacer un link a nuestro `dist/main.js` para ver si todo funciona bien.

Continúe y cree un archivo `index.html` en la raíz de nuestra carpeta webpack_beginners y rellénelo con el código que ve en el Listado 1-2.

```html
<!DOCTYPE html>
<html lang="en" dir="ltr">
  <head>
    <meta charset="utf-8">
    <title></title>
  </head>
  <body>
  <script type="text/javascript" src="dist/main.js"></script>
  </body>
</html>
```
***Listado 1-2*** `index.html`: haciendo referencia a nuestro archivo `dist/main.js`

Guarde el archivo y ábralo en su navegador. Sí, el código está funcionando y aparece su primer `“Hello Webpack World”`. Vea la Figura 1-7.

![01-07](images/01-07.png)

***Figura 1-7*** Su primer alert `“Hello world”`

Si bien este es un ejemplo muy básico de nuestro primer archivo JavaScript bundled(funcional) incluido en el webpack, ¡es hora de felicitarse! Lo hiciste y deberías estar orgulloso de haber dado tu primer paso en el mundo de los webpack. Pero antes de pasar a cosas más serias, hablemos un poco sobre el comando de empaquetado y cómo podemos usarlo de una manera más amigable para decirle a webpack que compile nuestro JavaScript.

<hr>

## El Comando Bundling

Como ya mencioné, antes de pasar al siguiente capítulo, quiero hablar sobre el comando webpack que usamos antes de “node_modules/.bin/webpack”, ya que podría parecer que es una forma fea de hacerlo, y seguro que no es una mejor manera. Lo que puede hacer es abrir su archivo `package.json` y buscar debajo de los scripts, que se ven así:

```js
"scripts": {
  "test": "echo \"Error: no test specified\" && exit 1"
}
```

Quite la línea:

```js
"test": "echo \"Error: no test specified\" && exit 1"
```

Y reemplázalo con este:

```js
"build": "webpack --mode=production"
```

Entonces se verá así:

```js
"scripts": {
  "build": "webpack --mode=production"
}
```

En la línea "script" que agregamos anteriormente a nuestro `package.json`, no es necesario especificar la ruta exacta al archivo webpack como lo hicimos en nuestra terminal porque sabrá dónde encontrarlo. Ahora en lugar de llamar:

```sh
$ node_modules/.bin/webpack
```

Usaremos nuestro comando personalizado:

```sh
$ npm run build
```

Esto buscará un comando webpack en la carpeta `node_modules` y lo llamará por nosotros. Tenga en cuenta que puede nombrar su secuencia de comandos como desee. No necesariamente tiene que ser `"build"`. Puede, por ejemplo, nombrarlo `"dev"` y luego llamarlo desde su terminal de la siguiente manera:

```sh
$ npm run dev
```

Entonces, como sea que lo nombre, debe llamarlo con su nombre, pero encontrará que la mayoría de la gente generalmente usa `"build"` o `"dev"` en el mundo webpack.

<hr>

## Resumen

En este capítulo, presentamos los comandos necesarios para instalar webpack en nuestra máquina. Hemos visto el archivo `package.json` y lo que básicamente hace. Luego creamos nuestro primer archivo JavaScript y lo empaquetamos con webpack. Además, exploramos el archivo de entrada y cómo se debe nombrar para que la configuración cero de webpack funcione correctamente. Además, hemos aprendido a ejecutar el comando webpack desde nuestra terminal.
