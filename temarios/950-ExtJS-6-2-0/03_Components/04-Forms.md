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

![01-Form](images/01-Form.png)

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

![01-Basic-Form-Panel](images/01-Basic-Form-Panel.png)

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

```html
```

```html
```
