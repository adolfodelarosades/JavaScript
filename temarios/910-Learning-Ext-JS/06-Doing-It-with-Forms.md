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

#### 🔴 6️⃣ 💻 Mi versión `910-Learning-Ext-JS-06-01-Form-01.html`

```html
<!DOCTYPE html>
<html>
   <head>
      <title>Extjs - Form 01</title>
      <meta charset="UTF-8">
      <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no"> 
      <link href = "https://cdnjs.cloudflare.com/ajax/libs/extjs/6.0.0/classic/theme-neptune/resources/theme-neptune-all.css" rel = "stylesheet" />
      <script type = "text/javascript" src = "https://cdnjs.cloudflare.com/ajax/libs/extjs/6.0.0/ext-all.js"></script>
      <link rel="stylesheet" type="text/css" href="styles/buttons.css">
      <script type = "text/javascript">

        // JavaScript Document
        Ext.Loader.setConfig({
            enabled: true,
            paths:{
                Myapp:'appcode'	
            }	
        });
        Ext.require([
            'Ext.form.*',
            'Ext.toolbar.*',
            'Ext.button.*',
            'Myapp.view.CustomerForm01'
        ]);
        Ext.onReady(function(){
            var mypanel = Ext.create('Myapp.view.CustomerForm01',{
                title:'Mi primer form personalizado...', 
                renderTo: Ext.getBody()		
            });
            console.log ('Ok');
        });

      </script>
   </head>
   <body style="padding:0px;">
   </body>
</html>
```

`styles/buttons.css`

```css
/* CSS Document */

.addicon-24{ background:transparent url('../images/add_24x24.png') center 0 no-repeat !important; }
.addicon-32{ background:transparent url('../images/add_32x32.png') center 0 no-repeat !important; }
.addicon-16{ background:transparent url('../images/add_16x16.png') center 0 no-repeat !important; }

.deleteicon-16{ background:transparent url('../images/delete.png') center 0 no-repeat !important; }
.editicon-16{ background:transparent url('../images/pencil.png') center 0 no-repeat !important; }

.help-16{ background:transparent url('../images/help.png') center 0 no-repeat !important; }
.help-32{ background:transparent url('../images/help_32x32.png') center 0 no-repeat !important; }

.print-16{ background:transparent url('../images/printer.png') center 0 no-repeat !important; }
.print-32{ background:transparent url('../images/printer_32x32.png') center 0 no-repeat !important; }

.export-16{ background:transparent url('../images/table_export.png') center 0 no-repeat !important; }
.export-32{ background:transparent url('../images/table_export_32x32.png') center 0 no-repeat !important; }

.home-16{ background:transparent url('../images/home_page.png') center 0 no-repeat !important; } 
.home-32{ background:transparent url('../images/home_page_32x32.png') center 0 no-repeat !important; } 

.categories-16{ background:transparent url('../images/three_tags.png') center 0 no-repeat !important; } 
.products-16{ background:transparent url('../images/package.png') center 0 no-repeat !important; } 
.clients-16{ background:transparent url('../images/group.png') center 0 no-repeat !important; } 
.invoices-16{ background:transparent url('../images/receipt_invoice.png') center 0 no-repeat !important; } 
```

`'Myapp.view.CustomerForm01'`

```js
/*
 * File: app/view/CustomerForm01.js
 */
Ext.define('Myapp.view.CustomerForm01', {
    extend: 'Ext.form.Panel',
    alias: 'widget.customerform01',
    requires: [
        'Ext.form.field.Number',
        'Ext.form.field.Date',
        'Ext.form.field.ComboBox',
        'Ext.toolbar.Toolbar',
        'Ext.toolbar.Fill',
        'Ext.button.Button'
    ],
    height: 280,
    width: 448,
    animCollapse: true,
    bodyPadding: 6,
    collapsible: false,
    header: true,
    title: 'Cliente ( .... )',
	defaultType:'textfield',
	defaults:{
		anchor:'-18',
		labelWidth:90, 
		labelAlign:'right'	
	}, 	
    items: [
        {
			xtype: 'numberfield',
			//anchor: '100%',
			// maxWidth: 200,
			//minWidth: 200,
			fieldLabel: 'Cliente ID',
			// labelAlign: 'right',
			// labelWidth: 80,
			// msgTarget: 'side',
			// hideTrigger: true
        },{
			//xtype: 'textfield',
			//anchor: '-18',
			fieldLabel: 'Nombre',
			//labelAlign: 'right',
			//labelWidth: 80,
			//msgTarget: 'side'
        },{
            //xtype: 'textfield',
            //anchor: '-18',
            fieldLabel: 'Teléfono',
            //labelAlign: 'right',
            //labelWidth: 80,
            // msgTarget: 'side'
        },{
            //xtype: 'textfield',
            //anchor: '-18',
            fieldLabel: 'Web site',
            //labelAlign: 'right',
            //labelWidth: 80,
            //msgTarget: 'side'
        },{
            xtype: 'datefield',
            //anchor: '60%',
            //width: '',
            fieldLabel: 'Cliente desde',
            //labelAlign: 'right',
            //labelWidth: 80,
            //msgTarget: 'side'
        },{
            xtype: 'combobox',
            //anchor: '-18',
            fieldLabel: 'Estado',
            //labelAlign: 'right',
            //labelWidth: 80,
            //msgTarget: 'side'
        }
    ],
    dockedItems: [{
            xtype: 'toolbar',
            dock: 'bottom',
            items: [{
                    xtype: 'tbfill'
                },{
                    xtype: 'button',
                    iconCls: 'save-16',
                    text: 'Save...'
                }
            ]
        },{
            xtype: 'toolbar', dock: 'top',
            items: [{
                    xtype: 'button',
                    iconCls: 'addicon-16',
                    text: 'Nuevo'
                },{
                    xtype: 'button',
                    iconCls: 'editicon-16',
                    text: 'Editar'
                },{
                    xtype: 'tbfill'
                },{
                    xtype: 'button',
                    iconCls: 'deleteicon-16',
                    text: '<b>Eliminar</b>'
                }
            ]
        }
    ]

});
```

![06-20](images/06-20.png)

### La Anatomía de los Campos

Ext JS proporciona muchos componentes para brindar al usuario una gran experiencia al usar sus aplicaciones. Los siguientes campos son componentes que podemos usar en un formulario o fuera de él.

Por ejemplo, podemos agregar un campo de texto o un cuadro combinado dentro de una toolbar en lugar de botones, de esta manera, podemos colocar campos dentro de la toolbar para que actúen como filtros u opciones de búsqueda.

Cada campo de entrada amplía la clase **`Ext.Component`**. Esto significa que cada campo tiene su propio ciclo de vida y eventos y también se puede colocar en cualquier contenedor.

También hay una clase llamada **`Ext.form.field.Base`** que define propiedades, métodos y eventos comunes en todos los campos de formulario. Esta clase base también se extiende desde las clases **`Ext.form.Labelable`** y **`Ext.form.field.Field`** (mediante el uso de mixins).

La clase **`Labelable`** le da al campo la capacidad de mostrar una etiqueta y errores en cada subclase, como textfields, comboboxes, etc.

La clase **`Field`** brinda a los campos la capacidad de administrar su valor, porque agrega algunos métodos importantes, como los métodos **`getValue`** y **`setValue`**, para establecer y recuperar el valor actual del campo. Esta clase también presenta un concepto importante, el **raw value**.

Un gran ejemplo del raw value es cuando extraemos datos de nuestro servidor y obtenemos un valor de fecha en formato de cadena. El raw value está en texto plano, pero el valor del campo de fecha debe estar en un objeto **`Date`** nativo para que podamos trabajar fácilmente con dates y times. Siempre podemos usar el raw value, pero se recomienda usarlo en su lugar. Es un objeto **`Date`** en este ejemplo.

## Los Campos Disponibles

Ext JS proporciona muchos widgets que podemos usar para recopilar y editar datos en nuestros formularios. Aprenderá sobre los widgets y las configuraciones más útiles que puede utilizar para crear hermosas formas. Algunos de los campos que vamos a ver son los siguientes:

* **`text`**
* **`number`**
* **`combobox`** y **`tag`**
* **`date`**
* **`checkbox`** y campos **`checkboxGroup`**
* **`radio`** y campos **`radioGroup`**

Los campos que vamos a cubrir son los básicos. Ext JS proporciona muchos más campos, que se pueden ver en los ejemplos de Ext JS, y también muchos de ellos se basan en subclases de estos. Para los siguientes ejemplos, vamos a crear una clase que se extiende desde la clase **`Form`** y contiene los campos que explicaremos en detalle más adelante:

```js
Ext.define('Myapp.view.AvailableFields01', {
   extend: 'Ext.form.Panel',
   alias: 'widget.availablefields01',
   requires: ['Ext.form.*'],
   height: 280,
   width:448,
   bodyPadding: 6,
   title: 'Available Fields',
   defaultType:'textfield',
   defaults:{
      anchor:'-18',
      labelWidth:100,
      labelAlign:'right'
   },
   initComponent: function() {
      var me = this;
      var myItems = me.createFields();
      Ext.applyIf(me,{items: myItems});
      me.callParent(arguments);
   },
   createFields: function (){
      var newItems=[];
      return newItems;
   }
});
```

En este ejemplo, configuramos la función **`initComponent`**. Aquí, podemos crear código para diferentes eventos: inicialización, validación de campo, etc. En este caso, estamos llamando a la función **`createFields`** para obtener los campos que necesitamos establecer en la propiedad Items.

Además, definimos la función **`createFields`**. Aquí es donde vamos a establecer los otros campos mientras avanzamos en este capítulo.

> **TIP**
> 
> Usar una función para definir el array de items es una excelente manera de escribir nuestro código para facilitar la lectura. Además, si desea extender esta clase, podemos override este método y agregar más componentes a su formulario en la subclase.

### La Clase TextField

Ya hemos usado la clase **`TextField`** para crear nuestro panel de formulario de **`Customer`**, y usamos la propiedad **`xtype`** para crearlo. Siempre podemos crear la instancia usando el método **`Ext.create`**, y la clase que deberíamos instanciar es **`Ext.form.field.Text`**.

Esta clase se extiende desde la clase **`Ext.form.field.base`** y está destinada a administrar texto como un valor de string. Define algunos eventos importantes, como **`keydown`**, **`keypress`** y **`keyup`**. Estos eventos son muy útiles para capturar las claves que el usuario ingresa en un componente de campo de texto.

Es importante tener en cuenta que si queremos usar estos eventos, debemos establecer la propiedad **`enableKeyEvents`** en **`true`**. Por lo tanto, cambiemos nuestra función **`createFields`** al siguiente código:

```js
createFields: function (){
  var newItems=[];
  // Step 1
  var myTextField = Ext.create('Ext.form.field.Text',{
     fieldLabel:'Name',
     name:'firstname',
     enableKeyEvents : true
  });
  // Step 2 (assign listener to the text field)
  myTextField.on({
    keyup:{
      fn:function( thisField, evt, eOpts ){
        if(evt.getCharCode() === evt.ENTER){
        if (thisField.getValue()!=''){
          Ext.Msg.alert('Alert','Welcome: '+
thisField.getValue() );
        }
        }
      }
    }
  });
  newItems.push( myTextField );
  return newItems;
}
```

En el **`Step 1`**, creamos una nueva instancia de la clase **`Ext.form.field.Text`** y configuramos las propiedades **`fieldLabel`**, **`name`** y **`enableKeyEvents`**.

En el segundo paso, adjuntamos un event listener al campo. En este caso, el campo reaccionará al evento **`keyup`**. Entonces, cada vez que el usuario suelta una tecla en el teclado, se ejecutará la función callback. En el código, esperamos a que el usuario presione la tecla **Enter**, y cuando eso sucede, el código muestra un mensaje de alerta con el valor ingresado en el texto, si hay algún valor para el campo.

> **NOTA**
> 
> Ext JS proporciona un contenedor para el objeto de evento nativo. Este contenedor define muchas constantes, como la tecla Enter. Podemos ver todas las constantes disponibles en la documentación de Ext JS, en la clase **`Ext.event.Event`**.

Bien, ahora ejecutemos el código o actualice el navegador para ver cómo funciona el campo de texto. Puede ver algo como esto:

![06-05](images/06-05.png)

Como podemos ver en el ejemplo anterior, todos los campos se extienden desde la clase **`Observable`**. Por lo tanto, podemos agregar eventos y listeners a todos los campos de formulario. Deberíamos echar un vistazo a la documentación para ver todos los eventos disponibles que podemos utilizar para nuestro beneficio.

Otras propiedades comunes que se utilizan con frecuencia en el campo de texto son **`minLength`** y **`maxLength`**. Estas dos propiedades permiten restricciones de campo y poseen un rango de un número mínimo y un número máximo de caracteres de entrada que el campo puede aceptar. Cambiemos las propiedades del campo de texto para implementar estas características:

```js
var myTextField = Ext.create('Ext.form.field.Text',{
   fieldLabel:'Name',
   name:'firstname',
   enableKeyEvents : true,
   minLength : 4,
   minLengthText: 'Name is too short, at least {0} chars..!',
   maxLength : 25,
   maxLengthText: 'Name is too long, max length is {0} chars..!'
});
```

La propiedad **`minLength`** se establece en **`4`**, por lo que Ext JS handle/ensure que se cumpla la longitud mínima; de lo contrario, el campo se marcará como no válido y con un error. Vea la siguiente captura de pantalla para comprender esto:

![06-06](images/06-06.png)

Como puede observar, este campo está marcado como inválido (con un error), gracias al borde rojo. Ahora coloquemos el mouse sobre el campo y aparecerá una información sobre herramientas.

De forma predeterminada, los campos en Ext JS tienen una propiedad llamada **`msgTarget`**. Esta propiedad establecerá cómo se debe mostrar el mensaje de error en el campo. Los valores más comunes para esta propiedad son **`qtip`**, **`under`** y **`side`**. Además, Ext JS nos permite personalizar el mensaje de error con la ayuda de las propiedades **`minLengthText`** y **`maxLengthText`**. Considere la siguiente línea de código:

```js
minLengthText: 'Name is too short, at least {0} chars..!',
```

En la línea de código anterior, la parte **`{0}`** será como una variable/placeholder que será reemplazada automáticamente por Ext JS, usando el valor **`minLength`** si no se cumple la longitud mínima.

> **NOTA**
> 
> Puede definir la propiedad **`msgTarget`** en todos los componentes de campo que maneja Ext JS, y también puede asignar mensajes personalizados para errores según sus necesidades.

Es importante mencionar que debemos echar un vistazo a la documentación para ver todas las opciones de configuración, propiedades y eventos disponibles que podemos usar a nuestro favor, y usarlos de acuerdo a nuestras necesidades.

### El campo `number`

Cuando se trata de números, Ext JS tiene un campo numérico que solo acepta números como valores. De esta forma, podemos asegurarnos de que el usuario no podrá introducir ningún carácter inválido. También podemos personalizar el rango de valores a aceptar (valores mínimo y máximo), decimales y mucho más. Este campo viene con indicadores spinners/triggers integrados que nos permiten aumentar o disminuir el valor en él.

Agreguemos el siguiente código a nuestra función **`createFields`**:

```js
createFields: function (){
  var newItems=[];
  ...
  newItems.push( myTextField );
  var myAgeField = Ext.create('Ext.form.field.Number',{
    fieldLabel:'Age',
    name:'age',
    minValue: 18,
    maxValue: 70,
    allowDecimals : false
  });
  var myIncomeField = Ext.create('Ext.form.field.Number',{
    fieldLabel:'Income',
    name:'income',
    minValue: 0,
    allowDecimals : true,
    decimalPrecision : 2,
    negativeText : 'The income cannot be negative..!',
    msgTarget:'side'
  });
  newItems.push( myAgeField );
  newItems.push( myIncomeField );
  return newItems;
}
```

Agregamos dos campos, uno para la edad y otro para los ingresos. El campo **age** tiene un rango de valor de validación de 18 a 70; otros valores invalidarán este campo. El campo **income**, por otro lado, permite decimales (**`allowDecimals: true, decimalPrecision: 2,`**), pero no permite valores negativos. De lo contrario, obtendremos el mensaje de error **The income cannot be negative..!**. Ahora actualice el navegador y pruebe los nuevos campos; debería ver algo como la siguiente captura de pantalla:

![06-07](images/06-07.png)

Consulte el campo **Income**; establecemos la propiedad **`msgTarget`** en **`side`**. Esto crea un ícono de alerta al lado del campo (en el lado derecho), y cuando colocamos la flecha del mouse sobre el ícono, aparece la información sobre tooltip que muestra el mensaje de error establecido en la propiedad **`negativeText`**. También observe que el campo de edad está marcado como no válido porque el valor es **5**.

Observe que en el lado derecho del campo, está el spinner/trigger (flecha hacia arriba y flecha hacia abajo). Esto nos permite aumentar el valor de acuerdo con la propiedad **`step`**. De forma predeterminada, está establecido en **`1`**, pero podemos cambiarlo. Hagamos un pequeño cambio en el campo de los ingresos; agregamos la propiedad step y establecemos su valor en 500. Actualice el navegador y verifique el incremento al presionar el botón hacia arriba desde el spinner, como se muestra aquí:

![06-08](images/06-08.png)

Finalmente, necesitamos hacer un cambio en el campo de edad. Este campo no requiere que el spinner esté allí, por lo que está bien que ocultemos el spinner del campo numérico con la propiedad **`hideTrigger`**:

```js
var myAgeField = Ext.create('Ext.form.field.Number',{
   fieldLabel:'Age',
   name:'age',
   minValue: 18,
   maxValue: 70,
   allowDecimals: false,
   hideTrigger:true
});
```

De esta forma no se mostrarán los spinners y tendremos algo parecido a un campo de texto, con la posibilidad de aceptar solo números.

> 

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
