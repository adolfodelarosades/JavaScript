# 08 Ejercicios de programación – lógica

## Introducción a la sección

:+1:

## Material de la sección

Ver archivo **tareas.pdf**

## 1- Convertir de Libras a Kilogramos

```js
let libras = 160;
let kg = libras/2.2046;

kg *= 100;
kg = Math.round(kg);
kg /=100;

console.log(libras +' libras equivalen a ' + kg + ' kilogramos'); //160 libras equivalen a 72.58 kilogramos
```

## 2- Convertir de kilómetros a millas

```js
let km = 20;
let millas = km * 0.62;

console.log(km +' km equivalen a ' + millas + ' millas');
```
## 3- Calcule el área de un triángulo rectángulo

```js
let base = 10;
let altura = 5;

let area = (base*altura)/2;

console.log(' El area del triangulo rectangulo es: ' + area);
```

## 4- Determinar ¿cuál es el número mayor en un arreglo?

```js
let numeros = [1, 6, 8, 4, 2, 7, 10, 3, 50];
let mayor = 0;

for (let i = 0; i < numeros.length; i++) {
    if(numeros[i]>mayor){
        mayor = numeros[i];
    }
}

console.log("El valor mayor del arreglo es : " + mayor); //El valor mayor del arreglo es : 50
```

## 5- Determinar ¿Números pares e impares?

```js
let numeros = [1, 6, 8, 4, 2, 7, 10, 3, 50];

for (let i = 0; i < numeros.length; i++) {
    if(numeros[i] % 2 == 0){
        console.log(numeros[i] + " es un número PAR ");
    }else{
        console.log(numeros[i] + " es un número IMPAR ");
    }
}
```

## 6- Realizar tabla de multiplicar

```js
for (let i = 1; i <= 5 ; i++) {
    renglon = '';
    for (let j = 1; j <= 5 ; j++) {    
        //renglon += ' ' + i*j;
        renglon += `${ j * i }   `;
    }
    console.log(renglon);
}

```

## 7- Crear una función que reciba 3 argumentos numéricos

```js
function max(a, b, c){
    let mayor = a;
    if(a>=b && a>=c){
        mayor = a;
    }else if(b>=a && b>=c){
        mayor = b;
    }else{
        mayor = c;
    }

    return mayor;
}

let mayor = max(5, 2, 6);

console.log('El numero mayor es ' + mayor);

```

## 8- Función para determinar el nombre más largo

```js
function masLargo(arr){    
    let nombreLargo = '';

    for(let i = 0; i < arr.length; i++){

        if(arr[i].length > nombreLargo.length){
            nombreLargo = arr[i];
        }
    }

    return nombreLargo;
}

let heroes = ['Deadpool', 'Ciclope', 'Magneto', 'Profesor Charles Xavier'];

let heroeLargo = masLargo(heroes);

console.log('Heroe con el nobre más largo: ' + heroeLargo); //Profesor Charles Xavier

```

## 9- Función para filtrar nombres

```js

function filtrarPorLetra(arr, letra){
    let nuevoArr = [];    
    for(i = 0 ; i < arr.length; i++){
        if(arr[i][0] === letra){
            nuevoArr.push(arr[i]);
        }
    }
    return nuevoArr;
}

let heroes = ['Doom', 'Dr. Strange', 'Hulk', 'She Hulk', 'Spiderman','Captain Marvel'];

let heroesCon = filtrarPorLetra(heroes, 'S');

console.log(heroesCon); //0: "She Hulk"
			//1: "Spiderman"

```

## Códigos fuente hasta el momento

:+1:
