# 01 Primeros pasos en jQuery 6 clases • 1h 1m

* Introducción 01:34
* Preparando nuestro ambiente de trabajo 13:29
* Error muy común del jQuery 08:08
* Alto - Usemos Bootstrap - Introducción 10:06
* Selectores y encadenamiento 14:52
* replaceWith, children y Find 13:01

## Introducción 01:34

## Preparando nuestro ambiente de trabajo 13:29

### Instalar Editor de Texto

Instalar un Editor de Texto, en mi caso VSC, en el curso usan TextEditor

### Instalar JQuery 

Descargar [JQuery](https://jquery.com/) en la sección [download](https://jquery.com/download/).

La última versión a fecha del 04/03/2023 es la **v3.6.3**, en momento del curso estaban las versiones **v1.11.3** y **v2.1.4**  

<img width="363" alt="image" src="https://user-images.githubusercontent.com/23094588/222903957-17f828fe-3594-48b2-bccd-691870af3574.png">

Las versiones superiores a 2.X no son compatibles con Internet Explorer 6, 7 y 8 en esos casos se usaría alguna versión 1.X

Vamos a descargar la versión 2.X (jQuery Core 2.2.4) 

<img width="1275" alt="image" src="https://user-images.githubusercontent.com/23094588/222904401-1671cffb-b037-4b70-842c-12e22c72ba5e.png">

o podemos usar un CDN

```js
<script src="https://code.jquery.com/jquery-3.6.3.js" integrity="sha256-nQLuAZGRRcILA+6dMBOvcRh5Pe310sBpanc6+QBmyVM=" crossorigin="anonymous"></script>

<script src="https://code.jquery.com/jquery-3.6.3.min.js" integrity="sha256-pvPw+upLPUjgMXY0G+8O0xUf+/Im1MZjXxxgOcBQBXU=" crossorigin="anonymous"></script>

<script
  src="https://code.jquery.com/jquery-2.2.4.js"
  integrity="sha256-iT6Q9iMJYuQiMWNd9lDyBUStIq/8PuOW33aOqmvFpqI="
  crossorigin="anonymous"></script>
  
<script
  src="https://code.jquery.com/jquery-2.2.4.min.js"
  integrity="sha256-BbhdlvQf/xTY9gja0Dq3HiwQF8LaCRTXxZKRutelT44="
  crossorigin="anonymous"></script>  
```

Vamos a crear la siguiente estructura para nuestro primer ejemplo.

<img width="754" alt="image" src="https://user-images.githubusercontent.com/23094588/222905621-44a92c6e-2aaa-4d6a-a496-72d27dd2c24b.png">


Vea la sección **`<script>...</script>`**, vemos como se defina una función y como invocarla. La sentencia **`jQuery();`**  es como llamar a una función cualquier.

<img width="958" alt="image" src="https://user-images.githubusercontent.com/23094588/222906027-65198093-b154-4bf4-95a4-f4429059dce2.png">

Vamos a usar solo **`jQuery();`** haciendo lo siguiente:

```js
jQuery('ul').css('color', 'red');
```

Le estamos diciendo a jQuery que búsque en la página todos los elementos **`ul`**  y aplicale el CSS para asignarle color rojo. En el programa solo hay un elemento **`ul`** por lo que al ejecutar el programa el listado se pintara de color rojo.

<img width="1512" alt="image" src="https://user-images.githubusercontent.com/23094588/223570449-31e3103a-015a-433d-aa1c-886846ada9c1.png">

<img width="1512" alt="image" src="https://user-images.githubusercontent.com/23094588/223570520-bbed3880-d83a-464a-b65f-f54688ab04f5.png">

```htm
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Lección 01</title>

    <script src="js/lib/jquery-2.2.4.min.js"></script>
</head>
<body>
    <ul>
        <li>Hola 1</li>
        <li>Hola 2</li>
        <li>Hola 3</li>
    </ul>

    <script>
        jQuery('ul').css('color', 'red');
    </script>
    
</body>
</html>
```


## Error muy común del jQuery 08:08

## Alto - Usemos Bootstrap - Introducción 10:06

## Selectores y encadenamiento 14:52

## replaceWith, children y Find 13:01

