<!--
Meta Description: # Uso del Bucle "for" en Solidity: Sintaxis y Ejemplos ## Sinopsis El bucle "for" en Solidity es una estructura de control fundamental que permite eje...
Meta Keywords: bucle, solidity, numeros, para, uint
-->

# Uso del Bucle "for" en Solidity: Sintaxis y Ejemplos

## Sinopsis
El bucle "for" en Solidity es una estructura de control fundamental que permite ejecutar un bloque de código repetidamente, un número específico de veces, facilitando la iteración sobre arrays y la ejecución de acciones repetitivas de manera eficiente.

## Documentación
El bucle "for" en Solidity se utiliza para realizar iteraciones en un rango definido. Su sintaxis permite especificar un contador, una condición de continuación y una expresión de incremento. 

### Sintaxis
```solidity
for (inicialización; condición; incremento) {
    // Bloque de código a ejecutar
}
```

- **inicialización**: Se ejecuta una vez al comienzo del bucle y se utiliza para declarar y/o inicializar el contador.
- **condición**: Se evalúa antes de cada iteración. Si es verdadera, se ejecuta el bloque de código; si es falsa, se termina el bucle.
- **incremento**: Se ejecuta al final de cada iteración para modificar el contador.

### Propósito
El bucle "for" es ideal para ejecutar un conjunto de instrucciones un número conocido de veces. Es especialmente útil para iterar a través de estructuras de datos como arrays.

## Ejemplos

### Ejemplo Básico de Iteración
```solidity
pragma solidity ^0.8.0;

contract EjemploFor {
    uint[] public numeros;

    function llenarNumeros(uint _cantidad) public {
        for (uint i = 0; i < _cantidad; i++) {
            numeros.push(i);
        }
    }
}
```
En este ejemplo, el contrato `EjemploFor` llena un array `numeros` con valores desde `0` hasta `_cantidad - 1`.

### Ejemplo de Suma de Elementos en un Array
```solidity
pragma solidity ^0.8.0;

contract SumaArray {
    uint[] public numeros;

    function sumarNumeros() public view returns (uint suma) {
        for (uint i = 0; i < numeros.length; i++) {
            suma += numeros[i];
        }
    }
}
```
Aquí, el método `sumarNumeros` calcula la suma de todos los elementos en el array `numeros`.

## Explicación
Al utilizar el bucle "for", es esencial tener cuidado con la condición de parada. Un error común es crear un bucle infinito, lo que puede llevar a un consumo excesivo de gas y bloqueos en la ejecución del contrato. Además, si el contador no se incrementa correctamente, esto puede resultar en iteraciones no deseadas.

Es importante también manejar adecuadamente el acceso a los índices del array, ya que un acceso fuera de los límites del array causará un error de ejecución.

## Resumen en Una Línea
El bucle "for" en Solidity permite ejecutar un bloque de código repetidamente un número específico de veces, siendo fundamental para la iteración sobre arrays y la ejecución de acciones repetitivas.