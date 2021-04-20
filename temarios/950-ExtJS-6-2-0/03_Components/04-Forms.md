# Forms

Un [Form Panel](https://docs.sencha.com/extjs/6.2.0/classic/Ext.form.Panel.html)  no es más que un [Panel](https://docs.sencha.com/extjs/6.2.0/classic/Ext.panel.Panel.html) básico con capacidades de manejo de formularios agregadas. Los Form Panels se pueden utilizar en toda una [aplicación](https://docs.sencha.com/extjs/6.2.0/classic/Ext.html#application) Ext siempre que sea necesario recopilar datos del usuario.

Además, los Form Panels pueden utilizar cualquier [Container Layout](), lo que proporciona una forma cómoda y flexible de gestionar el posicionamiento de sus campos. Los Form Panels también se pueden vincular a un [Model](), lo que facilita la carga y el envío de datos al servidor.

Debajo del capó, un Form Panel envuelve un [Basic Form]() que maneja todos sus servicios de administración de campos de entrada, validación, envío y carga de formularios. Esto significa que muchas de las opciones de configuración de un Basic Form se pueden utilizar directamente en un Form Panel.

## Basic Form Panel

Para comenzar, aquí se explica cómo crear un simple Form que recopile datos del usuario:

```js
Ext.create('Ext.form.Panel', {
    renderTo: document.body,
    title: 'User Form',
    height: 350,
    width: 300,
    bodyPadding: 10,
    defaultType: 'textfield',
    items: [
        {
            fieldLabel: 'First Name',
            name: 'firstName'
        },
        {
            fieldLabel: 'Last Name',
            name: 'lastName'
        },
        {
            xtype: 'datefield',
            fieldLabel: 'Date of Birth',
            name: 'birthDate'
        }
    ]
});
```

![01-Form](/temarios/950-ExtJS-6-2-0/images/01-Form.png)


Este Form se representa en el cuerpo del documento y tiene tres [Fields](): "First Name", "Last Name" y "Date of Birth". Los campos se agregan al Form Panel utilizando la configuración de [items]().

La configuración [fieldLabel]() define qué texto aparecerá en la etiqueta junto al campo, y la configuración del [name]() se convierte en el atributo **`name`** del campo HTML subyacente.

Observe cómo este Form Panel tiene un [defaultType]() de **'textfield'**. Esto significa que cualquiera de sus elementos que no tienen un [xtype]() especificado (los campos "First Name" y "Last Name" en este ejemplo), son [Text Fields]().

El campo "Date of Birth", por otro lado, tiene su **`xtype`** configurado explícitamente como **'datefield'**, lo que lo convierte en un [Date Field](). Los Date Field solo contienen datos de fecha válidos y vienen con un [DatePicker]() para seleccionar una fecha.


### 🔴 Basic Form Panel `01-Basic-Form-Panel.html`

http://127.0.0.1:5500/950-ExtJS-6-2-0/03-Components/04-Forms/01-Basic-Form-Panel.html

`01-Basic-Form-Panel.html`

```html
<!DOCTYPE html>
<html>
   <head>
    <title>Primera Aplicación Extjs</title>
    <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no"> 
      <link href = "https://cdnjs.cloudflare.com/ajax/libs/extjs/6.2.0/classic/theme-classic/resources/theme-classic-all.css" 
         rel = "stylesheet" />
      <script type = "text/javascript" 
         src = "https://cdnjs.cloudflare.com/ajax/libs/extjs/6.2.0/ext-all.js"></script>
      
      <script type = "text/javascript">
         Ext.onReady(function() {
            Ext.create('Ext.form.Panel', {
                renderTo: document.body,
                title: 'Formulario de Usuario',
                height: 350,
                width: 300,
                bodyPadding: 10,
                defaultType: 'textfield',
                items: [
                    {
                        fieldLabel: 'Nombre',
                        name: 'firstName'
                    },
                    {
                        fieldLabel: 'Apellido',
                        name: 'lastName'
                    },
                    {
                        xtype: 'datefield',
                        fieldLabel: 'Fecha de Nacimiento',
                        name: 'birthDate'
                    }
                ]
            });
         });
      </script>
   </head>
   
   <body></body>
</html>
```

![01-Basic-Form-Panel](/temarios/950-ExtJS-6-2-0/images/01-Basic-Form-Panel.png)

## Fields

### Field Types

Ext JS proporciona un conjunto de tipos de campo estándar listos para usar. Cualquiera de los campos del namespace **`Ext.form.field`** se puede utilizar en un Form Panel. Para obtener más información, consulte la documentación de la API para cada tipo de campo:

* **`Ext.form.field.Checkbox`**
* **`Ext.form.field.ComboBox`**
* **`Ext.form.field.Date`**
* **`Ext.form.field.Display`**
* **`Ext.form.field.File`**
* **`Ext.form.field.Hidden`**
* **`Ext.form.field.HtmlEditor`**
* **`Ext.form.field.Number`**
* **`Ext.form.field.Radio`**
* **`Ext.form.field.Text`**
* **`Ext.form.field.TextArea`**
* **`Ext.form.field.Time`**

### Validation

#### 1. Built-in Validations

Ext JS tiene soporte integrado para la validación en cualquier tipo de campo, y algunos campos tienen reglas de validación integradas.

Por ejemplo, si se ingresa un valor en un [Date Field]() y ese valor no se puede convertir en un **`Date`**, el campo tendrá la clase CSS **`x-form-invalid-field`** agregada a su elemento HTML.

Si es necesario, esta clase CSS se puede cambiar usando la configuración [invalidCls](). La adición de **`invalidCls`** agrega un borde rojo al campo de entrada (así como una decoración roja de "invalid underline" cuando se usa el Classic theme):

![02-Form](/temarios/950-ExtJS-6-2-0/images/02-Form.png)

Un campo que contenga datos no válidos también mostrará un mensaje de error. De forma predeterminada, este mensaje se muestra como información sobre un tool tip:

![03-Form](/temarios/950-ExtJS-6-2-0/images/03-Form.png)

Es fácil cambiar la ubicación del mensaje de error de un campo usando la configuración de [msgTarget](), y la configuración de [invalidText]() cambia el mensaje de error.

Cada campo proporciona su propia implementación de **`invalidText`** y muchos admiten el reemplazo de token en el mensaje de error.

Por ejemplo, en el texto **`invalidText`** de un Date Field, cualquier aparición de `"{0}"` se reemplazará con el valor del campo, y cualquier aparición de `"{1}"` se reemplazará con el [formato]() de fecha requerido.

El siguiente código demuestra colocar el mensaje de error directamente debajo del campo y personalizar el texto del mensaje de error:

```js
{
    xtype: 'datefield',
    fieldLabel: 'Date of Birth',
    name: 'birthDate',
    msgTarget: 'under', // location of the error message
    invalidText: '"{0}" bad. "{1}" good.' // custom error message text
}
```

![04-Form](/temarios/950-ExtJS-6-2-0/images/04-Form.png)


### 🔴 Built-in Validations `02-Basic-Form-Panel-Validation.html`

http://127.0.0.1:5500/950-ExtJS-6-2-0/03-Components/04-Forms/02-Basic-Form-Panel-Validation.html

`02-Basic-Form-Panel-Validation.html`

```html
<!DOCTYPE html>
<html>
   <head>
    <title>Primera Aplicación Extjs</title>
    <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no"> 
      <link href = "https://cdnjs.cloudflare.com/ajax/libs/extjs/6.2.0/classic/theme-classic/resources/theme-classic-all.css" 
         rel = "stylesheet" />
      <script type = "text/javascript" 
         src = "https://cdnjs.cloudflare.com/ajax/libs/extjs/6.2.0/ext-all.js"></script>
      
      <script type = "text/javascript">
         Ext.onReady(function() {
            Ext.create('Ext.form.Panel', {
                renderTo: document.body,
                title: 'Formulario de Usuario',
                height: 350,
                width: 300,
                bodyPadding: 10,
                defaultType: 'textfield',
                items: [
                    {
                        fieldLabel: 'Nombre',
                        name: 'firstName'
                    },
                    {
                        fieldLabel: 'Apellido',
                        name: 'lastName'
                    },
                    {
                        xtype: 'datefield',
                        fieldLabel: 'Fecha de Nacimiento',
                        name: 'birthDate',
                        msgTarget: 'under', // ubicación del mensaje de error
                        invalidText: '"{0}" mal. "{1}" bien.' // texto de mensaje de error personalizado
                    }
                ]
            });
         });
      </script>
   </head>
   
   <body></body>
</html>
```

![02-Basic-Form-Panel-Validation](/temarios/950-ExtJS-6-2-0/images/02-Basic-Form-Panel-Validation.png)

#### 2. Custom Validations

Algunos requisitos de validación no se pueden cumplir con las validaciones integradas. La forma más sencilla de implementar una validación personalizada es utilizar la configuración de expresiones regulares del campo de texto para aplicar las reglas de validación y la configuración de [maskRe]() para limitar qué caracteres se pueden escribir en el campo. A continuación, se muestra un ejemplo de un campo de texto que valida una hora.

```js
{
    xtype: 'textfield',
    fieldLabel: 'Last Login Time',
    name: 'loginTime',
    regex: /^([1-9]|1[0-9]):([0-5][0-9])(\s[a|p]m)$/i,
    maskRe: /[\d\s:amp]/i,
    invalidText: 'Not a valid time.  Must be in the format "12:34 PM".'
}
```

Si bien el método anterior funciona bien para validar un solo campo, no es práctico para una aplicación que tiene muchos campos que comparten la misma validación personalizada.

La clase [Ext.form.field.VTypes]() proporciona una solución para crear validaciones personalizadas reutilizables. Así es como se puede crear un validador de "time" personalizado:

```js
// custom Vtype for vtype:'time'
var timeTest = /^([1-9]|1[0-9]):([0-5][0-9])(\s[a|p]m)$/i;
Ext.apply(Ext.form.field.VTypes, {
    //  vtype validation function
    time: function(val, field) {
        return timeTest.test(val);
    },
    // vtype Text property: The error text to display when the validation function returns false
    timeText: 'Not a valid time.  Must be in the format "12:34 PM".',
    // vtype Mask property: The keystroke filter mask
    timeMask: /[\d\s:amp]/i
});
```

Una vez que se ha creado un validador personalizado, se puede usar en Text Fields en una aplicación usando la configuración [vtype]():

```js
{
    fieldLabel: 'Last Login Time',
    name: 'loginTime',
    vtype: 'time'
}
```

Para obtener más información sobre validaciones personalizadas, consulte la documentación de API para [VTypes]().

### 🔴 Custom Validations `03-Basic-Form-Panel-Custom-Validation.html`

http://127.0.0.1:5500/950-ExtJS-6-2-0/03-Components/04-Forms/03-Basic-Form-Panel-Custom-Validation.html

`03-Basic-Form-Panel-Custom-Validation.html`

```html
<!DOCTYPE html>
<html>
   <head>
    <title>Validation</title>
    <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no"> 
      <link href = "https://cdnjs.cloudflare.com/ajax/libs/extjs/6.2.0/classic/theme-classic/resources/theme-classic-all.css" 
         rel = "stylesheet" />
      <script type = "text/javascript" 
         src = "https://cdnjs.cloudflare.com/ajax/libs/extjs/6.2.0/ext-all.js"></script>
      
      <script type = "text/javascript">
         Ext.onReady(function() {
            Ext.create('Ext.form.Panel', {
                renderTo: document.body,
                title: 'Formulario de Usuario',
                height: 350,
                width: 300,
                bodyPadding: 10,
                defaultType: 'textfield',
                items: [
                    {
                        fieldLabel: 'Nombre',
                        name: 'firstName'
                    },
                    {
                        fieldLabel: 'Apellido',
                        name: 'lastName'
                    },
                    {
                        xtype: 'datefield',
                        fieldLabel: 'Fecha de Nacimiento',
                        name: 'birthDate',
                        msgTarget: 'under', // ubicación del mensaje de error
                        invalidText: '"{0}" mal. "{1}" bien.' // texto de mensaje de error personalizado
                    },
                    {
                        xtype: 'textfield',
                        fieldLabel: 'Hora del último inicio de sesión',
                        name: 'loginTime',
                        regex: /^([1-9]|1[0-9]):([0-5][0-9])(\s[a|p]m)$/i,
                        maskRe: /[\d\s:amp]/i,
                        msgTarget: 'under',
                        invalidText: 'No es una hora válida. Debe estar en el formato "12:34 PM".'
                     }
                ]
            });
         });
      </script>
   </head>
   
   <body></body>
</html>
```

![03-Basic-Form-Panel-Custom-Validation](/temarios/950-ExtJS-6-2-0/images/03-Basic-Form-Panel-Custom-Validation.png)

![03-02-Basic-Form-Panel-Custom-Validation](/temarios/950-ExtJS-6-2-0/images/03-02-Basic-Form-Panel-Custom-Validation.png)



### 🔴 Custom Validations `04-Basic-Form-Panel-Custom-Validation.html`

http://127.0.0.1:5500/950-ExtJS-6-2-0/03-Components/04-Forms/04-Basic-Form-Panel-Custom-Validation.html

`04-Basic-Form-Panel-Custom-Validation.html`

```html
<!DOCTYPE html>
<html>
   <head>
    <title>Validation</title>
    <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no"> 
      <link href = "https://cdnjs.cloudflare.com/ajax/libs/extjs/6.2.0/classic/theme-classic/resources/theme-classic-all.css" 
         rel = "stylesheet" />
      <script type = "text/javascript" 
         src = "https://cdnjs.cloudflare.com/ajax/libs/extjs/6.2.0/ext-all.js"></script>
      
      <script type = "text/javascript">
         Ext.onReady(function() {

            // custom Vtype for vtype:'time'
            var timeTest = /^([1-9]|1[0-9]):([0-5][0-9])(\s[a|p]m)$/i;
            Ext.apply(Ext.form.field.VTypes, {
               //  vtype validation function
               time: function(val, field) {
                  return timeTest.test(val);
               },
               // vtype Text property: El texto de error que se mostrará cuando la función de validación devuelva false
               timeText: 'No es una hora válida. Debe estar en el formato "12:34 PM".',
               // vtype Mask property: La máscara de filtro de pulsaciones de teclas
               timeMask: /[\d\s:amp]/i
            });

            Ext.create('Ext.form.Panel', {
                renderTo: document.body,
                title: 'Formulario de Usuario',
                height: 350,
                width: 300,
                bodyPadding: 10,
                defaultType: 'textfield',
                items: [
                    {
                        fieldLabel: 'Nombre',
                        name: 'firstName'
                    },
                    {
                        fieldLabel: 'Apellido',
                        name: 'lastName'
                    },
                    {
                        xtype: 'datefield',
                        fieldLabel: 'Fecha de Nacimiento',
                        name: 'birthDate',
                        msgTarget: 'under', // ubicación del mensaje de error
                        invalidText: '"{0}" mal. "{1}" bien.' // texto de mensaje de error personalizado
                    },
                    {
                        xtype: 'textfield',
                        fieldLabel: 'Hora del último inicio de sesión',
                        name: 'loginTime',
                        vtype: 'time',
                        msgTarget: 'under'
                     }
                ]
            });
         });
      </script>
   </head>
   
   <body></body>
</html>
```

![04-Basic-Form-Panel-Custom-Validation](/temarios/950-ExtJS-6-2-0/images/04-Basic-Form-Panel-Custom-Validation.png)

![04-02-Basic-Form-Panel-Custom-Validation](/temarios/950-ExtJS-6-2-0/images/04-02-Basic-Form-Panel-Custom-Validation.png)

## Handling Data (Handling Data)

### Submitting a Form (Enviar un formulario)

La forma más sencilla de enviar datos al servidor es utilizar la configuración [url]() de [Basic Form]. Dado que el [Form Panel] envuelve un Basic Form, podemos usar cualquiera de las opciones de configuración del Formulario básico directamente en un Form Panel:

```js
Ext.create('Ext.form.Panel', {
    ...
    url: 'add_user',
    items: [
        ...
    ]
});
```

El método [submit]() del formulario se puede utilizar para enviar datos a la **`url`** configurada:

```js
Ext.create('Ext.form.Panel', {
    ...
    url: 'add_user',
    items: [
        ...
    ],
    buttons: [
        {
            text: 'Submit',
            handler: function() {
                var form = this.up('form'); // get the form panel
                if (form.isValid()) { // make sure the form contains valid data before submitting
                    form.submit({
                        success: function(form, action) {
                           Ext.Msg.alert('Success', action.result.msg);
                        },
                        failure: function(form, action) {
                            Ext.Msg.alert('Failed', action.result.msg);
                        }
                    });
                } else { // display error alert if the data is invalid
                    Ext.Msg.alert('Invalid Data', 'Please correct form errors.')
                }
            }
        }
    ]
});
```

En el ejemplo anterior, un botón está configurado con un [handler] que maneja el envío de formularios. El handler realiza las siguientes acciones:

1. Primero, se debe adquirir una referencia al Form Panel.
2. Luego, se llama al método [isValid]() antes del envío para verificar que ninguno de los campos tenga errores de validación.
3. Finalmente, se llama al método **`submit`** y se pasan dos funciones callback: **`success`** y **`failure`**. Dentro de estas funciones de devolución de llamada, **`action.result`** se refiere a la respuesta JSON analizada.

El ejemplo anterior espera una respuesta JSON que se parece a esto:

```json
{ "success": true, "msg": "User added successfully" }
```

### 🔴 Submitting a Form `05-Submitting-a-Form.html`

http://127.0.0.1:5500/950-ExtJS-6-2-0/03-Components/04-Forms/05-Submitting-a-Form.html

`05-Submitting-a-Form.html`

```html
<!DOCTYPE html>
<html>
   <head>
    <title>Submitting a Form</title>
    <meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no"> 
      <link href = "https://cdnjs.cloudflare.com/ajax/libs/extjs/6.2.0/classic/theme-classic/resources/theme-classic-all.css" 
         rel = "stylesheet" />
      <script type = "text/javascript" 
         src = "https://cdnjs.cloudflare.com/ajax/libs/extjs/6.2.0/ext-all.js"></script>
      
      <script type = "text/javascript">
         Ext.onReady(function() {

            // custom Vtype for vtype:'time'
            var timeTest = /^([1-9]|1[0-9]):([0-5][0-9])(\s[a|p]m)$/i;
            Ext.apply(Ext.form.field.VTypes, {
               //  vtype validation function
               time: function(val, field) {
                  return timeTest.test(val);
               },
               // vtype Text property: El texto de error que se mostrará cuando la función de validación devuelva false
               timeText: 'No es una hora válida. Debe estar en el formato "12:34 PM".',
               // vtype Mask property: La máscara de filtro de pulsaciones de teclas
               timeMask: /[\d\s:amp]/i
            });

            Ext.create('Ext.form.Panel', {
                renderTo: document.body,
                title: 'Formulario de Usuario',
                height: 350,
                width: 300,
                bodyPadding: 10,
                defaultType: 'textfield',
                url: 'http://familiadelarosa.com/950-ExtJS-6-2-0/serverside/add_user_01.php',
                items: [
                    {
                        fieldLabel: 'Nombre',
                        name: 'firstName'
                    },
                    {
                        fieldLabel: 'Apellido',
                        name: 'lastName'
                    },
                    {
                        xtype: 'datefield',
                        fieldLabel: 'Fecha de Nacimiento',
                        name: 'birthDate',
                        msgTarget: 'under', // ubicación del mensaje de error
                        invalidText: '"{0}" mal. "{1}" bien.' // texto de mensaje de error personalizado
                    },
                    {
                        xtype: 'textfield',
                        fieldLabel: 'Hora del último inicio de sesión',
                        name: 'loginTime',
                        vtype: 'time',
                        msgTarget: 'under'
                     }
                ],
                buttons: [
                  {
                     text: 'Submit',
                     handler: function() {
                        var form = this.up('form'); // obtener el form panel
                        if (form.isValid()) { // asegúrese de que el formulario contenga datos válidos antes de enviar
                           form.submit({
                                 success: function(form, action) {
                                    Ext.Msg.alert('Éxitoso', action.result.msg);
                                 },
                                 failure: function(form, action) {
                                    Ext.Msg.alert('Fallido', action.result.msg);
                                 }
                           });
                        } else { // display error alert if the data is invalid
                           Ext.Msg.alert('Datos no válidos', 'Corrija los errores de formulario')
                        }
                     }
                  }
               ]
            });
         });
      </script>
   </head>
   
   <body></body>
</html>
```

En este ejercicio estamos invocando la URL http://familiadelarosa.com/950-ExtJS-6-2-0/serverside/add_user_01.php cuyo contenido es:

`add_user_01.php`

```php
<?php 
   header('Content-Type: application/json');
   header('Access-Control-Allow-Origin: *');
   header("Access-Control-Allow-Headers: X-API-KEY, Origin, X-Requested-With, Content-Type, Accept, Access-Control-Request-Method");
   header("Access-Control-Allow-Methods: GET, POST, OPTIONS, PUT, DELETE");
   header("Allow: GET, POST, OPTIONS, PUT, DELETE");
   $method = $_SERVER['REQUEST_METHOD'];
   if($method == "OPTIONS") {
      die();
   }

   echo '{
      "success" : true,
      "msg"     : "Usuario agregado exitosamente"
    }'; 

?>
```

o el URL http://familiadelarosa.com/950-ExtJS-6-2-0/serverside/add_user_02.php cuyo contenido es:

`add_user_02.php`

```php
<?php 
   header('Content-Type: application/json');
   header('Access-Control-Allow-Origin: *');
   header("Access-Control-Allow-Headers: X-API-KEY, Origin, X-Requested-With, Content-Type, Accept, Access-Control-Request-Method");
   header("Access-Control-Allow-Methods: GET, POST, OPTIONS, PUT, DELETE");
   header("Allow: GET, POST, OPTIONS, PUT, DELETE");
   $method = $_SERVER['REQUEST_METHOD'];
   if($method == "OPTIONS") {
      die();
   }

   echo '{
      "failure" : true,
      "msg"     : "El Usuario no ha sido agregado"
    }'; 

?>
```

En este caso ambos PHPs nos retornan un JSON para el caso de **success** o **failure** ya que no estamos insertando realmente el usuario sino haciendo una simulación al invocar estos URLs tenemos:

![add_user_01](/temarios/950-ExtJS-6-2-0/images/add_user_01.png)

![add_user_02](/temarios/950-ExtJS-6-2-0/images/add_user_02.png)

Al cargar el HTML tenemos:

![05-01-Submitting-a-Form](/temarios/950-ExtJS-6-2-0/images/05-01-Submitting-a-Form.png)

![05-02-Submitting-a-Form](/temarios/950-ExtJS-6-2-0/images/05-02-Submitting-a-Form.png)

![05-03-Submitting-a-Form](/temarios/950-ExtJS-6-2-0/images/05-03-Submitting-a-Form.png)

![05-04-Submitting-a-Form](/temarios/950-ExtJS-6-2-0/images/05-04-Submitting-a-Form.png)

Aquí estamos simulando que todo ha ido bien.

Ahora vamos a simular que el usuario no se añadio.

![05-05-Submitting-a-Form](/temarios/950-ExtJS-6-2-0/images/05-05-Submitting-a-Form.png)

![05-06-Submitting-a-Form](/temarios/950-ExtJS-6-2-0/images/05-06-Submitting-a-Form.png)



