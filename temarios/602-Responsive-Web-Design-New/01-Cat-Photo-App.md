# Aprende HTML construyendo una aplicación de Fotos de Gatos (Cat Photo App).

Las etiquetas HTML le dan a una página web su estructura. Puede usar etiquetas HTML para agregar fotos, botones y otros elementos a su página web.

En este curso, aprenderá las etiquetas HTML más comunes mediante la creación de su propia aplicación de fotos de gatos.

## Paso 1

Vamos a comenzar viendo nuestro primer archivo HTML.

```html
<html>
   <body>
      <h1>Hello World</h1>
   </body>  
</html>
```

El cual tiene la siguiente salida:

![image](https://user-images.githubusercontent.com/23094588/194502102-75d586ea-6850-49ce-9167-8dcbc21dd0f8.png)



Los elementos HTML tienen etiquetas de apertura como **`<h1>`** y etiquetas de cierre como **`</h1>`**.

El texto de un elemento va entre sus etiquetas de apertura y cierre.

Encuentra el elemento **`h1`** y cambia su texto a:

**`CatPhotoApp`**

```html
<html>
   <body>
      <h1>CatPhotoApp</h1>
   </body>  
</html>
```

Ahora tenemos esta salida:

![image](https://user-images.githubusercontent.com/23094588/194502583-03a28a4f-6de1-4392-8bc4-3c1b88994826.png)


## Paso 2

Los elementos de encabezado **`h1`** a **`h6`** se utilizan para indicar la importancia del contenido debajo de ellos. ***Cuanto menor sea el número, mayor será la importancia***, por lo que los elementos **`h2`** tienen menos importancia que los elementos **`h1`**. ***Solo use un elemento `h1` por página*** y coloque los encabezados de menor importancia debajo de los encabezados de mayor importancia.

Debajo del elemento **`h1`**, agregue un elemento **`h2`** con este texto:

**`Cat Photos`**

```html
<html>
   <body>
      <h1>CatPhotoApp</h1>
      <h2>Cat Photos</h2>
   </body>  
</html>
```

![image](https://user-images.githubusercontent.com/23094588/194503537-2df0f7eb-18e8-4950-bb7a-13a4f83ebfbf.png)


## Paso 3

El elemento **`p`** se utiliza para crear un párrafo de texto en sitios web. Cree un elemento **`p`** debajo de su elemento **`h2`** y asígnele el siguiente texto:

**`Click here to view more cat photos.`**


```html
<html>
   <body>
      <h1>CatPhotoApp</h1>
      <h2>Cat Photos</h2>
      <p>Click here to view more cat photos.</p>
   </body>  
</html>
```

![image](https://user-images.githubusercontent.com/23094588/194506142-81faa8ba-d24e-43de-b914-45254e7136ab.png)


## Paso 4

Comentar le permite dejar mensajes sin afectar la visualización del navegador. También le permite hacer que el código esté inactivo. Un comentario en HTML comienza con **`<!--`**, contiene cualquier número de líneas de texto y termina con **`-->`**. Por ejemplo, el comentario **`<!-- TODO: Remove h1 -->`** contiene el texto **TODO: Remove h1**.

Agregue un comentario sobre el elemento **`p`** con este texto:

**`TODO: Add link to cat photos`**

```html
<html>
   <body>
      <h1>CatPhotoApp</h1>
      <h2>Cat Photos</h2>
      <!-- TODO: Add link to cat photos -->
      <p>Click here to view more cat photos.</p>
   </body>  
</html>
```

La salida no se altera:

![image](https://user-images.githubusercontent.com/23094588/194506142-81faa8ba-d24e-43de-b914-45254e7136ab.png)

## Paso 5

HTML5 tiene algunos elementos que identifican diferentes áreas de contenido. Estos elementos hacen que su HTML sea más fácil de leer y ayudan con la optimización de motores de búsqueda (SEO) y la accesibilidad.

Identifique la sección principal de esta página agregando una etiqueta de apertura **`<main>`** después del elemento **`h1`** y una etiqueta de cierre **`</main>`** después del elemento **`p`**.

```html
<html>
   <body>
      <h1>CatPhotoApp</h1>
      <main>
      <h2>Cat Photos</h2>
      <!-- TODO: Add link to cat photos -->
      <p>Click here to view more cat photos.</p>
      </main>
   </body>  
</html>
```

## Paso 6

En el paso anterior, colocó los elementos **`h2`**, comentario y **`p`** dentro del elemento **`main`**. Esto se llama **anidamiento (nesting)**. Los elementos anidados deben colocarse dos o tres espacios más a la derecha del elemento en el que están anidados. Este espacio se denomina **sangría** y se utiliza para facilitar la lectura de HTML.

El elemento **`h2`** y el comentario tienen una sangría de dos espacios más que el elemento principal en el código siguiente. Use la barra espaciadora en su teclado para agregar dos espacios más delante del elemento **`p`** para que también tenga la sangría adecuada.

```html
<html>
   <body>
      <h1>CatPhotoApp</h1>
      <main>
         <h2>Cat Photos</h2>
         <!-- TODO: Add link to cat photos -->
         <p>Click here to view more cat photos.</p>
      </main>
   </body>  
</html>
```

Esto no altera en nada la salida obtenida.

## Paso 7

Puede agregar imágenes a su sitio web utilizando el elemento **`img`**. Los elementos **`img`** tienen una etiqueta de apertura sin una etiqueta de cierre. Una etiqueta para ***un elemento sin una etiqueta de cierre se conoce como etiqueta de cierre automático***.

Agregue un elemento **`img`** debajo del elemento **`p`**. En este punto, no aparecerá ninguna imagen en el navegador.

```html
<html>
   <body>
      <h1>CatPhotoApp</h1>
      <main>
         <h2>Cat Photos</h2>
         <!-- TODO: Add link to cat photos -->
         <p>Click here to view more cat photos.</p>
         <img>
      </main>
   </body>  
</html>
```

Esto no altera en nada la salida obtenida.

## Paso 8

Los ***atributos*** HTML son palabras especiales que se usan dentro de la etiqueta de apertura de un elemento para controlar el comportamiento del elemento. El atributo **`src`** en un elemento **`img`** especifica la URL de la imagen (donde se encuentra la imagen). Un ejemplo de un elemento **`img`** usando un atributo **`<img src="https://www.example.com/the-image.jpg">`**.

Dentro del elemento **`img`** existente, agregue un atributo **`src`** con esta URL:

**`https://cdn.freecodecamp.org/curriculum/cat-photo-app/relaxing-cat.jpg`**


```html
<html>
   <body>
      <h1>CatPhotoApp</h1>
      <main>
         <h2>Cat Photos</h2>
         <!-- TODO: Add link to cat photos -->
         <p>Click here to view more cat photos.</p>
         <img src="https://cdn.freecodecamp.org/curriculum/cat-photo-app/relaxing-cat.jpg">
      </main>
   </body>  
</html>
```

La salida es:

![image](https://user-images.githubusercontent.com/23094588/194514669-1e45e6dd-78e1-49c2-9b5a-658f1a235c62.png)


## Paso 9
## Paso 10
## Paso 11
## Paso 12
## Paso 13
## Paso 14
## Paso 15
## Paso 16
## Paso 17
## Paso 18
## Paso 19
## Paso 20
## Paso 21
## Paso 22
## Paso 23
## Paso 24
## Paso 25
## Paso 26
## Paso 27
## Paso 28
## Paso 29
## Paso 30
## Paso 31
## Paso 32
## Paso 33
## Paso 34
## Paso 35
## Paso 36
## Paso 37
## Paso 38
## Paso 39
## Paso 40
## Paso 41
## Paso 42
## Paso 43
## Paso 44
## Paso 45
## Paso 46
## Paso 47
## Paso 48
## Paso 49
## Paso 50
## Paso 51
## Paso 52
## Paso 53
## Paso 54
## Paso 55
## Paso 56
## Paso 57
## Paso 58
## Paso 59
## Paso 60
## Paso 61
## Paso 62
## Paso 63
## Paso 64
## Paso 65
## Paso 66
## Paso 67
## Paso 68
## Paso 69


