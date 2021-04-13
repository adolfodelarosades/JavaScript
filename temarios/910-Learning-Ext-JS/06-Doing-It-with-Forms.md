# 6. Haciéndolo con formularios

* El componente de formulario
   * La anatomía de los campos
* Los campos disponibles
   * La clase TextField
   * El campo number
   * El campo ComboBox
   * El campo Tag
   * El campo Date
   * Los campos Checkbox y CheckboxGroup
   * Los botones Radio y RadioGroup
* El contenedor de campos
* Triggers
* Envío de datos
* Resumen   


Ext JS viene con poderosos widgets para recopilar y editar datos. Tenemos el componente form y muchos tipos de widgets de entrada. Estos incluyen textfield, textarea, radio, checkbox, combobox, slider y muchos más tipos.

En este capítulo, aprenderá sobre los componentes que podemos utilizar para recopilar datos en nuestras aplicaciones. Además, trabajaremos en algunas partes para ser reutilizadas para nuestra aplicación final, así como también crearemos algunos formularios.

En este capítulo se tratarán los siguientes temas:

* El componente form
* Los tipos de campo disponibles
* El contenedor de campo
* Envío de datos

## El Componente form

Ext JS contiene un componente llamado **`Ext.form.Panel`**. Este componente es una subclase de **`Ext.panel.Panel`** y usa **`Ext.form.Basic`** como clase requerida. Esta clase es fundamental para manejar el envío del formulario.

A la hora de diseñar aplicaciones, es importante mencionar que un análisis previo puede ser claro para nosotros, por eso creamos bloques (código, formularios, componentes, etc.) que se pueden reutilizar en otros módulos. La siguiente captura de pantalla representa una parte de nuestra aplicación. Podemos ver que el componente de formulario deberá tener ciertas funcionalidades, como crear, editar, eliminar, etc.

![06-01](images/06-01.png)

Como puede ver, el prototipo de formulario en el lado derecho contiene un título, una toolbar en la parte superior, una toolbar en la parte inferior y luego seis campos. Ahora podemos comenzar a crear el formulario como un componente separado. Como en nuestros ejemplos de código anteriores, ampliamos nuestra nueva clase de la clase **`Ext.form.Panel`**:

```js
Ext.define('MyApp.view.CustomerForm01', {
   extend: 'Ext.form.Panel',
   alias: 'widget.customerform01',
   height: 280,
   width: 448,
   bodyPadding: 6,
   title: 'Customer ( .... )',
   items: [  ],
   dockedItems: [ ]
});
```

Este código hasta ahora no hace mucho. Estamos creando el código base para extenderlo más adelante en el panel de formulario. Como puede ver, este código establece algunos atributos predeterminados, como **`height`**, **`width`**, **`bodyPadding`** y **`title`**. Hasta ahora, los elementos y las propiedades acopladas están vacíos.

Tenga en cuenta las convenciones definidas en el Capítulo 2, *Conceptos básicos*, al crear clases. Entonces, necesitamos crear el archivo y colocar el código anterior en la ruta **`appcode/view/CustomerForm01.js`**.

Como en los ejemplos de código anteriores, creemos el archivo HTML y ejecútelo para probar nuestra configuración básica:

```html
<!doctype html>
<html>
<head>
  <meta http-equiv=”X-UA-Compatible” content=”IE=edge”>
  <meta charset=”utf-8”>
  <title>Extjs - Form 01 </title>
    <link rel=”stylesheet” type=”text/css” href=”../ext-5.1.1/build/packages/ext-theme-neptune/build/resources/ext-theme-neptune-all.css”>
    <script src=”../ext-5.1.1/build/ext-all.js”></script>
    <script src=”../ext-5.1.1/build/packages/ext-theme-neptune/build/ext-theme-neptune.js”></script>

<link rel=”stylesheet” type=”text/css” href=”../shared/styles/buttons.css”>
<script type =”text/javascript” src=”form_01.js”></script>
</head>
<body style=”padding:6px;”>
</body>
</html>
```

Ahora creemos el archivo **`form_01.js`** con el siguiente código:

```js
Ext.Loader.setConfig({
   enabled: true,
   paths:{Myapp:'appcode'}
});
Ext.require([
   'Ext.form.*',
   'Ext.toolbar.*',
   'Ext.button.*',
   'Myapp.view.CustomerForm01'
]);
Ext.onReady(function(){
   var mypanel = Ext.create('Myapp.view.CustomerForm01',{
      title:'My first customer form...',
      renderTo: Ext.getBody()
   });
   console.log ('Ok');
});
```

Ejecutemos y probemos el código básico. Obtendremos un resultado similar a este:

![06-02](images/06-02.png)

El form panel se crea sin ningún contenido ni elementos. Recuerde que podemos agregar cualquier componente y widget disponible, así que ahora agreguemos algunos campos. Cambiemos la propiedad **`items`** como se muestra en el siguiente código:

```js
items: [{
xtype: 'numberfield',
anchor: '60%',
   fieldLabel: 'Customer ID'
},{
xtype: 'textfield',
anchor: '-18',
fieldLabel: 'Name'
},{
xtype: 'textfield',
fieldLabel: 'Phone'
}]
```

La propiedad **`items`** ahora tiene tres campos: un campo numérico y dos campos de texto. Además, establecemos la propiedad **`anchor`** en dos campos, y el tercero no la tiene.

> **NOTA**
> 
> De forma predeterminada, **`Ext.form.Panel`** utiliza el anchor layout, que se explica en el Capítulo 3, *Componentes y diseños*.


Actualicemos nuestro navegador y veamos el siguiente resultado, de la siguiente manera:

![06-03](images/06-03.png)

Bien, ahora tenemos tres campos en nuestro formulario y puede notar que cada campo tiene un ancho diferente. Desde la versión 4 de Ext JS en adelante, podemos configurarlos individualmente para cada campo, como **`labelWidth`**, **`labelAlign`** y otras propiedades. Tenemos dos propiedades útiles dentro del panel de formulario, que son **`defaultType`** y **`defaults`**.

La propiedad **`defaultType`** nos permite establecer el xtype predeterminado para cada campo (donde la propiedad **`xtype`** no está definida), y la propiedad **`defaults`** nos permite definir muchas configuraciones que se aplicarán a todos los elementos child (si es posible aplicarlos). Hagamos el siguiente cambio en la clase de formulario:

```js
Ext.define('MyApp.view.CustomerForm01', {
   extend: 'Ext.form.Panel',
   alias: 'widget.customerform01',
   height: 280,
   width: 448,
   bodyPadding: 6,
  defaultType:'textfield',
  defaults:{
    anchor:'-18',
    labelWidth:90,
    labelAlign:'right'
  },
   title: 'Customer ( .... )',
   items: [{
    fieldLabel: 'Customer ID',
        },{
    fieldLabel: 'Name',
        },{
fieldLabel: 'Phone',
}],
  dockedItems: [ ]
});
```

Ahora los tres items/fields tendrán **`anchor`**, **`labelWidth`** y **`labelAlign`** con la misma frecuencia. Actualicemos el navegador y veamos el resultado, que debería ser así:

![06-04](images/06-04.png)

Convertimos los tres campos a **`textfield`**. Además, la alineación de la etiqueta se estableció a **`right`** y todas tienen el mismo ancho. Como puede ver, el uso de **`defaultType`** y **`defaults`** es muy conveniente, por lo que tendremos que codificar solo unas pocas líneas en nuestro archivo, y este código se aplicará a muchos fields/components.

Por lo tanto, de acuerdo con nuestro formulario **`Customers`**, creemos los otros campos y las toolbars. Cambiemos la propiedad **`items`** de la siguiente manera:

```js
items: [{
xtype: 'numberfield',fieldLabel: 'Customer ID',
},{
  fieldLabel: 'Name',
},{
fieldLabel: 'Phone',
},{
fieldLabel: 'Web site',
},{
xtype: 'datefield',fieldLabel: 'Client since',
},{
xtype: 'combobox',fieldLabel: 'Status',
}],
```

Ahora creemos las toolbars (como se muestra en el Capítulo 5, *Botones y Toolbars*):

```js
dockedItems: [{
   xtype: 'toolbar',
   dock: 'bottom',
   items: [{
      xtype: 'tbfill'
   },{
      xtype: 'button',
      iconCls: 'save-16',
      text: 'Save...'
   }]
},{
   xtype: 'toolbar',
   dock: 'top',
   items: [{
      xtype: 'button',
      iconCls: 'addicon-16',
      text: 'New'
   },{
      xtype: 'button',
      iconCls: 'editicon-16',
      text: 'Edit'
  },{
      xtype: 'tbfill'
  },{
      xtype: 'button',
      iconCls: 'deleteicon-16',
      text: '<b>Delete</b>'
  }]
}]
```

> **NOTA**
> 
> Observe que estamos reutilizando las mismas clases CSS que en el Capítulo 5, *Botones y Toolbars*. Sin embargo, también puede usar nuevas clases y otros íconos.

Hemos terminado nuestro primer formulario, pero todavía no está haciendo nada. Agregaremos la funcionalidad en breve. Por ahora, avancemos y revisemos las otras secciones para comprender más sobre los campos disponibles de Ext JS.

### La Anatomía de los Campos

Ext JS proporciona muchos componentes para brindar al usuario una gran experiencia al usar sus aplicaciones. Los siguientes campos son componentes que podemos usar en un formulario o fuera de él.

Por ejemplo, podemos agregar un campo de texto o un cuadro combinado dentro de una toolbar en lugar de botones, de esta manera, podemos colocar campos dentro de la toolbar para que actúen como filtros u opciones de búsqueda.

Cada campo de entrada amplía la clase **`Ext.Component`**. Esto significa que cada campo tiene su propio ciclo de vida y eventos y también se puede colocar en cualquier contenedor.

También hay una clase llamada **`Ext.form.field.Base`** que define propiedades, métodos y eventos comunes en todos los campos de formulario. Esta clase base también se extiende desde las clases **`Ext.form.Labelable`** y **`Ext.form.field.Field`** (mediante el uso de mixins).

La clase **`Labelable`** le da al campo la capacidad de mostrar una etiqueta y errores en cada subclase, como textfields, comboboxes, etc.

La clase **`Field`** brinda a los campos la capacidad de administrar su valor, porque agrega algunos métodos importantes, como los métodos **`getValue`** y **`setValue`**, para establecer y recuperar el valor actual del campo. Esta clase también presenta un concepto importante, el **raw value**.

Un gran ejemplo del raw value es cuando extraemos datos de nuestro servidor y obtenemos un valor de fecha en formato de cadena. El raw value está en texto plano, pero el valor del campo de fecha debe estar en un objeto **`Date`** nativo para que podamos trabajar fácilmente con dates y times. Siempre podemos usar el raw value, pero se recomienda usarlo en su lugar. Es un objeto **`Date`** en este ejemplo.

## Los Campos Disponibles

```js
```

```js
```

### La clase TextField
```js
```

### El campo number
```js
```

```js
```

### El campo ComboBox
```js
```

```js
```

### El campo Tag

```js
```

```js
```
### El campo Date

```js
```

```js
```
### Los campos Checkbox y CheckboxGroup

```js
```

```js
```
### Los botones Radio y RadioGroup

```js
```

```js
```
## El contenedor de campos

```js
```

```js
```
## Triggers

```js
```

```js
```
## Envío de datos

```js
```

```js
```
## Resumen   
