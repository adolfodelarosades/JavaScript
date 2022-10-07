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

Todos los elementos **`img`** deben tener un atributo **`alt`**. El texto del atributo **`alt`** se usa para que los lectores de pantalla mejoren la accesibilidad y se muestra si la imagen no se carga. Por ejemplo, **`<img src="cat.jpg" alt="A cat">`** tiene un atributo **`alt`** con el texto **`A cat`**.

Dentro del elemento **`img`**, agrega un atributo **`alt`** con este texto:

**`A cute orange cat lying on its back`**

```html
<html>
   <body>
      <h1>CatPhotoApp</h1>
      <main>
         <h2>Cat Photos</h2>
         <!-- TODO: Add link to cat photos -->
         <p>Click here to view more cat photos.</p>
         <img src="https://cdn.freecodecamp.org/curriculum/cat-photo-app/relaxing-cat.jpg" alt="A cute orange cat lying on its back">
      </main>
   </body>  
</html>
```

Esto no altera en nada la salida obtenida ya que la imagen existe y la podemos ver si por ejemplo ponemos **`relaxing-cat2.jpg`** que es una imagen que no existe en la salida que obtenemos es:

![image](https://user-images.githubusercontent.com/23094588/194517260-c009ba09-85c4-41d9-9471-448817984cda.png)


## Paso 10

Puede vincular a otra página con el elemento ancla - anchor (**`a`**). Por ejemplo, **`<a href='https://freecodecamp.org'></a>`** vincularía a **`freecodecamp.org`**.

Agregue un elemento de anclaje después del párrafo que vincula a **`https://freecatphotoapp.com`**. En este punto, el enlace no aparecerá en la vista previa.

```html
<html>
   <body>
      <h1>CatPhotoApp</h1>
      <main>
         <h2>Cat Photos</h2>
         <!-- TODO: Add link to cat photos -->
         <p>Click here to view more cat photos.</p>
         <a href='https://freecatphotoapp.com'></a>
         <img src="https://cdn.freecodecamp.org/curriculum/cat-photo-app/relaxing-cat.jpg" alt="A cute orange cat lying on its back">
      </main>
   </body>  
</html>
```

![image](https://user-images.githubusercontent.com/23094588/194518995-7ca44964-8941-4be6-b2cc-e739f24aa9de.png)


## Paso 11

El texto de un enlace debe colocarse entre las etiquetas de apertura y cierre de un elemento ancla (**`a`**). Por ejemplo, **`<a href="https://www.freecodecamp.org">click here to go to freeCodeCamp.org</a>`** es un enlace con el texto **`click here to go to freeCodeCamp.org`**.

Agregue al enlace el texto **`link to cat pictures`** al elemento de anclaje. Esto se convertirá en el texto del enlace.

```html
<html>
   <body>
      <h1>CatPhotoApp</h1>
      <main>
         <h2>Cat Photos</h2>
         <!-- TODO: Add link to cat photos -->
         <p>Click here to view more cat photos.</p>
         <a href='https://freecatphotoapp.com'>link to cat pictures</a>
         <img src="https://cdn.freecodecamp.org/curriculum/cat-photo-app/relaxing-cat.jpg" alt="A cute orange cat lying on its back">
      </main>
   </body>  
</html>
```

![image](https://user-images.githubusercontent.com/23094588/194520276-f004d0bc-a086-4474-9fda-2beb9bca792c.png)


## Paso 12

En el paso anterior, convirtió las palabras **`link to cat pictures`** en un enlace colocándolos entre las etiquetas de anclaje (**`a`**) de apertura y cierre. Puede hacer lo mismo con las palabras dentro de un elemento, como un elemento **`p`**.

En el texto de su elemento **`p`**, convierta las palabras **`cat photos`** en un enlace a **`https://freecatphotoapp.com`** colocando estas palabras dentro de las etiquetas de anclaje (**`a`**) de apertura y cierre.

```html
<html>
   <body>
      <h1>CatPhotoApp</h1>
      <main>
         <h2>Cat Photos</h2>
         <!-- TODO: Add link to cat photos -->
         <p>Click here to view more <a href='https://freecatphotoapp.com'>cat photos</a>.</p>
         <a href='https://freecatphotoapp.com'>link to cat pictures</a>
         <img src="https://cdn.freecodecamp.org/curriculum/cat-photo-app/relaxing-cat.jpg" alt="A cute orange cat lying on its back">
      </main>
   </body>  
</html>
```

![image](https://user-images.githubusercontent.com/23094588/194521486-35aa9657-7c01-43c4-9640-558fd86044af.png)


## Paso 13

Ahora que convirtió el texto **`cat photos`** dentro del elemento **`p`** en un enlace, no necesita el segundo enlace debajo del elemento **`p`**. Elimine todo el elemento de anclaje debajo del elemento **`p`**.

```html
<html>
   <body>
      <h1>CatPhotoApp</h1>
      <main>
         <h2>Cat Photos</h2>
         <!-- TODO: Add link to cat photos -->
         <p>Click here to view more <a href='https://freecatphotoapp.com'>cat photos</a>.</p>
         <img src="https://cdn.freecodecamp.org/curriculum/cat-photo-app/relaxing-cat.jpg" alt="A cute orange cat lying on its back">
      </main>
   </body>  
</html>
```

![image](https://user-images.githubusercontent.com/23094588/194522127-56733e8e-be16-4f41-80f9-d8e6ad33240f.png)


## Paso 14

Agregue un atributo **`target`** con el valor **`_blank`** a la etiqueta de apertura del elemento ancla (**`a`** ), para que el enlace se abra en una nueva pestaña.


```html
<html>
   <body>
      <h1>CatPhotoApp</h1>
      <main>
         <h2>Cat Photos</h2>
         <!-- TODO: Add link to cat photos -->
         <p>Click here to view more <a href='https://freecatphotoapp.com' target='_blank'>cat photos</a>.</p>
         <img src="https://cdn.freecodecamp.org/curriculum/cat-photo-app/relaxing-cat.jpg" alt="A cute orange cat lying on its back">
      </main>
   </body>  
</html>
```

Esto no altera en nada la salida obtenida.


## Paso 15

Convierta la imagen en un enlace rodeándola con las etiquetas de los elementos necesarios. Utilice **`https://freecatphotoapp.com`** como el valor del atributo **`href`** del ancla.

```html
<html>
   <body>
      <h1>CatPhotoApp</h1>
      <main>
         <h2>Cat Photos</h2>
         <!-- TODO: Add link to cat photos -->
         <p>Click here to view more <a href='https://freecatphotoapp.com' target='_blank'>cat photos</a>.</p>
         <a href='https://freecatphotoapp.com' target='_blank'><img src="https://cdn.freecodecamp.org/curriculum/cat-photo-app/relaxing-cat.jpg" alt="A cute orange cat lying on its back"></a>
      </main>
   </body>  
</html>
```

Con esto cuando nos pongamos sobre la imagen nos saldra una manita que indica que podemos pulsar en la imagen para ir al enlace linkado.

## Paso 16

Antes de agregar cualquier contenido nuevo, debe utilizar un elemento **`section`** para separar el contenido de las fotos de gatos del contenido futuro.

Tome todos los elementos ubicados actualmente dentro del elemento **`main`** y anídelos en un elemento **`section`**.

```html
<html>
   <body>
      <h1>CatPhotoApp</h1>
      <main>
         <section>
            <h2>Cat Photos</h2>
            <!-- TODO: Add link to cat photos -->
            <p>Click here to view more <a href='https://freecatphotoapp.com' target='_blank'>cat photos</a>.</p>
            <a href='https://freecatphotoapp.com' target='_blank'><img src="https://cdn.freecodecamp.org/curriculum/cat-photo-app/relaxing-cat.jpg" alt="A cute orange cat lying on its back"></a>
         </section>
      </main>
   </body>  
</html>
```

Esto no altera en nada la salida obtenida.

## Paso 17

Es hora de agregar una nueva sección. Agregue un segundo elemento **`section`** debajo del elemento **`section`** existente.

```html
<html>
   <body>
      <h1>CatPhotoApp</h1>
      <main>
         <section>
            <h2>Cat Photos</h2>
            <!-- TODO: Add link to cat photos -->
            <p>Click here to view more <a href='https://freecatphotoapp.com' target='_blank'>cat photos</a>.</p>
            <a href='https://freecatphotoapp.com' target='_blank'><img src="https://cdn.freecodecamp.org/curriculum/cat-photo-app/relaxing-cat.jpg" alt="A cute orange cat lying on its back"></a>
         </section>
         <section></section>
      </main>
   </body>  
</html>
```

Esto no altera en nada la salida obtenida.


## Paso 18

Dentro del segundo elemento **`section`**, agregue un nuevo elemento **`h2`** con el texto **`Cat Lists`**.

```html
<html>
   <body>
      <h1>CatPhotoApp</h1>
      <main>
         <section>
            <h2>Cat Photos</h2>
            <!-- TODO: Add link to cat photos -->
            <p>Click here to view more <a href='https://freecatphotoapp.com' target='_blank'>cat photos</a>.</p>
            <a href='https://freecatphotoapp.com' target='_blank'><img src="https://cdn.freecodecamp.org/curriculum/cat-photo-app/relaxing-cat.jpg" alt="A cute orange cat lying on its back"></a>
         </section>
         <section>
            <h2>Cat Lists</h2>
         </section>
      </main>
   </body>  
</html>
```

![image](https://user-images.githubusercontent.com/23094588/194533238-27544c93-f053-4720-bc76-30cfd748f79e.png)


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


