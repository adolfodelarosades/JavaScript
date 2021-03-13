# Capítulo 2: Conceptos básicos
* El sistema de clases
   * Ext
      * application
      * define
      * create
      * onReady
      * widget
      * getClass
      * getClassName
      * Ext.Base
      * Ext.Class
      * Ext.ClassManager
      * Ext.Loader
* Events
   * Agregar listeners
   * Eliminación de listeners
   * El DOM node manejo de eventos
* Accediendo a DOM
   * Ext.get
   * Ext.query
   * Ext.select
      * Multiple selections
      * Selection root
      * Selection chaining
   * Ext.ComponentQuery
* Componentes, containers y layouts
   * Componentes
   * Containers
   * Layouts
      * updateLayout
      * suspendLayout
      * El absolute layout
      * El accordion layout
      * El anchor layout
      * El border layout
      * El card layout
      * El center layout
      * El column layout
      * El fit Layout
      * El hbox layout
      * El table layout
      * El VBox layout
* Resumen

Antes de que comencemos a crear un proyecto de muestra en el siguiente capítulo, aprenderá algunos conceptos básicos en Ext JS, que le ayudarán a comprender el proyecto de muestra fácilmente. En este capítulo se tratarán los siguientes temas:

* El sistema de clases y la creación y ampliación de clases.
* Events
* Querying
* Containers
* Layouts

## El sistema de clases

Ext JS proporciona una serie de funciones que facilitan la creación y el trabajo con clases.

Las siguientes son las clases en el sistema de clases Ext JS 6:

* `Ext`
* `Ext.Base`
* `Ext.Class`
* `Ext.ClassManager`
* `Ext.Loader`

### Ext

`Ext` es un objeto singleton global que encapsula todas las clases, singletons y métodos utility en la library Sencha. Muchas funciones de utilidad de uso común se definen en `Ext`. También proporciona accesos directos a métodos de uso frecuente en otras clases.

Echemos un vistazo a algunos de los métodos y propiedades de la clase `Ext`:

#### application

Muchas aplicaciones se inician con `Ext.application`. Esta función carga la clase `Ext.app.Application` y la inicia con la configuración dada después de cargar la página.

`Ext.app.Application` es una clase que representa la aplicación completa que vio en el Capítulo 1, Introducción a Ext JS. El siguiente es un ejemplo de `Ext.app.Application`.

```js
Ext.application({
   name: 'MyApp',
   extend:'MyApp.Application',
   launch: function() {
   }
});
```

Este código crea una variable global llamada `MyApp`. Todas las clases de la aplicación residen bajo este single namespace, lo que reducirá las posibilidades de colisión de variables globales.

#### define

Para crear o override una clase, puede utilizar esta función. Se necesitan tres parámetros, como se muestra en el siguiente código. Aquí, `name` es el nombre de la clase, `data` son las propiedades para aplicar a esta clase, y `callback` es una función opcional que será llamado después de que se crea la clase:

   ```js
   Ext.define(name,data, callback)
   ```
   
El siguiente código crea una clase llamada `Car`:

```js
Ext.define('Car', {
   name: null,
   constructor: function(name) {
      if (name) {
         this.name = name;
      }
   },
   start: function() {
      alert('Car started');
   }
});
```

También puedes usar `define` para extender una clase:

   ```js
   Ext.define('ElectricCar', {
      extend: 'Car',
      start: function() {
         alert("Electric car started");
      }
   });
   ```

Si desea reemplazar la implementación de una clase base, puede usar `Ext.define` para override el método, como se muestra en el siguiente código:

   ```js
   Ext.define('My.ux.field.Text', {
      override: 'Ext.form.field.Text',
      setValue: function(val) {
         this.callParent(['In override']);
         return this;
      }
   });
   ```
   
Si desea crear una clase singleton, puede usar una propiedad llamada singleton definido en `Ext.Class`, como se muestra en el siguiente código:   

   ```js
   Ext.define('Logger', {
      singleton: true,
      log: function(msg) {
         console.log(msg);
      }
   });
   ```

#### create

```js
```

```js
```

#### onReady
#### widget
#### getClass
#### getClassName
#### Ext.Base
#### Ext.Class
#### Ext.ClassManager
#### Ext.Loader
## Events
### Agregar listeners
### Eliminación de listeners
### El DOM node manejo de eventos
## Accediendo a DOM
### Ext.get
### Ext.query
### Ext.select
#### Multiple selections
#### Selection root
#### Selection chaining
### Ext.ComponentQuery
## Componentes, containers y layouts
### Componentes
### Containers
### Layouts
#### updateLayout
#### suspendLayout
#### El absolute layout
#### El accordion layout
#### El anchor layout
#### El border layout
#### El card layout
#### El center layout
#### El column layout
#### El fit Layout
#### El hbox layout
#### El table layout
#### El VBox layout
## Resumen

