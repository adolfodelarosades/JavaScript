# Capítulo 3: Componentes básicos

* Familiarizarse con los componentes básicos
   * Ext.Button
   * Ext.MessageBox
* Formularios y campos de formulario
   * Ext.form.Panel
* Fields
   * Ext.form.field.Text
   * Ext.form.field.Number
   * Ext.form.field.ComboBox
   * Ext.form.field.HtmlEditor
* La validación de campos del formulario
   * Eventos en el panel de formulario
   * Formulario de contenedores de campo
   * Ext.form.CheckboxGroup
   * Ext.form.FieldContainer
   * Ext.form.RadioGroup
   * Submitting a form
   * Menus y toolbar
* El diseño del formulario de comentarios del cliente
* Calculadora: un proyecto de muestra
   * La estructura de carpetas
      * App – app.js
   * MVC y MVVM – Revisión
      * Model
      * View
      * Controller
      * ViewController y Controller
      * View model
   * View – Main.js
   * Controller – MainController.js
   * ViewModel – MainViewModel.js
* Resumen

En este capítulo, aprenderá algunos de los componentes básicos disponibles Ext JS. Usaremos los conceptos aprendidos en los capítulos anteriores y en este capítulo para crear un proyecto de muestra. En este capítulo se tratarán los siguientes temas:

* Familiarizarse con los componentes básicos: buttons, text field, date picker, etcétera
* La validación del campo del formulario
* Menus y toolbars
* Un diseño de formulario de comentarios del cliente
* Calculadora: un proyecto de muestra

El objetivo principal del capítulo es crear un diseño de formulario y un proyecto de muestra de calculadora. La Figura 3.1 y la Figura 3.2 muestran el diseño del formulario de comentarios del cliente y el diseño de la calculadora, respectivamente.
Primero, si observa el diseño del formulario de comentarios de los clientes en la Figura 3.1, verá que hemos usado muchos controles, como una label, un text field.

La siguiente figura es el diseño del formulario **Customer Feedback**(Comentarios del cliente):

![03-01](images/03-01.png)

A continuación, puede ver el button y label: los controles más importantes utilizados en el diseño de calculadora en la Figura 3.2. Por lo tanto, primero aprenderá sobre los botones y los controladores. Más tarde, al final de este capítulo, crearemos el proyecto de la calculadora. En el proyecto de la calculadora, aprenderá cómo la vista y el controlador interactúan y funcionan juntos. También veremos cómo vincular la propiedad del modelo de vista a un campo en la vista.

La siguiente figura es el diseño de la calculadora:

![03-02](images/03-02.png)

## Familiarizarse con los componentes básicos

Ext JS viene con muchos controles útiles. Echemos un vistazo a algunos de los componentes:

### Ext.Button

Este es un control de uso común; el handler se utiliza para el evento de clic, como se muestra en el siguiente código:

   ```js
   Ext.create('Ext.Button', {
      text: 'My Button',
      renderTo: Ext.getBody(),
      handler: function() {
         alert('click');
      }
   });
   ```

![03-03](images/03-03.png)

Ya mencioné la ejecución del código de muestra en el Capítulo 2, pero me gustaría reiterar este punto nuevamente. Mientras lee, puede ejecutar esta muestra de código y la mayoría del otro código de muestra que veremos en este libro. Tu también puedes ejecútelos en tu máquina local o en Sencha Fiddle. Puedes visitar Sencha Fiddle en https://fiddle.sencha.com y coloque el código anterior en la función launch, ejecútelo y vea el resultado. Entonces, si va a https://fiddle.sencha.com, verá el siguiente código:

   ```js
   Ext.application({
      name : 'Fiddle',
      launch : function() {
         Ext.Msg.alert('Fiddle', 'Welcome to Sencha Fiddle!');
      }
   });
   ```
   
Ahora, pegue el código de muestra del botón como se muestra aquí, ejecútelo y vea el resultado:   

   ```js
   Ext.application({
      name : 'Fiddle',
      launch : function() {
         Ext.create('Ext.Button', {
            text: 'My Button',
            renderTo: Ext.getBody(),
            handler: function() {
               alert('click');
            }
         });
      }
   });
   ```
   
> **NOTA:** No todos los ejemplos se pueden ejecutar de esta manera, y no todos el código de muestra tiene representación visual.

También puede usar la configuración de los `listeners` para agregar uno o más event handlers, como se muestra en el siguiente código:

   ```js
   Ext.create('Ext.Button', {
      text: 'My Button',
      renderTo: Ext.getBody(),
      listeners: {
         click: {
            fn: function(){
               //Handle click event
               alert('click');
            }
         },
         mouseout: {
            fn: function(){
               //Handle double click event
               alert('Mouse out');
            }
         }
      }
   });
   ```
   
El código anterior crea un botón simple, pero puede crear muchas variaciones de botones. También puede crear un botón de enlace(link button), un botón con un menú, un botón de alternancia(toggle), etcétera.

Para crear un link button, establezca la propiedad `href`, como se muestra en el siguiente código:   

   ```js
   Ext.create('Ext.Button', {
      renderTo: Ext.getBody(),
      text: 'Link Button',
      href: 'http://www.sencha.com/'
   });
   ```
   
La salida del link button se muestra en la *Figura 3.4*. Al hacer clic en él, el enlace abrir:   

![03-04](images/03-04.png)

Puede crear un botón de menú(menu button) estableciendo la propiedad `menu`, como se muestra en el siguiente código:

   ```js
   Ext.create('Ext.Button', {
      text: 'My Button',
      renderTo: Ext.getBody(),
      menu: [{
         text: 'Item 1'
      }, {
         text: 'Item 2'
      }, {
         text: 'Item 3'
      }]
   });
   ```

La salida se muestra aquí:

![03-05](images/03-05.png)

`Ext.Button` tiene muchas otras propiedades, como `bind`, `cls`, `disabled`, `html`, `tooltip`, `tpl`, etc., que puede utilizar para personalizar el botón.

### Ext.MessageBox

La clase `Ext.window.MessageBox` proporciona la implementación del message box. `Ext.MessageBox` es una instancia única de esta clase. Puede usar `MessageBox` para mostrar un alerta, obtener confirmación, solicitar entrada, etc.

El siguiente código mostrará una alerta simple. Aquí, `Ext.Msg` es el alias de `Ext.Messagebox`:

   ```js
   Ext.Msg.alert('Info', 'Document saved!');   
   ```

Puede mostrar un cuadro de mensaje de confirmación con un botón de `yes` y `no` con el siguiente código:

   ```js
   Ext.Msg.confirm('Confirm', 'Are you want to cancel the updates?',
   function(button){
      if('yes'==button) {
      
      }
      else {
      
      }
   }
   );
   ```
   
Además, puede personalizar el cuadro de mensaje de la siguiente manera:   

   ```js
   Ext.MessageBox.show({
      title:'Save Changes?',
      msg: 'Do you want to save the file?',
      buttons: Ext.MessageBox.YESNO,
      fn: function(button){
         if('yes'==button)
         {
         
         }
         else if('no'==button)
         {
         
         }
      } ,
      icon: Ext.MessageBox.QUESTION
   });
   ```
La salida del código anterior es la siguiente:

![03-06](images/03-06.png)

## Formularios y campos de formulario

Ahora, echemos un vistazo a algunos de los componentes relacionados con el formulario.

### Ext.form.Panel

El panel de formularios hereda del panel y agrega funcionalidades relacionadas con los formularios, como gestión de campo, validación, envío, etc. El diseño predeterminado de el panel de formulario es un diseño de anclaje, pero puede cambiarlo si es necesario.

El panel de formulario tiene una configuración conveniente llamada `fieldDefaults`, que se puede utilizar para
especifique los valores de configuración predeterminados para todos los campos.

## Fields

Ext JS viene con tantos campos de formulario integrados listos para usar. Algunos de los los campos usados son:

   ```js
   Ext.form.field.Checkbox
   Ext.form.field.ComboBox
   Ext.form.field.Date
   Ext.form.field.File
   Ext.form.field.Hidden
   Ext.form.field.HtmlEditor
   Ext.form.field.Number
   Ext.form.field.Radio
   Ext.form.field.Text
   Ext.form.field.TextArea
   Ext.form.field.Time
   ```
   
Echemos un vistazo a algunos de estos campos de formulario aquí.   

### Ext.form.field.Text

Este es un campo de texto básico, pero tiene muchas propiedades y configuraciones útiles. Una de estas propiedades útil es `vtype` que se utiliza para la validación. Por ejemplo, puede configurar la propiedad `vtype` como un correo electrónico para validar la entrada para el correo electrónico válido, como se muestra en la siguiente código:

   ```js
   Ext.create('Ext.form.field.Text', {
      renderTo: Ext.getBody(),
      name: 'email',
      fieldLabel: 'Email',
      allowBlank: false,
      vtype: 'email'
   });
   ```

Aquí `allowBlank` es una propiedad de validación. Al establecer `allowBlank` en `false`, muestra el error de validación si el campo está en blanco.

### Ext.form.field.Number

El campo numérico se extiende desde el campo spinner, que a su vez se extiende desde el campo de texto. El campo de número proporciona varias opciones para manejar un valor numérico. El siguiente código generará un campo numérico que se muestra en la *Figura 3.7*:

   ```js
   Ext.create('Ext.form.field.Number', {
      renderTo: Ext.getBody(),
      name: 'Count',
      fieldLabel: 'Count',
      value: 0,
      maxValue: 10,
      minValue: 0
   });
   ```

![03-07](images/03-07.png)

Puede eliminar los botones spinner, las teclas de flecha y los listeners de la rueda del mouse con las
opciones de configuración: `hideTrigger`, `keyNavEnabled` y `mouseWheelEnabled` respectivamente.

### Ext.form.field.ComboBox

El siguiente código crea un dropdown(menú desplegable) con una lista de meses. El `combobox` tiene un config llamado `store`. El datastore proporciona los datos para el dropdown. El datastore es parte de los data packages de ExtJS, que cubriremos en detalle en los próximos capítulos.

Otra configuración importante en el `combobox` es `queryMode`. Esto puede ser local o remoto. Si configura esto como remoto, el datastore se cargará en tiempo de ejecución enviando una solicitud al servidor remoto:

   ```js
   var months = Ext.create('Ext.data.Store', {
      fields: ['abbr', 'name'],
      data: [
      {"abbr":"JAN", "name":"January"},
      {"abbr":"FEB", "name":"February"},
      {"abbr":"MAR", "name":"March"},
      {"abbr":"APR", "name":"April"},
      {"abbr":"MAY", "name":"May"},
      {"abbr":"JUN", "name":"June"},
      {"abbr":"JUL", "name":"July"},
      {"abbr":"AUG", "name":"August"},
      {"abbr":"SEP", "name":"September"},
      {"abbr":"OCT", "name":"October"},
      {"abbr":"NOV", "name":"November"},
      {"abbr":"DEC", "name":"December"}
      ]
   });
   
   Ext.create('Ext.form.ComboBox', {
      fieldLabel: 'Choose Month',
      store: months,
      queryMode: 'local',
      displayField: 'name',
      valueField: 'abbr',
      renderTo: Ext.getBody()
   });
   ```
La salida del código anterior es la siguiente:

![03-08](images/03-08.png)

### Ext.form.field.HtmlEditor

```js
```

![03-09](images/03-09.png)

## La validación de campos del formulario
### Eventos en el panel de formulario
### Formulario de contenedores de campo
### Ext.form.CheckboxGroup

```js
```

![03-10](images/03-10.png)

### Ext.form.FieldContainer

```js
```
![03-11](images/03-11.png)

### Ext.form.RadioGroup

```js
```


![03-12](images/03-12.png)

### Submitting a form

```js
```

### Menus y toolbar

![03-13](images/03-13.png)

```js
```

## El diseño del formulario customer feedback

![03-14](images/03-14.png)

```js
```

## Calculadora: un proyecto de muestra

![03-15](images/03-15.png)

### La estructura de carpetas

![03-16](images/03-16.png)

#### App – app.js

```js
```

### MVC y MVVM – Revisión
#### Model
#### View
#### Controller
#### ViewController y Controller
#### View model
### View – Main.js

```js
```

### Controller – MainController.js

```js
```

### ViewModel – MainViewModel.js

```js
```

## Resumen





