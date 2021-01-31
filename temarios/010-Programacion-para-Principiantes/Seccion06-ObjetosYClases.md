# 06 Objetos y Clases

## Introducción a la sección
:+1:

## Explicación sobre objetos

**Objeto:** Representación abstracta de una cosa de la vida real.

Los objetos son variables que dentro de sí tienen propiedades.

```js
let carro = {
	color: 'blanco',
	traccion: '4x4',
	llantas: 4,
	puertas: 5,
	marca:'Mitsubishi'
}

carro.color; //blanco
carro.llantas; //4
```

Para acceder a las propiedades de un objeto usamos la notación de punto.

## Ejercicio práctico sobre objetos

```js
let persona = {
	nombre: 'Fernando',
	edad: 32,
	estatura: 1.79
}

function describirPersona( p) {
	console.log( `${ p.nombre } tiene una edad de ${ p.edad } y mide ${ p.estatura}`); //Fernando tiene una edad de 32 y mide 1.79
}

console.log(persona); //{nombre: "Fernando", edad: 32, estatura: 1.79}
console.log(persona.nombre); //Fernando
console.log(persona.edad); //32

describirPersona(persona);
```

## Arreglos de objetos

```js
//Arreglo de Objetos
let persona1 = {
	nombre: 'Fernando',
	edad: 32,
}

let persona2 = {
	nombre: 'Melissa',
	edad: 27,
}

let persona3 = {
	nombre: 'Juan',
	edad: 40,
}

let personas = [persona1, persona2, persona3];

console.log(personas); //(3) [{…}, {…}, {…}]
						//0: {nombre: "Fernando", edad: 32}
						//1: {nombre: "Melissa", edad: 27}
						//2: {nombre: "Juan", edad: 40}

for( let i = 0; i < personas.length; i++){
	console.log(`${ personas[i].nombre } -- ${ personas[i].edad }`);
}

```

## Explicación sobre las clases

**Clases:** Al igual que los objetos, las clases pueden ser representaciones abstractas de cosas de la vida real, pero sirven para crear varias instancias de una misma clase, son como moldes para hacer galletas.

Los nombres de las clases comienzan con mayúsculas. 

```js
class Galleta {}

let galletaUno = new Galleta();
let galletaDos = new Galleta();

```

Las clases también tienen propiedades como los objetos.

```js
class Galleta {
	sabor
	forma
	fechaCreacion
}
```

Todas las clases tienen una función interna llamada **constructor**, cuando se crea una instancia de la clase, se ejecuta esta función. 

```js
class Galleta{
	constructor(forma, sabor){
		this.forma = forma;
		this.sabor = sabor;
		this.fechaCreacion = 'HOY'
	}
	
}
```

Una clase además  de tener propiedades también puede tener **Métodos** que son funciones relacionadas a la clase. Y cualquier variable que sea una instancia de la clase, tendrá esas funciones.

Por ejemplo, podemos tener una clase **Carro** el cual puede tener las siguientes propiedades y métodos.

Propiedades

1. Número de puertas
2. Número de llantas
3. Color
4. Marca

Métodos

1. encenderCarro()
2. apagarCarro()
3. cambiarMarcha()

Podemos instanciar esta clase para crear dos carros diferentes

```js
new Carro('Seda');
new Carro('Jeep');
```

## Ejercicio práctico - Clases

```js
//Creando un objeto carro1
let carro1 = {
	marca: 'Toyota',
	tipo: 'Sedan',
	puertas: 3,
	creado: 'Hoy'
}

//Creando una clase Carro
class Carro{

	constructor(marca, tipo, puertas){
		this.marca = marca;
		this.tipo = tipo;
		this.puertas = puertas;
		this.creado = 'Hoy'
	}
}

//Instanciando la clase Carro
let carro2 = new Carro('Masda', 'Sedan', 2);

console.log(carro1); //{marca: "Toyota", tipo: "Sedan", puertas: 3, creado: "Hoy"}
console.log(carro2); //Carro {marca: "Masda", tipo: "Sedan", puertas: 2, creado: "Hoy"}

```

Observe que uno es un objeto y otro es una instancia de la clase Carro.

## Métodos de clase

```js

//Creando una clase Carro
class Carro{

	constructor(marca, tipo, puertas){
		this.marca = marca;
		this.tipo = tipo;
		this.puertas = puertas;
		this.creado = 'Hoy'
		this.encendido = false;
		this.gasolina = 100;
	}

	//Métodos
	encenderCarro(){
		if (!this.encendido) {
			this.encendido = true;
			console.log('El carro esta encendido');
		}else {
			console.error('El carro YA está encendido, no lo puedes volver a encender.')
		}

		//OJO con esto, cada que se ejecuta este método imprime la 
		//instancia de Carro, para no estar haciendo un console.log aparte
		//recordar que lo que se retorne se pinta en consola.
		return this;
	}

	realizarViaje(consumo){
		/*
		if (!this.encendido) {
			console.log('Debes encender primero el carro.');
		}else{
			if(consumo > this.gasolina){
				console.log('La gasolina que tienes ' + this.gasolina + ' no es suficiente para realizar un viaje que consume ' + consumo);
			}else {
				this.gasolina = this.gasolina - consumo;
				console.log('Viaje realizado!!! Le queda ' + this.gasolina + '% de gasolina');
		}
		*/

		//Otra forma de escribir el código anterior es:
		if (!this.encendido) return console.log('Debes encender primero el carro.');

		if(consumo > this.gasolina) return console.log('La gasolina que tienes es de ' + this.gasolina + ' no es suficiente para realizar un viaje que consume ' + consumo);

		this.gasolina = this.gasolina - consumo;
		return console.log('Viaje realizado!!! Le queda ' + this.gasolina + '% de gasolina');

	}
}

//Instanciando la clase Carro
let carro1 = new Carro('Masda', 'Sedan', 2);

console.log(carro1); //Carro {marca: "Masda", tipo: "Sedan", puertas: 2, creado: "Hoy"}
```

## Código fuente de la sección

:+1:
