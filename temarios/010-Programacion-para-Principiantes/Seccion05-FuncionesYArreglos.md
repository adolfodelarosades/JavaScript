# 05 Funciones y arreglos

## Introducción a la sección

:+1:

## Explicación sobre las funciones

**Función**: Una función es un conjunto de líneas de código que realizan una tarea específica y pueden retornar algo, ayudan a no repetir código.

```js
function saludar(){
	.....
	.....
	.....
}
```

Las funciones pueden recibir parámetros (valores que se le envían a la función):

```js
function saludar(nombre){
	.....
	.....
	.....
}
```

Una función también puede retornar un valor:

```js
function sumar(a,b){
	return a + b;
}

let suma = sumar(10, 20); //Retorna 30

console.log("Suma = " + suma);
```

## Ejercicio básico de funciones

```js
// Función sumar
function sumar(a, b){
	return a + b;
}

let suma = sumar(10, 20);

console.log("La suma de 10 + 20 = " + suma);
```

## Separando código en funciones

```js
// Función que calcula la tabla de multiplicación
function tablaMultiplicacion(base, limite) {

	for (let i = 1; i <= limite; i++){
	  let resultado = 2 *i;
	  console.log(base + ' X ' + i + " = " + base * i);
	}
}

tablaMultiplicacion(9, 10);
tablaMultiplicacion(3, 10);
```

## Tarea práctica sobre funciones

```js
function calcularNota(nota) {
  if(nota >= 90) {
    notaLetra = 'A';
  } else if(nota >= 80) {
    notaLetra = 'B';
  } else if(nota >= 70) {
    notaLetra = 'C';
  } else if(nota >= 60) {
    notaLetra = 'D';
  } else {
    notaLetra = 'F';
  }
  console.log('La nota es ' + nota + ', equivale a una ' + notaLetra);
}

calcularNota(100);
calcularNota(80);
calcularNota(59);
```

## Explicación sobre los Arreglos - Arrays

Un arreglo es un conjunto de cosas similares.

**Arreglo vació**

`let flores = [];`

**Arreglo de Strings**

`let flores = ["Rosa", "Girasol", "Lirio"];`

**Extraer elementos del arreglo**

`let primerFlor = flores[0]; //Rosa`

Los índices de un array empiezan en 0.

## Ejercicio básico con arreglos

```js
let flores = ['Rosa', 'Girasol', 'Lirio'];

console.log(flores[0]); //Rosa
console.log(flores[1]); //Girasol
console.log(flores[2]); //Lirio
console.log(flores[3]); //undefined
```
## Ejercicio sobre arreglos #2

```js
let personas = ['Rosa', 'Adolfo', 'Laura'];
let salarios = [1000, 500, 2000];

for (let i = 0; i < personas.length; i++) {
	console.log( personas[i] + " tiene un salario de " + salarios[i])	
}
```

## Códigos fuente hasta el momento

:+1:
