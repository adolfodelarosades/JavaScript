# 5. Buttons y Toolbars

* Desarrollo impulsado por eventos (Event-driven development)
* Creando un botón simple
   * Configuración de iconos en botones
   * Alineación de iconos en botones
      * Manejo de eventos de botón
* Botones segmentados
* Agregar menús
* Toolbars
   * Grupos de botones de la Toolbars
* La breadcrumb bar
   * Manejo de selecciones en la breadcrumb bar
* El menú principal de nuestra aplicación
* Resumen 

Cuando trabajemos con buttons y toolbars, definitivamente necesitaremos organizarlos siempre que usemos componentes window o panel. Las toolbars son una excelente manera de agregar botones y menús, y podemos crear grupos de botones. Sin embargo, también necesitamos entender cómo manejar eventos para ejecutar acciones. Podemos agregar acciones a nuestros widgets usando callbacks y eventos para procesar la interacción del usuario.

En este capítulo, aprenderá cómo crear buttons y toolbars y cómo manejar un evento (o eventos) para comenzar con la interacción del usuario en la interfaz de usuario de Ext JS.

## Desarrollo impulsado por eventos (Event-driven development)

Antes de comenzar a hablar sobre componentes, debe comprender cómo funcionan los eventos y los listeners entre bastidores. Lo primero que debe aprender es el patrón observable.

Básicamente, ***el patrón observable*** está diseñado para permitir que las entidades u objetos se comuniquen entre sí mediante eventos. Cuando ocurre una determinada acción dentro de un objeto o componente, este objeto debe transmitir un evento a quien esté escuchando.

Por ejemplo, cuando se hace clic en un botón, se activa el evento **`click`**. Cuando se hace clic en una fila de un grid, el grid dispara el evento **`itemclick`**. Todos los componentes tienen eventos definidos y se activan cuando se produce una acción.

El componente que está disparando el evento no sabe quién escuchará sus mensajes, pero su responsabilidad es que otros sepan que algo ha sucedido. Entonces, tal vez otros componentes hagan algo al respecto, o nada en absoluto.

La clase base **`Ext.util.Observable`** nos permite agregar, disparar y escuchar eventos de un objeto o componente específico y realizar acciones cuando se ejecuta ese evento.

Todos los widgets incluidos en la library Ext JS tienen la clase **`Ext.util.Observable`** mezclada, por lo que todos los widgets activan eventos que podemos escuchar para realizar acciones y dar vida a nuestros widgets.

Como se mencionó anteriormente, podemos definir y disparar nuevos eventos en nuestros componentes personalizados usando la misma clase **`Ext.util.Observable`**.

Copie el archivo **`singleton_01.js`** (de los archivos de código del capítulo 02). Luego, tenemos que agregar los siguientes cambios a la clase **`Employee`**:

```js
Ext.define('Myapp.sample.Employee',{
mixins: {observable: 'Ext.util.Observable'},
   Code.....
   constructor: function( config ){
      Code.....
      this.mixins.observable.constructor.call( this, config );
   },
   quitJob: function(){
      this.fireEvent('quit', this.getName(), new Date(), 2, 1, 'more params...' );
   }
});
```

Como puede observar, la clase **`Employee`** ahora contiene la mezcla, la clase **`Ext.util.Observable`**. Además, dentro de la función constructor, este mixin es inicializado por el código **`this.mixins.observable.constructor.call(this, config);`**. Esto significa que **`Ext.util.Observable`** estará al tanto de cualquier evento que se inicie dentro de la clase **`Employee`**, siempre que suceda.

> **NOTA**
> 
> Para comprender más sobre los mixins, consulte http://docs.sencha.com/extjs/5.1/5.1.1-apidocs/#!/api/Ext.Mixin.


AQUIIIIIII
La función quitJob, cuando se llama, lanzará el evento quit, pasando los parámetros this.getName (), new Date (), 2, 1, 'more params ...'.

## Creando un botón simple
### Configuración de iconos en botones
### Alineación de iconos en botones
#### Manejo de eventos de botón
## Botones segmentados
## Agregar menús
## Toolbars
### Grupos de botones de la Toolbars
## La breadcrumb bar
### Manejo de selecciones en la breadcrumb bar
## El menú principal de nuestra aplicación
## Resumen 


