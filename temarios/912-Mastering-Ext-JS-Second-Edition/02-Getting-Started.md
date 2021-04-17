# 2. Getting Started
   * Preparing the development environment
* Presenting the application and its capabilities
   * The splash screen
   * The login screen
   * The main screen
   * User administration
   * MySQL table management
   * Content management control
   * Charts
* Creating the application with Sencha Cmd
   * A quick word about MVC
   * Creating the application
      * Looking out for changes with the watch command
      * Applying the first changes in our app
      * Understanding the Application.js file
* Creating the loading page
* Summary

En este libro, nos sumergiremos en el mundo de Sencha Ext JS 5 y exploraremos ejemplos del mundo real. También construiremos una aplicación completa desde cero, desde la fase de wireframe hasta la implementación en producción.

A lo largo de este libro, vamos a desarrollar una aplicación para administrar una tienda de alquiler de DVD. En este capítulo, presentaremos la aplicación y describiremos sus capacidades. También aprenderá a organizar los archivos de la aplicación, que se creará a lo largo de los capítulos de este libro. Este capítulo también presentará la maqueta (wireframe) de la aplicación y cómo empezar a organizar las pantallas (que es un paso muy importante y algunos desarrolladores se olvidan de hacerlo). En este capítulo, cubriremos:

* Preparar el entorno de desarrollo instalando el software necesario
* Presentando la aplicación y sus capacidades
* Creación de mockups/wireframes (maquetas/wireframes) de cada pantalla
* Creando la estructura de la aplicación usando Sencha Cmd
* Creando la loading page (página de carga) (pantalla de bienvenida)

## Preparando el Entorno de Desarrollo

La aplicación que vamos a desarrollar tiene una arquitectura muy sencilla. Vamos a usar Ext JS 5 en la interfaz, que se comunicará con un módulo del lado del servidor usando Ajax/JSON, que luego se comunicará con una base de datos.

El siguiente diagrama encapsula el párrafo anterior:

![02-01](images/02-01.png)

> **NOTA**
> 
> Si es un desarrollador de Java, puede encontrar un código de muestra sobre cómo integrar Java con Ext JS en http://goo.gl/rv76E2 y http://goo.gl/nNIRuQ.

> **NOTA**
> 
> 

## Presentación de la aplicación y sus capacidades.
### La pantalla de bienvenida

![02-02](images/02-02.png)

### La pantalla de inicio de sesión

![02-03](images/02-03.png)

### La pantalla principal

![02-04](images/02-04.png)

![02-05](images/02-05.png)

### Administración de Usuario

![02-06](images/02-06.png)

### Gestión de tablas MySQL

![02-07](images/02-07.png)

![02-08](images/02-08.png)


### Control de gestión de contenido

![02-09](images/02-09.png)

![02-10](images/02-10.png)

### Gráficos

![02-11](images/02-11.png)

## Creando la aplicación con Sencha Cmd
### Unas palabras breves sobre MVC

![02-12](images/02-12.png)

### Creando la aplicación

![02-13](images/02-13.png)

> **NOTA**
> 
> 

![02-14](images/02-14.png)

> **NOTA**
> 
> 

![02-15](images/02-15.png)

> **NOTA**
> 
> 

> **NOTA**
> 
> 


#### Buscando cambios con el comando watch

![02-16](images/02-16.png)

> **TIP**
> 
> 

![02-17](images/02-17.png)

![02-18](images/02-18.png)

> **TIP**
> 
> 
#### Aplicando los primeros cambios en nuestra aplicación
#### Comprensión del archivo Application.js

> **TIP**
> 
> 

![02-19](images/02-19.png)

## Creando la página de carga

![02-20](images/02-20.png)


![02-21](images/02-21.png)

![02-22](images/02-22.png)

> **NOTA**
> 
> 

> **NOTA**
> 
> 

![02-23](images/02-23.png)
![02-24](images/02-24.png)
![02-25](images/02-25.png)
![02-26](images/02-26.png)
![02-27](images/02-27.png)

> **TIP**
> 
> 

> **NOTA**
> 
> 

## Resumen

En este capítulo, exploramos la aplicación que implementaremos a lo largo de los capítulos de este libro con mucha profundidad. También cubrimos todos los requisitos para crear el entorno de desarrollo para esta aplicación. Aprendió a crear la estructura inicial de una aplicación Ext JS MVC.

También aprendió, a través de ejemplos, cómo crear una pantalla de presentación (también conocida como loading screen(pantalla de carga)), manipulando el DOM usando la clase **`Ext.dom.Element`**. Aprendió los pasos para iniciar una aplicación Ext JS y también aprendió la diferencia entre los métodos **`init`** y **`launch`** de **`Ext.application`**. Dejamos **`Application.js`** listo para mostrar su primera pantalla, que será una pantalla de inicio de sesión(login screen), y que aprenderá a implementar en el próximo capítulo.
