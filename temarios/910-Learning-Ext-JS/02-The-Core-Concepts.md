# 2. Los Conceptos Básicos

* El sistema de clases
   * Convenciones de nombres
   * Escribiendo tu primera clase
   * Herencia simple
   * Preprocesadores y posprocesadores
   * Mezcla de muchas clases (el uso de mixins)
   * Una explicación de mixins
      * Usando la propiedad mixinConfig
      * Configuraciones
   * Métodos y propiedades estáticos
      * Explicación
   * La clase Singleton
   * Aliases
* Carga de clases bajo demanda
   * Habilitando el loader
* Trabajando con el DOM
   * Obteniendo elementos
   * Query: ¿cómo los encontramos?
   * Manipulación del DOM: ¿cómo lo cambiamos?
* Resumen

En este capítulo, aprenderá sobre el sistema de clases, que se introdujo por primera vez en Ext JS versión 4. También aprenderá cómo cargar clases dinámicamente y cómo interactuar con el **Document Object Model (DOM)** para modificar la estructura del árbol DOM para nuestra conveniencia.

Debe saber que JavaScript no tiene clases (prototype-oriented); sin embargo, podemos emularlo utilizando el objeto **`prototype`** y otras técnicas. Una de las principales características de Ext JS es que desde la versión 4, todo el código del framework se desarrolló con una estructura basada en clases. Junto con las convenciones de nomenclatura, es fácil de aprender y comprender, y mantener el código organizado, estructurado y fácil de mantener.

Conocer y comprender el concepto del **Object-Oriented Programming System (OOPS)** es muy importante. Es posible que este libro no sea una guía enfocada en el concepto de OOPS, pero aprenderá cómo podemos usar e implementar este concepto en Ext JS.

Los siguientes son los temas principales de este capítulo, que debe comprender bien antes de pasar a otras partes de la library:

* El sistema de clases(class system)
* Carga de clases bajo demanda
* Trabajando con el DOM

## El sistema de clases (class system)

En la versión 4, el sistema de clases se rediseñó por completo y se agregaron nuevas funciones. Se convirtió en una forma más poderosa de ampliar y crear clases. Y Ext JS 5 mantiene la misma estructura y consistencia que la versión 4.

Para crear clases, Ext JS usa el objeto **`Ext.ClassManager`** internamente para administrar las asociaciones entre los nombres, alias o nombres alternativos que definimos. Y todas las clases (existentes y nuevas) usan **`Ext.Base`** como código base.

No se recomienda utilizar estas clases directamente; en su lugar, deberíamos usar las siguientes abreviaturas:

* **`Ext.define`**: Esta abreviatura se usa para crear una nueva clase, extender una clase o siempre que necesitemos aplicar alguna override(s) en una clase.

* **`Ext.create`**: Esta abreviatura crea una nueva instancia de una clase, utilizando la clase **`fullname`**, la clase **`alias`** o la clase  **`alternate name`**. Usando cualquiera de estas opciones, el administrador de clases maneja el mapeo correcto para crear la clase. También podemos usar esta abreviatura para crear objetos a partir de una clase existente.

* **`Ext.widget`**: Esta abreviatura se usa para crear un widget usando la propiedad **`xtype`** (alias) o un objeto de configuración.

> **NOTA**<br>
> Alias es un short name para una clase, que generalmente es fácil de recordar y manejar en el código, por ejemplo, **`Ext.grid.column.Action`** tiene un alias que es **`actioncolumn`** . La lista completa se puede encontrar aquí: http://docs.sencha.com/extjs/5.1/5.1.1-apidocs/#!/api/Ext.enums.Widget.

### Convenciones de Nombres

Ext JS utiliza convenciones de nomenclatura coherentes en todo el framework. Esto le permite tener classes, namespaces, filenames, etc., para mantener una estructura organizada. Como parte de las convenciones de codificación utilizadas por Sencha, existen algunas reglas básicas:

* Los nombres pueden usar caracteres alfanuméricos y usted puede usar números, pero como convención, los números de reglas pueden usarse para términos técnicos. El uso de guiones bajos o guiones no puede usarse como una regla de convención, pero no es imposible usarlos. Por ejemplo:
   
   * **`MyApp.utils-common.string-renderers`** (incorrecto)
   * **`MyApp.utils.Md5encyption`** (correcto)
   * **`MyApp.reportFormats.FM160`** (correcto)

* Los nombres deben agruparse en **`packages/namespaces`**, espaciados utilizando la notación de puntos del objeto como **`(namespace).(namespace).(class)`**. No puede repetir el espacio de nombres de nivel superior seguido del nombre de la clase. Por ejemplo:

   * **`MyApp.EmployeeApp`** (correcto)
   * **`MyApp.EmployeeApp.EmployeeClass`** (incorrectono; también esto se interpretará como una propiedad en lugar de una clase)

* El nombre de las clases de nivel superior debe estar escrito en formato camel-cased. Los grupos y agrupación de namespaces de la clase de nivel superior debe estar en minúsculas (nuevamente como una convención, pero no prohibido). Por ejemplo:

   * **`MyApp.`grids`.EmployeesGrid`**
   * **`MyApp.`data.clients`.SalesReport`**

### Escribiendo tu primera clase
### Herencia simple
### Preprocesadores y posprocesadores
### Mezcla de muchas clases (el uso de mixins)
### Una explicación de mixins
#### Usando la propiedad mixinConfig
#### Configuraciones
### Métodos y propiedades estáticos
#### Explicación
### La clase Singleton
### Aliases
## Carga de clases bajo demanda
### Habilitando el loader
## Trabajando con el DOM
### Obteniendo elementos
### Query: ¿cómo los encontramos?
### Manipulación del DOM: ¿cómo lo cambiamos?
## Resumen
