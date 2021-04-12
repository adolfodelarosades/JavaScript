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

Como puede observar, la clase **`Employee`** ahora contiene el mixin, la clase **`Ext.util.Observable`**. Además, dentro de la función constructor, este mixin es inicializado por el código **`this.mixins.observable.constructor.call(this, config);`**. Esto significa que **`Ext.util.Observable`** estará al tanto de cualquier evento que se inicie dentro de la clase **`Employee`**, siempre que suceda.

> **NOTA**
> 
> Para comprender más sobre los mixins, consulte http://docs.sencha.com/extjs/5.1/5.1.1-apidocs/#!/api/Ext.Mixin.

La función **`quitJob`**, cuando se llama, lanzará el evento **`quit`**, pasando los parámetros **`this.getName(), new Date(), 2, 1, 'more params...'`**.

> **NOTA**
> 
> En versiones anteriores de Ext JS, teníamos que agregar el método **`addEvent(...)`** para crear o definir el evento (o eventos) adecuado dentro de la clase. Si está actualizando desde la versión 4, tenga en cuenta este cambio. La versión 5 es más flexible al respecto.

Ahora, necesitamos el código para escuchar el evento **'quit'** cuando se lanza. En Ext JS, tenemos la propiedad **`listeners`** que se usa para tales propósitos (listen/handle events). Modifiquemos el código donde instanciamos la clase:

```js
var patricia = Ext.create('Myapp.sample.Employee', {
   name:'Patricia',
   lastName:'Diaz',
   age:21,
   isOld:false,
   listeners:{
      'quit':function(EmployeeName, quitDate, param, paramb, paramc){
         console.log('Event quit launched');
         console.log('Employee:' + EmployeeName);
         console.log('Date:'+ Ext.util.Format.date(quitDate,'Y-m-d H:i'));
         console.log('Param :' + param);
         console.log('Param B:' + paramb);
         console.log('Param C:' + paramc);
      }
   }
});
console.log(Myapp.CompanyConstants.welcomeEmployee(patricia));
patricia.quitJob();
```

La propiedad **`listeners`** se incluyó en el objeto de configuración (la nueva clase **`Employee`**), por lo que de esta manera, podemos interceptar y manejar el evento **`quit`** cuando suceda. Ejecutemos el código en nuestro navegador y revisemos la salida de la consola, como se muestra en la siguiente captura de pantalla:

![05-01](images/05-01.png)

> **NOTA**
> 
> 

```js
patricia.on({
   'quit':function(EmployeeName, quitDate, param, paramb, paramc){
      console.log('Event quit launched');
      console.log('Employee:' + EmployeeName);
      console.log('Date:' + Ext.util.Format.date(quitDate, 'Y-m-d H:i'));
      console.log('Param :' + param);
      console.log('Param B:' + paramb);
      console.log('Param C:' + paramc);
   }
});
patricia.quitJob();
```

## Creando un Botón Simple

```js
var myButton = Ext.create('Ext.button.Button', {
   text:'My first button',
   tooltip:'Click me...!',
   renderTo:Ext.getBody()
});
```

![05-02](images/05-02.png)

```js
var myButton = Ext.create('Ext.button.Button', {
   text:'My first small button',
   scale:'small',
   renderTo:Ext.getBody()
});

var myButtonB = Ext.create('Ext.button.Button', {
   text:'My first medium button',
   scale:'medium',
   renderTo:Ext.getBody()
});

var myButtonC = Ext.create('Ext.button.Button', {
   text:'My first large button',
   scale:'large',
   renderTo:Ext.getBody()
});
```

![05-03](images/05-03.png)

### Configuración de Iconos en Botones


```css
.addicon-16{
   background:transparent url('images/add_16x16.png') center 0 no-repeat !important;
}
.addicon-24{
   background:transparent url('images/add_24x24.png') center 0 no-repeat !important;
}
.addicon-32{
   background:transparent url('images/add_32x32.png') center 0 no-repeat !important;
}
```

```js
var myButton = Ext.create('Ext.button.Button', {
   text:'My first small button',
   iconCls:'addicon-16',
   scale:'small',
   renderTo:Ext.getBody()
});

var myButtonB = Ext.create('Ext.button.Button', {
   text:'My first medium button',
   iconCls:'addicon-24',
   scale:'medium',
   renderTo:Ext.getBody()
});

var myButtonC = Ext.create('Ext.button.Button',{
   text:'My first large button',
   iconCls:'addicon-32',
   scale:'large',
   renderTo:Ext.getBody()
});
```

![05-04](images/05-04.png)

### Alineación de Iconos en Botones

```js
var myButtonA = Ext.create('Ext.button.Button',{
   text:'left icon',
   iconCls:'addicon-16',
   iconAlign:'left',
   renderTo:Ext.getBody()
});

var myButtonB = Ext.create('Ext.button.Button',{
   text:'top icon',
   iconCls:'addicon-16',
   iconAlign:'top',
   renderTo:Ext.getBody()
});

var myButtonC = Ext.create('Ext.button.Button',{
   text:'right icon',
   iconCls:'addicon-16',
   iconAlign:'right',
   renderTo:Ext.getBody()
});

var myButtonD = Ext.create('Ext.button.Button',{
   text:'bottom icon',
   iconCls:'addicon-16',
   iconAlign:'bottom',
   renderTo:Ext.getBody()
});
```

![05-05](images/05-05.png)

#### Manejo de Eventos del Botón

```js
myButtonA.on('click', function(){
   Ext.Msg.alert("Click event", "You clicked left icon button..!");
});
```

![05-06](images/05-06.png)

## Botones Segmentados

```js
var mySegmentedbuttons = Ext.create('Ext.button.Segmented',{
   renderTo:'segmentedbuttons',
   vertical:false,
   items:[{
      xtype: 'button', text:'1st button', iconCls:'addicon-16'
   },{
      text:'2nd button', iconCls:'addicon-16'
   },{
      text:'3th button', iconCls:'addicon-16'
   },{
      text:'4th button', iconCls:'addicon-16'
   }]
});
```

![05-07](images/05-07.png)

![05-08](images/05-08.png)

## Agregar Menús

```js
var myButton = Ext.create('Ext.button.Button',{
   text:'Add payment method...',
   iconCls:'addicon-32',
   iconAlign:'left',
   scale:'large',
   renderTo:'normalbuttons',
   menu:[
      {text:'Master Card'},
      {text:'Visa'},
      {text:'PayPal'},
      {text:'Other...'}
   ]
});
```

![05-09](images/05-09.png)

```js
//Step 1
var menuItemA = Ext.create('Ext.menu.Item',{text:'Master card'});
//Step 2
var menu = Ext.create('Ext.menu.Menu',{
   items : [  //Step 3
      menuItemA,   // Variable
      Ext.create('Ext.menu.Item',{text:'Visa'}), // constructor
      {text:'Paypal'} //object config
   ]
});
var myButton = Ext.create('Ext.button.Button',{
   text:'Add payment method...',
   iconCls:'addicon-32',
   iconAlign:'left',
   scale:'large',
   renderTo:'normalbuttons',
   menu:menu
});
```

```js
items : [ //Step 3
   menuItemA,  // Variable
   Ext.create( 'Ext.menu.Item' ,{
      text:'American Express'
   }), // constructor
   {text:'Other'} //object config
]
```

![05-10](images/05-10.png)

```js
var myButton = Ext.create('Ext.button.Button',{
   text:'Add payment method...',
   iconCls:'addicon-32',
   iconAlign:'left',
   scale:'large',
   renderTo:'normalbuttons',
   menu:[{
      text:'Master Card',
      listeners:{  // Option 1
         click:function(){
            Ext.Msg.alert("Click event", "You selected Master Card..!");
         }
      }
   },{
      text:'Visa', //Option 2
      handler: onMenuItemClick
   },{
      text:'PayPal',
      listeners:{ //Option 3
         'click':{fn: onMenuItemClick , single:true}
      }
   },{
      text:'Other...',
      handler: onMenuItemClick
   }]
});
function onMenuItemClick (itemBtn, Event){
   var optionString = itemBtn.text;
   Ext.Msg.alert("Click event","You selected " + optionString + " ..!");
}
```

> **NOTA**
> 
> 

```js
var optionString = itemBtn.text;
```

## Toolbars

```js
var myPanel = Ext.create( 'Ext.panel.Panel' ,{
   title: 'My first toolbar...',
   width: 450,
   height: 200,
   dockedItems: [{ //Step 1
      xtype : 'toolbar',
      dock: 'top', //Step 2
      items: [
         {text: 'New record'},
         {text: 'Edit record'},
         {text: 'Remove record'}
      ]
   }],
   renderTo:Ext.getBody()
});
```

```js
items:[
   {text:'New', iconCls:'addicon-16'},
   {text:'Edit', iconCls:'editicon-16'},
   {text:'Remove', iconCls:'deleteicon-16'},
   {text:'Export', iconCls:'export-16'},
   {text:'Print', iconCls:'print-16'},
   {text:'Help', iconCls:'help-16'}
]
```

```css
.addicon-16{ background:transparent url('../images/add_16x16.png') center 0 no-repeat !important; }
.deleteicon-16{ background:transparent url('../images/delete.png') center 0 no-repeat !important; }
.editicon-16{ background:transparent url('../images/pencil.png') center 0 no-repeat !important; }
.help-16{ background:transparent url('../images/help.png') center 0 no-repeat !important; }
.print-16{ background:transparent url('../images/printer.png') center 0 no-repeat !important; }
.export-16{ background:transparent url('../images/page_go.png') center 0 no-repeat !important; }
```

![05-11](images/05-11.png)

### Grupos de Botones de la Toolbars

```js
var myPanel = Ext.create('Ext.panel.Panel',{
   title:'My first toolbar...',
   width:600,
   height:200,
   dockedItems:[{ //Step 1
      xtype : 'toolbar',
      dock: 'top', //Step 2
      items:[
         { xtype:'buttongroup',
            title:'Actions',
            items:[
               {text: 'New', iconCls: 'addicon-16'},
               {text: 'Edit', iconCls: 'editicon-16'},
               {text: 'Remove', iconCls: 'deleteicon-16'}
            ]
         },{
            xtype: 'buttongroup',
            title: 'Print / Export & Help',
            items:[
               {text: 'Export', iconCls: 'export-16'},
               {text: 'Print', iconCls: 'print-16'},
               {text: 'Help', iconCls: 'help-16'}
            ]
         }
      ]
   }],
   renderTo:Ext.getBody()
});
```

![05-12](images/05-12.png)

```js
var myPanel = Ext.create('Ext.panel.Panel',{
   title:'My first toolbar...',
   width:600,
   height:200,
   dockedItems:[{ //Step 1
      xtype : 'toolbar',
      dock: 'top', //Step 2
      items:[{ 
         xtype:'buttongroup',
         title:'Actions',
         columns:2,
         items:[
            {text:'New', iconCls:'addicon-32', scale:'large', rowspan:2, iconAlign:'top' },
            {text:'Edit', iconCls:'editicon-16'},
            {text:'Remove', iconCls:'deleteicon-16'}
         ]
      },{
         xtype:'buttongroup', title:'Print / Export & Help',
         defaults:{scale:'large', iconAlign:'top'},
         items:[
            {text:'Export', iconCls:'export-32'},
            {text:'Print', iconCls:'print-32'}
         ]
      },{
         xtype:'buttongroup', title:'Help',
         items:[
            {text:'Help', iconCls:'help-32', scale:'large', iconAlign:'bottom' }
         ]
      }]
   }],
   renderTo:Ext.getBody()
});
```

![05-13](images/05-13.png)

## La Breadcrumb Bar

```js
Ext.define('Myapp.sample.store.mainMenu', {
   extend: 'Ext.data.TreeStore',
   root: {
      text: 'My app',
      expanded: true,
      children: [{
         text: 'Modules',
         expanded: true,
         children: [
            {leaf: true, text: 'Employees'},
            {leaf: true, text: 'Customers'},
            {leaf: true, text: 'Products'}
         ]
      },{
         text: 'Market',
         expanded: true,
         children: [
            {leaf: true, text: 'Sales'},
            {leaf: true, text: 'Budgets'},
            {leaf: true, text: 'SEO'},
            {leaf: true, text: 'Statistics'}
         ]
      },{
         text: 'Support',
         iconCls:'help-16',
         children: [
            {leaf: true, text: 'Submit a ticket'},
            {leaf: true, text: 'Forum'},
            {leaf: true, text: 'Visit our web site'}
         ]
      },
      {leaf: true, text: 'Reports'},
      {leaf: true, text: 'Charts'}
      ]
   }
});
```

```js
//step 1
var myMenuStore = Ext.create('Myapp.sample.store.mainMenu',{});
var myPanel = Ext.create('Ext.panel.Panel',{
   title:'My first breadcrumb bar...',
   width:600,
   height:200,
   dockedItems:[{ //Step 2
      xtype : 'breadcrumb',
      dock: 'top',
      store: myMenuStore,
      showIcons: true,
      selection: myMenuStore.getRoot().childNodes[2].childNodes[0]
   }],
   renderTo:Ext.getBody()
});
```

![05-14](images/05-14.png)

```js
{
   text: 'Support', iconCls:'help-16',
   children: [
      {leaf: true, text: 'Submit a ticket'},
      {leaf: true, text: 'Forum'},
      {leaf: true, text: 'Visit our web site'}
   ]
}
```

![05-15](images/05-15.png)

![05-16](images/05-16.png)

### Manejo de Selecciones en la Breadcrumb Bar

```js
dockedItems:[{
   xtype : 'breadcrumb',
   dock: 'top',
   store: myMenuStore,
   showIcons: true,
   selection: myMenuStore.getRoot().childNodes[2].childNodes[0],
   listeners:{
      'selectionchange':{
         fn:function(mybreadcrumb, node, eOpts){
            var panel = mybreadcrumb.up('panel');
            panel.update( 'This is the zone for:<b>' +  node.data.text + '</b>' );
         },
         delay:200
       }
   }
}],
```

![05-17](images/05-17.png)

## El Menú Principal de Nuestra Aplicación

![05-18](images/05-18.png)

> **NOTA**
> 
> 

> **NOTA**
> 
> 

```js
Ext.define('MyApp.view.Viewport',{
   extend: 'Ext.container.Viewport',
   layout: 'fit',
   initComponent: function(){
      var me = this;
      me.items = [{
         xtype: 'panel',
      }];
      me.callParent();
   }
});
```

```js
me.items = [{
   xtype: 'panel',
}];
```

```js
dockedItems: [{
   xtype: 'toolbar', docked:'top',
   items: [{
      text: 'Home', iconCls: 'home-16',
      menu:[
         {text: 'Categories', iconCls: 'categories-16'},
         {text: 'Products', iconCls: 'products-16'},
         {text: 'Clients', iconCls: 'clients-16' },
         {text: 'Invoices', iconCls: 'invoices-16'}
      ]
   },{
      text: 'Help', iconCls: 'help-16',
      menu: {
         xtype: 'menu',
         items: [
            {xtype: 'menuitem', text: 'Submit a support ticket'},
            {xtype: 'menuitem', text: 'Forum'},
            {xtype: 'menuitem', text: 'About...'}
         ]
      }
   },
   {xtype: 'tbfill'},
   {xtype: 'tbtext', text: 'User: Brett Fravre'}
   ]
}]
```

```js
Ext.onReady(function(){
   Ext.create("MyApp.view.Viewport");
});
```

![05-19](images/05-19.png)

```js
dockedItems : [{
   xtype : 'toolbar', docked:'top',
   //your code here…
},
{
   xtype : 'toolbar', dock:'bottom',
   items : [
      {xtype: 'tbtext', text: '<b>Status :</b>Connected'},
      {xtype: 'tbfill' },
      {text:'', iconCls: 'help-16'}
   ]
}]
```


![05-20](images/05-20.png)

> **TIP**
> 
> 

![05-21](images/05-21.png)

![05-22](images/05-22.png)

```js
```
## Resumen 


