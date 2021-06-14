# 23. All About JSON (aka JavaScript Object Notation)

* What Is JSON?
* Looking Inside a JSON Object
* Reading JSON Data
* Writing JSON Data?


En este capítulo

* Comprender las funciones anónimas
* Aprenda a invocar un bloque de código inmediatamente
* Lleve nuestro conocimiento del alcance más allá mediante la creación de datos privados.

Cuando se trata de almacenar, recuperar o transmitir datos, hay un montón de formatos de archivo y estructuras de datos que puede utilizar. Probablemente haya utilizado archivos de texto, documentos de Word, hojas de cálculo de Excel, archivos zip, etc. para tratar los distintos tipos de datos que maneja. En el frente web, hay un formato que reina sobre todos los demás. Corre más rápido. Salta más alto. Tiene un pelaje más brillante (y más peludo). Ese formato se conoce como **JSON**, abreviatura de **JavaScript Object Notation**.

En este artículo, aprenderemos todo sobre lo que hace que los objetos JSON sean increíbles. Veremos en detalle lo que contienen y cómo puede leer valores de ellos como parte de sus propias implementaciones.

¡Adelante!

## ¿QUÉ ES JSON?

En JavaScript, tiene una forma de definir objetos utilizando la sintaxis literal de objeto:

```js
let funnyGuy = {
  firstName: "Conan",
  lastName: "O'Brien",

  getName: function () {
    return "Name is: " + this.firstName + " " + this.lastName;
  }
};

let theDude = {
  firstName: "Jeffrey",
  lastName: "Lebowski",

  getName: function () {
    return "Name is: " + this.firstName + " " + this.lastName;
  }
};

let detective = {
  firstName: "Adrian",
  lastName: "Monk",

  getName: function () {
    return "Name is: " + this.firstName + " " + this.lastName;
  }
};
```

Si no está familiarizado con esta sintaxis, le recomiendo que lea más sobre ella en el artículo [Deeper Look at Objects article](https://www.kirupa.com/html5/a_deeper_look_at_objects_in_javascript.htm) - Un análisis más profundo de los objetos. ¡Hará que la comprensión y el trabajo con objetos JSON sean significativamente más fáciles!

En la superficie, la sintaxis literal del objeto parece un montón de corchetes, dos puntos y llaves extrañas que definen las propiedades y los valores de su objeto. A pesar de lo extraño que parece, bajo las sábanas, es bastante descriptivo. Muchos de los tipos de datos comunes que le gustaría utilizar están disponibles. Puede representar claramente sus propiedades y valores como pares de clave y valor separados por dos puntos. Igual de importante que todas las demás cosas que acabo de mencionar, esta sintaxis le permite tener estructura y valores anidados. En general, es una forma bastante agradable de representar objetos JavaScript ... ¡en una representación literal!

El formato JSON se basa en gran medida en la sintaxis literal de este objeto. Aquí hay un ejemplo de algunos datos JSON reales honestos devueltos por la [API WeatherUnderground](https://www.wunderground.com/) para mostrar el clima en mi ciudad natal de Seattle:

```json
{
  "response": {
    "version": "0.1",
    "termsofService":
"http://www.wunderground.com/weather/api/d/terms.html",
    "features": {
      "conditions": 1
    }
  },
  "current_observation": {
    "image": {
      "url": "http://icons.wxug.com/graphics/wu2/logo_130x80.png",
      "title": "Weather Underground",
      "link": "http://www.wunderground.com"
    },
    "display_location": {
      "full": "Seattle, WA",
      "city": "Seattle",
      "state": "WA",
      "state_name": "Washington",
      "country": "US",
      "country_iso3166": "US",
      "zip": "98101",
      "magic": "1",
      "wmo": "99999",
      "latitude": "47.61167908",
      "longitude": "-122.33325958",
      "elevation": "63.00000000"
    },
    "observation_location": {
      "full": "Herrera, Inc., Seattle, Washington",
      "city": "Herrera, Inc., Seattle",
      "state": "Washington",
      "country": "US",
      "country_iso3166": "US",
      "latitude": "47.616558",
      "longitude": "-122.341240",
      "elevation": "121 ft"
    },
    "estimated": {},
    "station_id": "KWASEATT187",
    "observation_time": "Last Updated on August 28, 9:28 PM PDT",
    "observation_time_rfc822": "Fri, 28 Aug 2015 21:28:12 -0700",
    "observation_epoch": "1440822492",
    "local_time_rfc822": "Fri, 28 Aug 2015 21:28:45 -0700",
    "local_epoch": "1440822525",
    "local_tz_short": "PDT",
    "local_tz_long": "America/Los_Angeles",
    "local_tz_offset": "-0700",
    "weather": "Overcast",
    "temperature_string": "68.0 F (20.0 C)",
    "temp_f": 68.0,
    "temp_c": 20.0,
    "relative_humidity": "71%",
    "wind_string": "Calm",
    "wind_dir": "NNW",
    "wind_degrees": 331,
    "wind_mph": 0.0,
    "wind_gust_mph": "10.0",
    "wind_kph": 0,
    "wind_gust_kph": "16.1",
    "pressure_mb": "1008",
    "pressure_in": "29.78",
    "pressure_trend": "-",
    "dewpoint_string": "58 F (15 C)",
    "dewpoint_f": 58,
    "dewpoint_c": 15,
    "heat_index_string": "NA",
    "heat_index_f": "NA",
    "heat_index_c": "NA",
    "windchill_string": "NA",
    "windchill_f": "NA",
    "windchill_c": "NA",
    "feelslike_string": "68.0 F (20.0 C)",
    "feelslike_f": "68.0",
    "feelslike_c": "20.0",
    "visibility_mi": "10.0",
    "visibility_km": "16.1",
    "solarradiation": "--",
    "UV": "0",
    "precip_1hr_string": "0.00 in ( 0 mm)",
    "precip_1hr_in": "0.00",
    "precip_1hr_metric": " 0",
    "precip_today_string": "0.00 in (0 mm)",
    "precip_today_in": "0.00",
    "precip_today_metric": "0",
    "icon": "cloudy",
    "icon_url": "http://icons.wxug.com/i/c/k/nt_cloudy.gif",
    "nowcast": ""
  }
}
```

Ignorando el tamaño de los datos devueltos, existen muchas similitudes entre los datos JSON que ve y la sintaxis literal del objeto que vio anteriormente. Hay algunas diferencias importantes que también debes conocer, pero veremos todas esas cosas aburridas más adelante. Primero, echemos un vistazo más profundo a qué constituye exactamente un objeto JSON.

## MIRAR DENTRO DE UN OBJETO JSON

Un objeto JSON no es más que una combinación de nombres de propiedad y sus valores. Parece bastante simple, pero hay algunos detalles importantes que debemos repasar en esta sección.

### Nombres de Propiedad

Los nombres de propiedad son los identificadores que utilizará para acceder a un valor. Visualmente, son las cosas a la izquierda del carácter de dos puntos:

```json
{
  "firstName": "Kirupa",
  "lastName": "Chinnathambi",
  "special": {
    "admin": true,
    "userID": 203
  },
  "devices": [
    {
      "type": "laptop",
      "model": "Macbook Pro 2015"
    },
    {
      "type": "phone",
      "model": "iPhone 6"
    }
  ]
}
```

En este fragmento de código JSON, los nombres de propiedad son **`firstName`**, **`lastName`**, **`special`**, **`admin`**, **`userID`**, **`devices`**, **`type`** y **`model`**. Observe cómo se definen los nombres de las propiedades. Son valores de cadena entre comillas. Las comillas son un detalle importante que no tiene que especificar en el caso literal del objeto para los nombres de propiedad, así que no olvide incluirlos cuando trabaje en el mundo JSON.

### Los Valores

Cada nombre de propiedad se asigna a un valor y los tipos de valores que puede tener son:

* Numbers
* Strings
* Booleans (true or false)
* Objects
* Arrays
* Null

Asignemos estos diversos tipos al ejemplo que acabamos de ver anteriormente.

#### Strings

Los valores Strings son las siguientes líneas resaltadas:

![image](https://user-images.githubusercontent.com/23094588/121819952-46cb0800-cc90-11eb-8a3f-2ff83f82a8bd.png)

Las comillas dobles son un claro indicio de que estos valores son cadenas. Además de sus letras, números y símbolos habituales, también puede incluir **escape characters - caracteres de escape** como `\'`, `\"`, `\\`, `\/`, etc. para definir caracteres en su cadena que, de otro modo, se analizarían como una operación JSON.

### Numbers

Nuestro único representante de la familia de números es el valor de la propiedad `userID`:

![image](https://user-images.githubusercontent.com/23094588/121820019-ba6d1500-cc90-11eb-94f1-4bc9dab654d3.png)

Puede especificar tanto valores decimales (por ejemplo: **0.204**, **1200.23**, **45**) como valores exponenciales (**2e16**, **3e+4**, **1.5e-2**). Sin embargo, hay algunas peculiaridades que debes tener en cuenta. No puede prefijar su número con un 0 seguido de otro número. Por ejemplo, ***no se permite un valor de 03.14***.

### Booleans

Los valores booleanos son fáciles:

![image](https://user-images.githubusercontent.com/23094588/121820137-61ea4780-cc91-11eb-8a59-3e4c5dd38163.png)

Los valores pueden ser **true** o **false**. Una cosa a tener en cuenta: las mayúsculas son importantes. Tanto el **true** y **false** deben estar en minúsculas. Está prohibido usar mayúsculas y minúsculas (**true** o **false**) o en mayúsculas (**TRUE** o **FALSE**).

### Objects

Aquí es donde las cosas se ponen un poco interesantes:

![image](https://user-images.githubusercontent.com/23094588/121820249-1be1b380-cc92-11eb-9d86-87173843ed6f.png)

Los objetos contienen una colección de nombres y valores de propiedad, y están separados del resto de su contenido, con llaves. ¿Ver? ¿No fue un poco interesante?

### Arrays

Nuestra propiedad `devices` representa un array:

![image](https://user-images.githubusercontent.com/23094588/121820344-91e61a80-cc92-11eb-8153-6f73a1d32f97.png)

Los Arrys almacenan una colección ordenada de cero o más valores que puede recorrer en iteración, y están separados por la notación de corchetes. Dentro de un array, puede usar cualquiera de los tipos JSON que hemos visto hasta ahora ... ¡incluidos otros arrays!

### Null

El último tipo de datos también es el más aburrido:

```json
{
  "foo": null
}
```

Tus valores JSON pueden ser **null**. Esto representa un valor vacío.

## LEER DATOS JSON

Lo admito. La sección anterior fue extremadamente aburrida, ¡pero hay buenas noticias! Dado lo aburrido que fue lo que acaba de ver, esta sección, en comparación, parecerá mucho más emocionante de lo que realmente es. ¡Hurra!

De todos modos, casi todas sus interacciones con JSON girarán en torno a la lectura de datos. Cuando se trata de leer datos JSON, lo principal a tener en cuenta es que es muy similar a leer valores almacenados dentro de un objeto JavaScript típico. Puede colocar un punto en el valor que desee (`propiedad.propertyFoo`) o puede usar el enfoque de array (`property["propertyFoo"]`) y acceder al valor de esa manera.

Para ayudar a explicar todo esto, usemos el siguiente ejemplo:

```json
let exampleJSON = {
  "firstName": "Kirupa",
  "lastName": "Chinnathambi",
  "special": {
    "admin": true,
    "userID": 203
  },
  "devices": [
    {
      "type": "laptop",
      "model": "Macbook Pro"
    },
    {
      "type": "phone",
      "model": "iPhone XS"
    }
  ]
};
```

Para leer el valor almacenado por `firstName`, puede realizar una de las siguientes acciones:

```js
exampleJSON.firstName;
exampleJSON["firstName"];
```

Ambas líneas devolverán un valor de **Kirupa**. No hay una respuesta correcta o incorrecta sobre si desea utilizar el enfoque de notación de puntos o el enfoque de array para acceder al valor que le interesa. Use lo que le resulte cómodo, pero mi preferencia personal es usar la notación de puntos. Pasar nombres de propiedades como cadenas me da náuseas, por lo que solo resaltaré el enfoque de notación de puntos en los fragmentos de código que verá.

Similar a lo que vio anteriormente, para acceder al valor almacenado por `lastName`, puede hacer esto:

```js
exampleJSON.lastName;
```

Para propiedades simples que almacenan valores simples, la vida es bastante simple. La única complicación MUY menor con la que se encontrará es cuando trabaje con valores más complejos compuestos por Objects y Arrays. Para leer un valor almacenado dentro de un Objeto, simplemente siga punteando en cada propiedad hasta que llegue a la propiedad que almacena el valor que le interesa.

Así es como se verá intentar acceder al valor almacenado por la propiedad `userID`:

```json
exampleJSON.special.userID;
```

Los Arrays no son diferentes, pero eventualmente tendrá que cambiar a la notación de array  una vez que llegue a la propiedad que almacena los valores de su array. Si quisiéramos acceder al valor del modelo del primer dispositivo en el array de dispositivos, podemos escribir algo que se vea de la siguiente manera:

```json
exampleJSON.devices[0].model;
```

Debido a que la propiedad `devices` se refiere a un array, también puede realizar operaciones estereotipadas similares a un array, como las siguientes:

```js
let devicesArray = exampleJSON.devices;

for (let i = 0; i < devicesArray.length; i++) {
  let type = devicesArray[i].type;
  let model = devicesArray[i].model;

  // do something interesting with this data!
}
```

Para reiterar lo que vio en la sección anterior, sus valores JSON pueden ser strings, numbers, objects, arrays, booleans, o nulls. Todo lo que JavaScript admite para un tipo de datos determinado que encuentre dentro de su objeto JSON, puede aprovecharlo fácilmente.

## Parsing JSON-looking Data into Actual JSON - Analizar datos de aspecto JSON en JSON real

En nuestro ejemplo, teníamos nuestros datos JSON claramente definidos dentro de la variable `exampleJSON`. No hay duda en la mente de nadie de que lo que estamos tratando es de un objeto JS real que se representa mediante la semántica JSON.

Con escenarios del mundo real, ese no siempre será el caso. Sus datos JSON pueden provenir de una variedad de fuentes diferentes, y no todas devolverán los datos JSON en este formato viable que vimos. Muchos devolverán datos JSON como texto sin formato. Tendrá algo que parece un objeto JSON, pero no podrá interactuar con los datos como lo haría cuando trabaja con un objeto JSON real.

Para lidiar con esto, tiene el método **`JSON.parse`** que toma sus datos JSON "falsos" como argumento:

![image](https://user-images.githubusercontent.com/23094588/121872626-c9da7580-cd05-11eb-96c0-e5e81cfabfa6.png)

Como puede ver en nuestra línea resaltada, este método toma cualquier dato de aspecto JSON con el que termine y lo convierte en un objeto JSON real con el que puede trabajar más fácilmente. Siempre que trabajo con datos JSON de una fuente externa, siempre uso `JSON.parse` solo para estar seguro.

## ESCRIBIR DATOS JSON?

Acabamos de tener una sección dedicada por completo a leer valores de datos JSON. Parecería lógico tener también una sección que se centre en escribir datos JSON. Resulta que escribir datos JSON no es tan popular a menos que esté guardando datos JSON en un archivo o haciendo algo con servicios web. Si está realizando cualquiera de estas tareas, ***estadísticamente está desarrollando en Node o escribiendo código en un lenguaje de programación que no sea JavaScript***.

Para el desarrollo de front-end, no puedo pensar en demasiados casos en los que la información sobre cómo escribir JSON sería útil. Si se encuentra con una situación poco común en la que necesita hacer algo más que leer datos JSON, ¡mi recomendación es que use Google!

<hr>

### El Mínimo Absoluto

En un momento dado, este capítulo se habría centrado en XML. Incluso hoy en día, XML sigue siendo muy popular como formato de archivo para almacenar o comunicar información. Solo en un mundo donde el navegador web es el rey (también conocido como el mundo en el que vivimos) es donde JSON es extremadamente popular. Fuera de los sitios web, las aplicaciones web y los servicios web basados en REST, tratar con datos en formato JSON no es tan popular. ¡Debe tener esto en cuenta cuando se encuentre en situaciones más antiguas y menos centradas en la web!

Si tiene alguna pregunta relacionada con JSON o sobre cualquier otra cosa, diríjase y publique en los foros en https://forum.kirupa.com.
