# 4. Acerca de los Datos
* Ajax
   * Pasar parámetros a Ajax request
   * Configuración del timeout para las llamadas a Ajax request
* Modelos
    * Mapeos
    * Validadores
    * Tipos de campos personalizados
    * Relaciones
       * Asociaciones One-to-many
       * Asociaciones One-to-one
* Trabajando con store
    * Añadiendo nuevos elementos
    * Recorrer los records/models en el store.
    * Recuperar los records en el store
       * Por posición de índice
       * Primer y último registro
       * Por rango
       * Por ID
    * Eliminación de registros
* Recuperando datos remotos
   * Ajax proxy
   * Readers
      * XML reader(Lector XML)
* Enviando datos
* Resumen

En este capítulo, aprenderemos sobre el uso del data package en Ext JS. Además, hablaremos sobre Ajax, Data Models, Data Stores y los lreaders y writers disponibles que podemos usar para almacenar nuestros datos localmente.

El data package es lo que nos permitirá cargar y guardar datos en nuestro código o aplicaciones. Es importante tener una comprensión sólida del data package para que podamos vincular o vincular datos en componentes Ext JS. El data package contiene varias clases para manejar datos, pero hay algunas clases principales que se utilizarán casi siempre. Eche un vistazo a la siguiente figura:

![04-01](images/04-01.png)

Ext JS crea una capa abstracta con muchas clases y configuraciones; la idea es utilizar estas clases cuando se trata de información. Todos los widgets y componentes que muestran información utilizan el data package para manipular y presentar los datos fácilmente.

> **NOTA**
> 
> Es importante mencionar que se requiere un servidor web para este capítulo y los siguientes. No importa cuál decida usar porque no estamos usando ninguna tecnología específica del lado del servidor.

## Ajax

Antes de comenzar a aprender sobre el data package, es importante saber cómo podemos realizar una solicitud Ajax al servidor. La solicitud Ajax es una de las formas más útiles de obtener datos del servidor de forma **asincrónica**. ***Esto significa que el bucle de JavaScript no se bloquea mientras se ejecuta la solicitud y se disparará un evento cuando el servidor responda; esto nos permite hacer cualquier otra cosa mientras se realiza la solicitud***.

Si eres nuevo en Ajax, te recomiendo que leas más al respecto. Hay miles de tutoriales en línea, pero le sugiero que lea este sencillo artículo en https://developer.mozilla.org/en-US/docs/AJAX/Getting_Started.

Ext JS proporciona un objeto singleton (`Ext.Ajax`) que se encarga de gestionar todos los procesos necesarios para realizar una solicitud en cualquier navegador. Hay algunas diferencias en cada navegador, pero Ext JS maneja estas diferencias por nosotros y nos brinda una solución entre navegadores para realizar solicitudes Ajax.

Hagamos nuestra primera llamada Ajax a nuestro servidor. Primero, necesitaremos crear un archivo HTML e importar la library Ext. Luego, podemos agregar el siguiente código dentro de la etiqueta del script:

```js
Ext.Ajax.request({
   url:"serverside/myfirstdata.json"
});
console.log("Next lines of code...");
```

Usando el método `request`, podemos hacer una llamada Ajax a nuestro servidor. El método `request` recibe un objeto que contiene las configuraciones para la llamada Ajax. La única configuración que tenemos definida es la URL donde queremos realizar nuestra solicitud.

Es importante tener en cuenta que Ajax es asíncrono de forma predeterminada. Esto significa que una vez que se ejecuta el método de solicitud, el motor de JavaScript continuará ejecutando las líneas de código que lo siguen y no esperará hasta que el servidor responda. ***También puede ejecutar Ajax de forma síncrona, estableciendo la propiedad `Ext.Ajax.async = false`***.

> **NOTA**
> 
> Para obtener más detalles, consulte http://docs.sencha.com/extjs/5.1/5.1.1-apidocs/#!/api/Ext.Ajax-cfg-async.

En el código anterior, no hicimos nada cuando el servidor respondió a nuestra solicitud. Para obtener la fecha de respuesta, necesitamos configurar una función `callback` para que se ejecute cuando el servidor responda, y también tenemos funciones para `success` o `failure`. Modifiquemos nuestro ejemplo anterior para configurar esas callbacks:

```js
Ext.Ajax.request({
   url:"serverside/myfirstdata.json",
   success: function(response,options){
      console.log('success function executed, here we can do some stuff !');
   },
   failure: function(response,options){
      Ext.Msg.alert("Message", 'server-side failure with status code ' + response.status);
   },
   callback: function( options, success, response ){
      console.log('Callback executed, we can do some stuff !');
   }
});
```

La función `success` se ejecutará solo cuando el servidor responda con un estado 200-299, lo que significa que la solicitud se ha realizado correctamente. Si el estado de respuesta es 403, 404, 500, 503 y cualquier otro estado de error, se ejecutará el callback `failure`.

Cada función (success o failure) recibe dos parámetros. El primer parámetro es el objeto de respuesta del servidor, donde podemos encontrar el texto de respuesta y los encabezados. El segundo parámetro es la opción de configuración que usamos para esta solicitud Ajax, en este caso el objeto contendrá tres propiedades: la URL y los callbacks `success` y `failure`.

La función `callback` se ejecutará siempre, sin importar si es un success o failure. Además, esta función recibe tres parámetros: `options` es un parámetro para la llamada de solicitud, `success` es un valor booleano según si la solicitud fue exitosa o no, y el parámetro `response` es un objeto `XMLhttpRequest` que contiene la información de la respuesta.

En este punto, tenemos nuestros callbacks configurados, pero todavía no estamos haciendo nada en el interior. Normalmente, necesitamos obtener la respuesta de los datos y hacer algo con ellos; supongamos que obtenemos el siguiente JSON en nuestra respuesta:

```js
{
   "success": true,
   "msg": "This is a success message..!"
}
```

> **TIP**
> 
> En la comunidad Ext JS, uno de los formatos preferidos para enviar y recibir datos al servidor es **JSON**; Ext JS también puede manejar XML. JSON son las siglas de **JavaScript Object Notation**. Si no está familiarizado con JSON, puede visitar http://www.json.org/ para comprender más sobre JSON.
 
Para que la función `success` interactúe con los datos devueltos, necesitamos decodificar los datos JSON devueltos (que vienen en formato de texto) y convertir el texto en un objeto para que podamos acceder a sus propiedades en nuestro código. Cambiemos el siguiente código en el callback `success`:

```js
success: function(response,options){
   var data = Ext.decode(response.responseText);
   Ext.Msg.alert("Message", data.msg);
},
```

Primero obtenemos la respuesta del servidor como un texto usando la propiedad `responseText` del objeto `response`. Luego, usamos el método `Ext.decode` para convertir el texto JSON en objetos JavaScript y guardar el resultado en una variable `data`.

Una vez que tengamos nuestro objeto data con la respuesta del servidor, mostraremos un mensaje de alerta accediendo a la propiedad `msg` desde el objeto data. Tengamos en cuenta que si queremos mostrar algo usando el DOM, necesitamos poner nuestro código dentro del método `onReady` que hemos aprendido en el capítulo anterior.

```js
Ext.Ajax.request({
   url: "serverside/myfirstdata.json ",
   success: function(response,options){
      console.log('success function executed, here we can do some stuff !');
   },
   failure: function(response,options){
      console.log('server-side failure with status code ' + response.status);
   },
   callback: function( options, success, response ){
      if(success){
         var data= Ext.decode(response.responseText);
         Ext.Msg.alert("Message", data.msg);
      }
   }
});
```

> **TIP**
> 
> Es importante que los archivos del lado del servidor devuelvan una respuesta adecuada y sin errores; esto significa que debemos asegurarnos de que los archivos del lado del servidor tengan la sintaxis adecuada y no se muestren advertencias o errores (PHP como ejemplo).
> 
> Además, es importante especificar el Header en el lado del servidor para garantizar el contenido adecuado. Por ejemplo, `header('Content-Type: application/json');`

Si actualizamos su navegador para ejecutar el código que hemos modificado, deberíamos ver algo como la siguiente captura de pantalla:

![04-02](images/04-02.png)


#### 🔴 6️⃣ 💻 Mi versión `910-Learning-Ext-JS-04-01-Ajax-JSON.html`

`miprimerdata.json`

```json
{
   "success" : true,
   "msg"     : "!Este es un mensaje exitoso ...!"
}
```

`miprimerdata.php`

```php
<?php 
header('Content-Type: application/json');
header('Access-Control-Allow-Origin: *');
header("Access-Control-Allow-Headers: X-API-KEY, Origin, X-Requested-With, Content-Type, Accept, Access-Control-Request-Method");
header("Access-Control-Allow-Methods: GET, POST, OPTIONS, PUT, DELETE");
header("Allow: GET, POST, OPTIONS, PUT, DELETE");
$method = $_SERVER['REQUEST_METHOD'];
if($method == "OPTIONS") {
    die();
}

echo '{
   "success" : true,
   "msg"     : "!Este es un mensaje exitoso ...!"
}'; 

?>
```

`910-Learning-Ext-JS-04-01-Ajax-JSON.html`

```html
<!DOCTYPE html>
<html>
   <head>
      <title>Ajax</title>
      <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no"> 
      <link href = "https://cdnjs.cloudflare.com/ajax/libs/extjs/6.0.0/classic/theme-neptune/resources/theme-neptune-all.css" rel = "stylesheet" />
      <script type = "text/javascript" src = "https://cdnjs.cloudflare.com/ajax/libs/extjs/6.0.0/ext-all.js"></script>

      <script type = "text/javascript">
         Ext.onReady(function(){
            Ext.Ajax.request({
            url: "http://familiadelarosa.com/serverside/miprimerdata.php",
            success: function(response,options){
               console.log('Función success ejecutada, ¡aquí podemos hacer algunas cosas!');
            },
            failure: function(response,options){
               console.log('Fallo del lado del servidor con código de estado ' + response.status);
            },
            callback: function( options, success, response ){
               if(success){
                  var data= Ext.decode(response.responseText);
                  Ext.Msg.alert("Mensaje", data.msg);
               }
            }
            });
         });   
      </script>
   </head>
   
   <body style="padding:10px;">  
      
   </body>
</html>
```

En teoría deberiamos usar el archivo `miprimerdata.json` que esta subido en el servidor pero por cuestiones de CORS se usa el archivo `miprimerdata.php` que tiene el manejo del CORS.

![04-12](images/04-12.png)
![04-13](images/04-13.png)
![04-14](images/04-14.png)


Ahora, supongamos que queremos usar XML en lugar de JSON. Crearemos la solicitud de una manera muy similar a nuestro código anterior. El siguiente código debe guardarse en un nuevo archivo en `serverside/data.xml`:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<response success="true">
<msg>This is a success message in XML format</msg>
</response>
```

Luego, procedamos a cambiar la URL y el código en la devolución del callback `success`, de la siguiente manera:

```js
Ext.Ajax.request({
   url: "serverside/myfirstdata.xml",
   success: function(response,options){
      var data = response.responseXML;
      var node = xml.getElementsByTagName('msg')[0];
      Ext.Msg.alert("Message", node.firstChild.data );
   },
   failure: function(response,options){
      Ext.Msg.alert("Message", 'server-side failure with status code ' + response.status);
   }
});
```

Usamos la propiedad `responseXML` para obtener el árbol de nodos y luego obtenemos el nodo con una etiqueta `msg`. Después de eso, podemos obtener el texto real usando la propiedad `firstChild.data` del nodo anterior. Si ejecutamos el código, veremos algo muy similar a nuestro ejemplo anterior con JSON.

Como podemos notar, es más fácil trabajar con JSON. Solo necesitamos decodificar el texto y luego podemos usar los objetos. XML es un poco complicado, pero también podemos usar este formato si nos sentimos cómodos con él.

#### 🔴 6️⃣ 💻 Mi versión `910-Learning-Ext-JS-04-02-Ajax-XML.html`

`miprimerdata.xml`

```xml
<?xml version="1.0" encoding="utf-8"?>
<response success="true">
   <msg>!Este es un mensaje exitoso ...!</msg>
</response>
```

`miprimerdataxml.php`

```php
<?php 
header('Content-Type: application/xml');
header('Access-Control-Allow-Origin: *');
header("Access-Control-Allow-Headers: X-API-KEY, Origin, X-Requested-With, Content-Type, Accept, Access-Control-Request-Method");
header("Access-Control-Allow-Methods: GET, POST, OPTIONS, PUT, DELETE");
header("Allow: GET, POST, OPTIONS, PUT, DELETE");
$method = $_SERVER['REQUEST_METHOD'];
if($method == "OPTIONS") {
   die();
}

echo '<?xml version="1.0" encoding="utf-8"?>
<response success="true">
   <msg>!Este es un mensaje exitoso ...!</msg>
</response>'; 

?>
```

`910-Learning-Ext-JS-04-02-Ajax-XML.html`

```html
<!DOCTYPE html>
<html>
   <head>
      <title>Ajax - XML</title>
      <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no"> 
      <link href = "https://cdnjs.cloudflare.com/ajax/libs/extjs/6.0.0/classic/theme-neptune/resources/theme-neptune-all.css" rel = "stylesheet" />
      <script type = "text/javascript" src = "https://cdnjs.cloudflare.com/ajax/libs/extjs/6.0.0/ext-all.js"></script>

      <script type = "text/javascript">
         Ext.onReady(function(){
            Ext.Ajax.request({
               url: "http://familiadelarosa.com/serverside/miprimerdataxml.php",
               success: function(response,options){
                  var data = response.responseXML;
                  var node = data.getElementsByTagName('msg')[0];
                  Ext.Msg.alert("Mensaje", node.firstChild.data );
               },
               failure: function(response,options){
                  Ext.Msg.alert("Mensaje", 'Fallo del lado del servidor con código de estado ' + response.status);
               }
            });
         });   
      </script>
   </head>
   
   <body style="padding:10px;">  
      
   </body>
</html>
```

![04-15](images/04-15.png)
![04-16](images/04-16.png)
![04-17](images/04-17.png)


### Pasar parámetros a Ajax request

Por lo general, en nuestras aplicaciones necesitamos pasar algunos parámetros a la solicitud Ajax para obtener la información adecuada. Para pasar parámetros usaremos el siguiente código:


```js
Ext.Ajax.request({
  url: "serverside/myfirstparams.php",
  method: 'POST',
  params: {
    x:200,
    y:300
  },
  success: function(response,options){
    var data = Ext.decode(response.responseText);
    Ext.Msg.alert("Message", data.msg);
  },
  failure: function(response,options){
    Ext.Msg.alert("Message", 'server-side failure with status code' + response.status);
    Ext.Msg.alert("Message", 'server-side failure:' + response.status);
  }
});
```

Usando la propiedad **`params`**, podemos establecer un objeto de parámetros. En este caso, enviaremos solo dos parámetros: **`x`** e **`y`**, pero podemos enviar tantos como necesitemos. Observe que establecemos la propiedad **`method`** con el valor **`POST`**; de forma predeterminada, Ext JS usa el valor **`GET`** para esta propiedad, y si usamos **`GET`**, los valores se incrustarán en la URL para la solicitud. Cuando ejecutamos este código, obtendremos la siguiente captura de pantalla:

![04-03](images/04-03.png)

> **TIP**
>
> Tenga en cuenta que puede devolver cadenas en formato HTML (valor de **`msg`** en este caso) para brindar mejoras visuales a la respuesta si está utilizando **`Ext.Msg.alert`**
 
#### 🔴 6️⃣ 💻 Mi versión `910-Learning-Ext-JS-04-03-Ajax-Parametros.html`

`miprimerparametros.php`

```php
<?php
   header('Content-Type: application/json');
   $information = array(
      'success'=>true, 
      'msg'=>'Mensaje de texto de respuesta con los siguientes parámetros:<br><b>x</b>=' . $_POST['x'] . ', <b>y</b>=' . $_POST['y'] . '', 
      'x'=> $_POST['x'],
      'y'=> $_POST['y']	
   );
   echo  json_encode( $information ); 
?>
```

Si cargamos este archivo en el navegador tenemos:

![04-21](images/04-21.png)

`910-Learning-Ext-JS-04-03-Ajax-Parametros.html`

```html
<!DOCTYPE html>
<html>
   <head>
      <title>Ajax - Parámetros</title>
      <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no"> 
      <link href = "https://cdnjs.cloudflare.com/ajax/libs/extjs/6.0.0/classic/theme-neptune/resources/theme-neptune-all.css" rel = "stylesheet" />
      <script type = "text/javascript" src = "https://cdnjs.cloudflare.com/ajax/libs/extjs/6.0.0/ext-all.js"></script>

      <script type = "text/javascript">
         Ext.onReady(function(){
            Ext.Ajax.request({
               url: "http://familiadelarosa.com/serverside/miprimerparametros.php",
               method: 'POST',
               params: {
                  x:200,
                  y:300
               },
               success: function(response,options){
                  var data = Ext.decode(response.responseText);
                  Ext.Msg.alert("Mensaje", data.msg);
               },
               failure: function(response,options){
                  Ext.Msg.alert("Mensaje", 'Fallo del lado del servidor con código de estado: ' + response.status);
                  Ext.Msg.alert("Mensaje", 'Fallo del lado del servidor: ' + response.status);
               }
            });
         });   
      </script>
   </head>
   <body style="padding:10px;">  
      
   </body>
</html>  
```

![04-19](images/04-19.png)

Como vemos tenemos un error por el CORS, pero gracias a esto vemos que pasa cuando existe un fallo `failure`, el cual muestra dos mensajes pero la forma de trabajar solo se muestra el segundo, como vimos en lecciones anteriores los mensajes no son bloqueantes, si comentamos el segundo mensaje nos presenta el primero.

Para solucionar el problema del CORS debemos añadir cabeceras dentro de nuestro archivo PHP, el cual nos queda así:

`miprimerparametros.php`

```php
<?php
   header('Content-Type: application/json');
   header('Access-Control-Allow-Origin: *');
   header("Access-Control-Allow-Headers: X-API-KEY, Origin, X-Requested-With, Content-Type, Accept, Access-Control-Request-Method");
   header("Access-Control-Allow-Methods: GET, POST, OPTIONS, PUT, DELETE");
   header("Allow: GET, POST, OPTIONS, PUT, DELETE");
   $method = $_SERVER['REQUEST_METHOD'];
   if($method == "OPTIONS") {
      die();
   }
  
   $information = array(
      'success'=>true, 
      'msg'=>'Mensaje de texto de respuesta con los siguientes parámetros:<br><b>x</b>=' . $_POST['x'] . ', <b>y</b>=' . $_POST['y'] . '', 
      'x'=> $_POST['x'],
      'y'=> $_POST['y']	
   );
   echo  json_encode( $information ); 
?>
```

La salida es:

![04-20](images/04-20.png)

Como podemos observar el error de CORS a desaparecido y ahora se muestra el mensaje con los parámetros que se le envian vía POST.

### Configuración de timeout para las llamadas a Ajax request

A veces, pero no todo el tiempo, el servidor puede tardar demasiado en responder, por lo que, de forma predeterminada, Ext JS tiene un tiempo configurado de 30 segundos para esperar la respuesta. Según nuestras necesidades, podemos disminuir o aumentar este tiempo estableciendo la propiedad de tiempo de espera en la configuración de la solicitud Ajax. El siguiente ejemplo nos muestra cómo:

```js
Ext.Ajax.request({
  url: "serverside/myfirstparams.php",
  method: 'POST',
  params: {x:200, y:300},
  timeout: 50000,
  success: function(response,options){
    var data = Ext.decode(response.responseText);
    Ext.Msg.alert("Message", data.msg);
  },
  failure: function(response,options){
    Ext.Msg.alert("Message", 'server-side failure with status code ' + response.status);
    Ext.Msg.alert("Message", 'server-side failure:' + response.status);
  }
});
```

Hemos aumentado la propiedad **`timeout`** de espera a 50 segundos (50000 milisegundos); ahora nuestra solicitud se eliminará después de 50 segundos de esperar la respuesta.

> **TIP**
> 
> Puede asignar un valor de tiempo de espera global para toda la configuración de la aplicación, cambiando el valor en **`Ext.Ajax.timeout`** (por defecto tiene el valor de **`30000`**). El ejemplo anterior muestra cómo establecer tiempos de espera en llamadas independientes.

#### 🔴 6️⃣ 💻 Mi versión `910-Learning-Ext-JS-04-04-Ajax-timeout.html`

`910-Learning-Ext-JS-04-04-Ajax-timeout.html`

```html
<!DOCTYPE html>
<html>
   <head>
      <title>Ajax - timeout</title>
      <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no"> 
      <link href = "https://cdnjs.cloudflare.com/ajax/libs/extjs/6.0.0/classic/theme-neptune/resources/theme-neptune-all.css" rel = "stylesheet" />
      <script type = "text/javascript" src = "https://cdnjs.cloudflare.com/ajax/libs/extjs/6.0.0/ext-all.js"></script>

      <script type = "text/javascript">
         Ext.onReady(function(){
            Ext.Ajax.request({
               url: "http://familiadelarosa.com/serverside/miprimerparametros.php",
               method: 'POST',
               params: {x:200, y:300},
               timeout: 50000,
               success: function(response,options){
                  var data = Ext.decode(response.responseText);
                  Ext.Msg.alert("Mensaje", data.msg);
               },
               failure: function(response,options){
                  Ext.Msg.alert("Mensaje", 'Fallo del lado del servidor con código de estado: ' + response.status);
                  //Ext.Msg.alert("Mensaje", 'Fallo del lado del servidor: ' + response.status);
               }
            });
         });   
      </script>
   </head>
   <body style="padding:10px;">  
      
   </body>
</html>
```

La salida es la misma que teniamos antes pero con un pequeño retraso.

![04-22](images/04-22.png)

Si buscamos en la documentación, encontraremos otras configuraciones, como el alcance de las devoluciones de llamada, encabezados, caché, etc. Deberíamos leer los documentos y jugar con esas configuraciones también, pero las que hemos cubierto aquí son las más importantes para aprender.

Ahora sabemos cómo obtener datos usando Ajax, pero también necesitamos una forma de manejar esos datos. Ext JS nos proporciona un paquete de clases para gestionar nuestros datos de forma sencilla; pasemos a nuestro próximo tema.

## Modelos

Los modelos representan objetos o entidades dentro de nuestra aplicación, por ejemplo, Clientes, Usuarios, Facturas, etc. Los data stores utilizarán esos modelos. Podemos definir tantos modelos como necesitemos dentro de nuestra aplicación. 

Un modelo puede contener campos, validaciones y relaciones entre otros modelos. También podemos configurar un proxy para que persista y extraiga nuestros datos.

> **NOTA:**
> 
> A partir de la versión 5.x, las definiciones de campo pueden ser opcionales a menos que necesite conversión, validaciones o establecer un tipo de datos implícito. Para obtener más información, consulte http://docs.sencha.com/extjs/5.1/whats_new/5.0/whats_new.html#Models.
 
Para crear un modelo, escribamos el siguiente código:

```js
Ext.define('Myapp.model.Client',{
extend:'Ext.data.Model',  // step 1
idProperty:'clientId ', // step 2
fields:[// step 3
  {name: 'clientId', type: 'int'},
  {name: 'name'    , type: 'string'},
  {name: 'phone'   , type: 'string'},
  {name: 'website' , type: 'string'},
  {name: 'status'  , type: 'string'},
  {name: 'clientSince', type: 'date', dateFormat:'Y-m-d H:i'}
]
});
```

Como puede notar, estamos definiendo el modelo de la misma manera que definimos una clase; en el paso uno extendemos desde la clase **`Ext.data.Model`**, que es la encargada de agregar toda la funcionalidad a nuestros modelos.

En el segundo paso, estamos definiendo la propiedad en nuestra respuesta JSON que contendrá el ID de cada instancia de registro. En este caso vamos a utilizar el campo **`clientId`**, pero si no definimos la configuración de **`clientId`**, el modelo automáticamente usará y generará una propiedad llamada **`id`** por defecto.

En el tercer paso definimos los campos para nuestro modelo. El valor de esta propiedad es un array; cada elemento del array es un objeto que contiene la configuración de cada campo. En este caso, establecemos el nombre y el tipo de campo, y el último campo (fecha) contiene una propiedad `dateFormat`.

> **NOTA**
> 
> Dependiendo del tipo de campo, podemos agregar algunas propiedades específicas. Por ejemplo, el campo de **`date`**, podemos agregar una propiedad **`dateFormat`**. Para ver más, consulte la documentación en la rama **`Ext.data.field`**.

Los tipos de datos disponibles son los siguientes:

* **`String`**
* **`Integer`**
* **`Float`** (recomendado para usar cuando usa números decimales)
* **`Boolean`**
* **`Date`** (recuerde establecer la propiedad dateFormat para garantizar un análisis de fecha correcto y la interpretación del valor de la fecha)
* **`Auto`** (este campo implica que no se realiza ninguna conversión a los datos recibidos)

Una vez que hayamos definido nuestro modelo, podemos crear un archivo HTML. Importemos la library Ext y nuestro archivo de clase de **`Client`** para probar nuestro modelo de la siguiente manera:

```js
var myclient = Ext.create('Myapp.model.Client',{
  clientId:10001,
  name:'Acme corp',
  phone:'+52-01-55-4444-3210',
  website:'www.acmecorp.com',
  status:'Active',
  clientSince:'2010-01-01 14:35'
});
console.log(myclient);
console.log("My client's name is = " + myclient.data.name);
console.log("My client's website is = " + myclient.data.name);
```

Usando el método **`create`** podemos instanciar nuestra clase de modelo, el segundo parámetro es un objeto con los datos que contendrá nuestro modelo (registro virtual). Ahora, podremos usar los métodos **`get`** y **`set`** para leer y escribir cualquiera de los campos definidos:

```js
// GET METHODS
var nameClient = myclient.get('name');
var websiteClient = myclient.get('website');
console.log("My client's info= " + nameClient + " - " + websiteClient);

// SET Methods
myclient.set('phone','+52-01-55-0001-8888'); // single value
console.log("My client's new phone is = " + myclient.get('phone'));
myclient.set({ //Multiple values
  name: 'Acme Corp of AMERICA LTD.',
  website:'www.acmecorp.net'
});
console.log("My client's name changed to = " + myclient.get("name"));
console.log("My client's website changed to = " + myclient.get("website") );
```

El código anterior muestra cómo leer y escribir nuestros datos. El método **`set`** nos permite modificar un campo, o incluso muchos campos al mismo tiempo, pasando un objeto que contiene los nuevos valores.

Si inspeccionamos la instancia de la **`invoice`** (factura), encontraremos que toda la información se encuentra en una propiedad llamada **`data`**. Siempre debemos usar los métodos **`get`** y **`set`** para leer y escribir nuestros modelos, pero si por alguna razón necesitamos tener acceso a todos los datos en nuestro modelo, podemos usar el objeto **`data`** de la siguiente manera:

```js
//READ
console.log("My client's name:" + myclient.data.name);
console.log("My client's website:" + myclient.data.website);
// Write
myclient.data.name = "Acme Corp ASIA LTD.";
myclient.data.website = "www.acmecorp.biz";
```

Una buena alternativa a este código y una mejor manera de **`get`** y **`set`** datos es:

```js
//READ
console.log("My client's name:" + myclient.get("name"));
console.log("My client's website:" + myclient.get("website"));
// Write
myclient.set("name", "Acme Corp ASIA LTD. ");
myclient.set("website", "www.acmecorp.biz");
```

Podemos leer y escribir cualquier campo en nuestro modelo. Sin embargo, establecer un nuevo valor de esta manera no es una buena práctica en absoluto. El método **`set`** realiza algunas tareas importantes al configurar el nuevo valor, como marcar nuestro modelo como sucio, guardar el valor anterior para que podamos rechazar o aceptar los cambios más tarde, y algunos otros pasos importantes.

### Mapeos

Al definir un campo dentro del modelo, podemos definir dónde se tomarán los datos para un campo con el mapeo de propiedades. Digamos que es una ruta, un nombre alternativo, que Ext JS se utilizará para completar el campo (data) a partir de los datos recibidos del servidor, como un archivo JSON o un archivo XML. Echemos un vistazo al siguiente ejemplo de JSON:

```js
{
  "success" :"true",
  "id":"id",
  "records":[
    {
      "id": 10001,
      "name": "Acme corp2",
      "phone": "+52-01-55-4444-3210",
      "x0001":"acme_file.pdf"
    }

  ]
}
```

Aquí podemos ver en el ejemplo JSON (o quizás XML) que la respuesta viene con un campo con el nombre **`x0001`**. En algunas respuestas puede suceder que el nombre del campo tenga un código especial (según la base de datos o el diseño de los datos), pero en nuestro código, este campo es el archivo de contrato del cliente. Entonces, usando la propiedad de mapeo, podemos poblar el campo, estableciendo la propiedad de mapeo para nuestro campo, como el siguiente ejemplo:

```js
Ext.define('Myapp.model.Client',{
extend: 'Ext.data.Model',
idProperty: 'clientId ',
fields:[
  {name: 'clientId', type: 'int'  },
  {name: 'name'    , type: 'string'},
  {name: 'phone'   , type: 'string'},
  {name: 'contractFileName', type: 'string', mapping:'x0001'}
]
});
```

Como puede ver, estamos definiendo el campo `contractFileName`, que utilizará el campo de datos **`x0001`** de la respuesta; en nuestro código no es necesario hacer referencia a **`x0001`**; simplemente lo manejaremos en nuestro código como **`contractFileName`**. Para verlo en acción, ejecute el archivo **`mapping_01.html`** del código de ejemplo. Abra la ventana de su consola y verá algo similar a la siguiente captura de pantalla:

![04-04](images/04-04.png)

En este momento no es necesario examinar todo el código. Al avanzar en este capítulo, comprenderá todo el código de este ejemplo. El propósito es que comprenda la propiedad de mapeo.

### Validadores

```js
Ext.define('Myapp.model.Client',{
extend:'Ext.data.Model',
idProperty:'clientId ',
fields:[
  {name: 'clientId', type: 'int'  },
  {name: 'name'    , type: 'string'},
  {name: 'phone'   , type: 'string'},
  {name: 'website' , type: 'string'},
  {name: 'status'  , type: 'string'},
  {name: 'clientSince' , type: 'date', dateFormat: 'Y-m-d H:i'}
],
validators:{
  name:[
    { type:'presence'}
  ],
  website:[
    { type:'presence', allowEmpty:true},
    { type:'length',  min: 5, max:250 }
  ]
}
});
```

```js
//Step 1
var myclient = Ext.create('Myapp.model.Client',{
    clientId  : '10001',
    name  : 'Acme corp',
    phone: '+52-01-55-4444-3210',
    website: 'www.acmecorp.com',
    status: 'Active',
    clientSince: '2010-01-01 14:35'
});

if   (myclient.isValid()){  //Step 2
  console.log("myclient model is correct");
}

console.log(myclient);
console.log("My client's name is = " + myclient.data.name);
console.log("My client's website is = " + myclient.data.website);
// SET methods   //Step 3
myclient.set('name','');
myclient.set('website','');
if   (myclient.isValid()){//Step 4
  console.log("myclient model is correct");
} else {
//Step 5
  console.log("myclient model has errors");
  var errors = myclient.validate();
  errors.each(function(error){
    console.log(error.field,error.message);
  });
}
```

> **NOTA:**
> 

![04-05](images/04-05.png)

### Tipos de campos personalizados

```js
Ext.define('Myapp.fields.Status',{
    extend: 'Ext.data.field.String',  //Step 1
    alias: 'data.field.status',//Step 2
    validators: {//Step 3
        type: 'inclusion',
        list: [ 'Active', 'Inactive'],
        message: 'Is not a valid status value, please select the proper options[Active, Inactive]'
    }
});
```

```js
Ext.define('Myapp.model.Client',{
extend:'Ext.data.Model',
idProperty:'clientId ',
fields:[
  {name: 'clientId', type: 'int'  },
  {name: 'name'    , type: 'string'},
  {name: 'phone'   , type: 'string'},
  {name: 'website' , type: 'string'},
  {name: 'status'  , type: 'status'}, //Using custom field
  {name: 'clientSince' , type: 'date', dateFormat: 'Y-m-d H:i'}
],
validators:{
  ...
}
});
```

```js
var myclient = Ext.create('Myapp.model.Client',{
  clientId: '10001',
  name: 'Acme corp',
  phone: '+52-01-55-4444-3210',
  website: 'www.acmecorp.com',
  status: 'Active',
  clientSince: '2010-01-01 14:35'
});
if(myclient.isValid()){
  console.log("myclient model is correct");
}
// SET methods
myclient.set('status','No longer client');
if(myclient.isValid()){
  console.log("myclient model is correct");
} else {
  console.log("myclient model has errors");
  var errors = myclient.validate();
  errors.each(function(error){
    console.log(error.field,error.message);
  });
}
```

> **TIP:**
> 

![04-06](images/04-06.png)

### Relaciones

#### ASOCIACIONES ONE-TO-MANY 

```js
Ext.define('Myapp.model.Client',{
  extend:'Ext.data.Model',  // step 1
  requires: ['Myapp.model.Employee'],
  idProperty:'id ',
  fields:[....  ],
  hasMany:{
    model:'Myapp.model.Employee',
    name:'employees',
    associationKey: 'employees'
  }
});
```

```js
Ext.define('Myapp.model.Employee',{
  extend:'Ext.data.Model',
  idProperty:'id ',
  fields:[
    {name: 'id', type: 'int' },
    {name: 'clientid'  , type: 'int'},
    {name: 'name'      , type: 'string'},
    {name: 'phone'     , type: 'string'},
    {name: 'email'     , type: 'string'},
    {name: 'gender'    , type: 'string'}
  ]
});
```

```js
yee. In order to test our relationship, we need to create an HTML file importing the Ext JS library and our two models. Then, we can test our models as follows:

var myclient = Ext.create('Myapp.model.ClientWithContacts',{
  id: 10001,
  name: 'Acme corp',
  phone: '+52-01-55-4444-3210',
  website: 'www.acmecorp.com',
  status: 'Active',
  clientSince: '2010-01-01 14:35'
});
//Step 2
myclient.employees().add(
{
  id:101, clientId:10001, name:'Juan Perez', phone:'+52-05-2222-333', email:'juan@test.com', gender:'male'},
{
  id:102, clientId:10001, name:'Sonia Sanchez', phone:'+52-05-1111-444', email:'sonia@test.com',gender:'female'}
);
//Step 3
myclient.employees().each(function(record){
  console.log(record.get('name') + ' - ' + record.get('email') );
});
```


#### ASOCIACIONES One-to-one

```js
Ext.define('Myapp.model.Contract',{
  extend:'Ext.data.Model',
  idProperty:'id ',
  fields:[
    {name: 'id', type: 'int' },
    {name: 'contractId', type: 'string'},
    {name: 'documentType', type: 'string'}
  ]
});
As you can see this is a plain model. Now on the Customer class we will define it as follows:

Ext.define('Myapp.model.Customer',{
  extend:'Ext.data.Model',
requires: ['Myapp.model.Contract'],
  idProperty:'id ',
fields:[
  {name: 'id', type: 'int'},
  {name: 'name'    , type: 'string'},
  {name: 'phone'   , type: 'string'},
  {name: 'website' , type: 'string'},
  {name: 'status'  , type: 'string'},
  {name: 'clientSince' , type: 'date', dateFormat: 'Y-m-d H:i'},
  {name: 'contractInfo' , reference: 'Contract', unique:true}
  ]
});
```

```js
var myclient = Ext.create('Myapp.model.Customer',{
  id: 10001,
  name: 'Acme corp',
  phone: '+52-01-55-4444-3210',
  website: 'www.acmecorp.com',
  status: 'Active',
  clientSince: '2010-01-01 14:35',
  contractInfo:{
    id:444,
    contractId:'ct-001-444',
    documentType:'PDF'
  }
});
```

![04-07](images/04-07.png)

![04-08](images/04-08.png)


## Trabajando con store

```js
Ext.define('MyApp.store.Customers',{
  extend : 'Ext.data.Store',        //Step 1
  model  : 'Myapp.model.Customer'  //Step 2
});
```

```js
var store = Ext.create("MyApp.store.Customers");
//counting the elements in the store
console.log(store.count());
```

### Añadiendo nuevos elementos

```js
//Step 1 (define /create new model instance)
var mynewcustomer = Ext.create('Myapp.model.Customer',{
  id: 10001,
  name: 'Acme corp',
  phone: '+52-01-55-4444-3210',
  website : 'www.acmecorp.com',
  status: 'Active',
  clientSince: '2010-01-01 14:35',
  contractInfo:{
    id:444,
    contractId:'ct-001-444',
    documentType:'PDF'
  }
});
store.add(mynewcustomer); //Step 2
console.log("Records in store:" + store.getCount() );
```

```js
//Method 2 for add Records
  store.add({
    id: 10002,
    name: 'Candy Store LTD',
    phone: '+52-01-66-3333-3895',
    website : 'www.candyworld.com',
    status: 'Active',
    clientSince: '2011-01-01 14:35',
    contractInfo:{
      id:9998,
      contractId:'ct-001-9998',
      documentType:'DOCX'
    }
  });
  console.log("Records in store:" + store.getCount());
```

```js
// Method 3 for add multiple records
  var mynewcustomer = Ext.create('Myapp.model.Customer', { ...});
  var mynewcustomerb = Ext.create('Myapp.model.Customer', {
  ...});
  store.add([mynewcustomer, mynewcustomerb]);
  console.log("Records in store:" + store.getCount());
```

### Recorrer los records/models en el store.

```js
store.each(function(record, index){
  console.log(index, record.get("name"));
});
```

### Recuperar los records en el store

#### POR INDEX POSITION

```js
var modelTest = store.getAt(2);
console.log(modelTest.get("name"));
```


#### PRIMER Y ÚLTIMO REGISTRO

```js
var first = store.first();
var last = store.last();
console.log(first.get("name"), last.get("name"));
```

#### POR RANGO

```js
var list = store.getRange(1,3);

Ext.each(list,function(record,index){
  console.log(index,record.get("name"));
});
```

#### POR ID

```js
var record = store.getById(10001);
console.log(modelTest.get("name"));
```

### Eliminación de registros

```js
store.remove(record);
store.each(function(record,index){
  console.log(index,record.get("name"));
});
```

```js
store.remove([first,last]);
store.each(function(record,index){
  console.log(record.get("name"));
});
```

```js
store.removeAt(2);
store.each(function(record,index){
  console.log(index,record.get("name"));
});
```

```js
store.removeAll();
console.log("Records:",store.count());
```

## Recuperando datos remotos

### Ajax proxy

```js
Ext.define('Myapp.store.customers.Customers',{
  extend:'Ext.data.Store',
  model: 'Myapp.model.Customer',
  proxy:{
    type:'ajax',
    url: 'serverside/customers.php',
    reader: {
      type:'json',
      rootProperty:'records'
    }
  }
});
```

```js
//Step 1
  var store = Ext.create("Myapp.store.customers.Customers");
  //Step 2
  store.load(function(records, operation, success) {

    console.log('loaded records');//Step 3
    Ext.each(records, function(record, index, records){
      console.log( record.get("name")  + '  - '  + record.data.contractInfo.contractId );
    });
  });
```

```js
{
  "success":true,
  "id":"id",
  "records":[
    {
      "id": 10001,
      "name": "Acme corp2",
      "phone": "+52-01-55-4444-3210",
      "website": "www.acmecorp.com",
      "status": "Active",
      "clientSince": "2010-01-01 14:35",
      "contractInfo":{
        "id":444,
        "contractId":"ct-001-444",
        "documentType":"PDF"
      }
    },{
      "id": 10002,
      "name": "Candy Store LTD",
      "phone": "+52-01-66-3333-3895",
      "website": "www.candyworld.com",
      "status": "Active",
      "clientSince": "2011-01-01 14:35",
      "contractInfo":{
        "id":9998,
        "contractId":"ct-001-9998",
        "documentType":"DOCX"
      }
    }
  ]
}
```

### Readers

```js
reader: {
  type:'json',
  rootProperty:'records'
}
```

```js
{
  "success" :"true",
  "id":"id",
  "output":{
    "appRecords":[{ our data .... }],
    "customerRecords":[{ our data .... }]
  }
}
```

```js
reader: {
  type:'json',
  rootProperty:'output.customerRecords'
}
```

#### XML READER(LECTOR XML)

```js
proxy:{
    type:'ajax',
    url: 'serverside/customers.xml',
    reader: {
      type: 'xml',
      rootProperty: 'data',
      record:'customer',
      totalProperty: 'total',
      successProperty: 'success'
    }
  }
```

```xml
<?xml version="1.0" encoding="UTF-8"?>
<data>
  <success>true</success>
  <total>2</total>
  <customer>
    <id>10001</id>
    <name>Acme corp2</name>
    <phone>+52-01-55-4444-3210</phone>
    <website>www.acmecorp.com</website>
    <status>Active</status>
    <clientSince>2010-01-01 14:35</clientSince>
    <contractInfo>
      <id>444</id>
      <contractId>ct-001-444</contractId>
      <documentType>PDF</documentType>
    </contractInfo>
  </customer>
  <customer>
    <id>10002</id>
    <name>Candy Store LTD</name>
    <phone>+52-01-66-3333-3895</phone>
    <website>www.candyworld.com</website>
    <status>Active</status>
    <clientSince>2011-01-01 14:35</clientSince>
    <contractInfo>
      <id>9998</id>
      <contractId>ct-001-9998</contractId>
      <documentType>DOCX</documentType>
    </contractInfo>
  </customer>
</data>
```

![04-09](images/04-09.png)


## Enviando datos

```js
Ext.define('Myapp.store.customers.CustomersSending',{
  extend:'Ext.data.Store',
  model: 'Myapp.model.Customer',
  autoLoad:false,
  autoSync:true,
  proxy:{
    type:'ajax',
    url: 'serverside/customers.json',
    api: {
      read    : 'serverside/customers.json',
      create  : 'serverside/process.php?action=new',
      update  : 'serverside/process.php?action=update',
      destroy : 'serverside/process.php?action=destroy'
    },
    reader: {
    ()type:'json',
      rootProperty:'records'
          },
    writer:{
      type:'json',
      encode:true,
      rootProperty:'paramProcess',
      allowSingle:false,
      writeAllFields:true,
      root:'records'
    },
    actionMethods:{
      create: 'POST',
      read: 'GET',
      update: 'POST',
      destroy: 'POST'
    }
  }
});
```

> **NOTA:**
> 

```html
<!doctype html>
<html>
<head>
<meta http-equiv="X-UA-Compatible" content="IE=edge">
<meta charset="utf-8">
<title>Extjs - Sending 01</title>
<link rel="stylesheet" type="text/css" href="../ext-5.1.1/build/packages/ext-theme-neptune/build/resources/ext-theme-neptune-all.css">
<script src="../ext-5.1.1/build/ext-all.js"></script>
<script src="../ext-5.1.1/build/packages/ext-theme-neptune/build/ext-theme-neptune.js"></script>
<script type ="text/javascript" src="sending_01.js"></script>
</head>
<body style="padding:10px;"></body>
</html>
```

```js
Ext.Loader.setConfig({
   enabled: true,
  paths:{ Myapp:'appcode' }
});
Ext.require([
  'Ext.data.*',
  'Myapp.model.Contract',
  'Myapp.model.Customer',
  'Myapp.store.customers.CustomersSending'
]);
Ext.onReady(function(){

var store = Ext.create("Myapp.store.customers.CustomersSending"); //Step 1
  store.load({ // Step 2 load  Store in order to get all records
    scope: this,
    callback: function(records, operation, success) {
      console.log('loaded records');
      Ext.each(records, function(record, index, records){
        console.log( record.get("name")  + '  - '  + record.data.contractInfo.contractId );
      });
      var test=11;
      console.log('Start adding model / record...!');
      // step 3 Add a record
      var mynewCustomer = Ext.create('Myapp.model.Customer',{
        clientId  : '10003',
        name: 'American Notebooks Corp',
        phone: '+52-01-55-3333-2200',
        website   : 'www.notebooksdemo.com',
        status    : 'Active',
        clientSince: '2015-06-01 10:35',
        contractInfo:{
          "id":99990,
          "contractId":"ct-00301-99990",
          "documentType":"DOC"
        }
      });
      store.add(mynewCustomer);

      // step 4 update a record

      console.log('Updating model / record...!');
      var updateCustomerModel = store.getAt(0);
      updateCustomerModel.beginEdit();
      updateCustomerModel.set("website","www.acmecorpusa.com");
      updateCustomerModel.set("phone","+52-01-33-9999-3000");
      updateCustomerModel.endEdit();

      // step 5 delete  a record
      console.log('deleting a model / record ...!');

      var deleteCustomerModel = store.getAt(1);
      store.remove(deleteCustomerModel);

    }
  });
});
```

![04-10](images/04-10.png)

## Resumen



