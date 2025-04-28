<!--
Meta Description: # Calldata en Solidity: Comprendiendo el tipo de datos para la eficiencia en la programación de contratos inteligentes ## Sinopsis `calldata` es un ti...
Meta Keywords: calldata, que, datos, solidity, para
-->

# Calldata en Solidity: Comprendiendo el tipo de datos para la eficiencia en la programación de contratos inteligentes

## Sinopsis
`calldata` es un tipo de datos en Solidity que se utiliza para definir la ubicación de almacenamiento de los parámetros de las funciones en contratos inteligentes. Es especialmente útil para funciones que reciben datos de forma externa, ya que permite un acceso eficiente y un menor consumo de gas.

## Documentación
En Solidity, `calldata` se utiliza para especificar que los datos de una función son de solo lectura y se almacenan de manera externa. Este tipo de datos es inmutable, lo que significa que no se puede modificar una vez que se ha pasado a la función. Se utiliza principalmente en las funciones de tipo `external`, donde los argumentos se pasan desde fuera del contrato.

### Propósito
El principal propósito de `calldata` es reducir el consumo de gas y mejorar la eficiencia al trabajar con grandes volúmenes de datos. Al utilizar `calldata`, los parámetros que se envían a las funciones no se copian en la memoria, lo que reduce el costo de gas asociado con las operaciones de almacenamiento.

### Uso
Para declarar un parámetro como `calldata`, simplemente se incluye la palabra clave `calldata` antes del tipo de dato al definir la función. Por ejemplo:

```solidity
function procesarDatos(uint256[] calldata datos) external {
    // lógica de procesamiento
}
```

### Detalles
- `calldata` solo se puede usar con parámetros de tipo `external`.
- No se puede modificar el contenido de `calldata` dentro de la función.
- Es ideal para trabajar con arrays y estructuras grandes, ya que evita la copia de datos a la memoria.

## Ejemplos

### Ejemplo 1: Uso básico de `calldata`
```solidity
pragma solidity ^0.8.0;

contract MiContrato {
    function sumar(uint256[] calldata numeros) external pure returns (uint256) {
        uint256 suma = 0;
        for (uint256 i = 0; i < numeros.length; i++) {
            suma += numeros[i];
        }
        return suma;
    }
}
```

### Ejemplo 2: Estructuras y `calldata`
```solidity
pragma solidity ^0.8.0;

struct Persona {
    string nombre;
    uint8 edad;
}

contract Registro {
    function registrarPersona(Persona[] calldata personas) external {
        // lógica para registrar personas
    }
}
```

## Explicación
Un error común al usar `calldata` es intentar modificar los datos dentro de la función, lo cual no es permitido y resultará en un error de compilación. Además, es importante recordar que `calldata` es solo para parámetros de función que se pasan desde el exterior; no se puede usar para variables de estado o locales.

Otro aspecto a tener en cuenta es que, dado que `calldata` es inmutable, se debe tener cuidado al depender de los datos dentro de la función, ya que cualquier intento de modificarlos resultará en un fallo.

## Resumen en una línea
`calldata` es un tipo de datos en Solidity que permite el acceso eficiente y de solo lectura a los parámetros de funciones externas, optimizando el consumo de gas.