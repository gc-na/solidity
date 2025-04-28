<!--
Meta Description: # Uso de "internal" en Solidity: Acceso y Visibilidad de Funciones y Variables ## Sinopsis En Solidity, la palabra clave "internal" se utiliza para co...
Meta Keywords: que, internal, funciones, contratos, variables
-->

# Uso de "internal" en Solidity: Acceso y Visibilidad de Funciones y Variables

## Sinopsis
En Solidity, la palabra clave "internal" se utiliza para controlar la visibilidad de funciones y variables dentro de contratos y sus derivados. Esta característica permite que solo los contratos que heredan de un contrato base puedan acceder a estas funciones y variables, promoviendo la encapsulación y seguridad en el código.

## Documentación
La visibilidad "internal" es una de las cuatro especificaciones de visibilidad en Solidity, junto con "public", "private" y "external". Las funciones y variables marcadas como "internal" son accesibles dentro del mismo contrato y en todos los contratos que lo heredan. Esto resulta útil para crear contratos modularizados y reutilizables.

### Propósito
El uso de "internal" permite desarrollar contratos que pueden compartir lógica entre diferentes contratos derivados, manteniendo al mismo tiempo un nivel de protección para la lógica interna que no debería ser accesible desde fuera.

### Uso
Para declarar una función o variable como interna, simplemente se debe anteponer la palabra clave "internal" antes de la declaración. Si no se especifica visibilidad, se asume que es "internal" por defecto para las funciones.

### Detalles
- **Funciones**: Las funciones internas pueden ser llamadas desde el mismo contrato o desde contratos que heredan de él.
- **Variables**: Las variables internas pueden ser leídas y modificadas dentro del contrato y sus derivados.
- **Acceso**: No se puede acceder a funciones o variables internas desde otros contratos que no sean los que heredan de la clase base.

## Ejemplos

### Ejemplo 1: Función Interna
```solidity
pragma solidity ^0.8.0;

contract Base {
    internal function internalFunction() internal pure returns (string memory) {
        return "Soy una función interna";
    }
}

contract Derivada is Base {
    function callInternalFunction() public view returns (string memory) {
        return internalFunction();
    }
}
```

### Ejemplo 2: Variable Interna
```solidity
pragma solidity ^0.8.0;

contract Base {
    uint internal internalVariable = 10;

    function getInternalVariable() internal view returns (uint) {
        return internalVariable;
    }
}

contract Derivada is Base {
    function readInternalVariable() public view returns (uint) {
        return getInternalVariable();
    }
}
```

## Explicación
Uno de los errores comunes al usar "internal" es olvidar que, aunque las funciones y variables internas son accesibles en contratos derivados, no lo son en contratos independientes. Esto puede llevar a confusiones al intentar acceder a estas funciones desde un contrato que no forma parte de la jerarquía de herencia.

Además, es importante señalar que "internal" no debe ser utilizado como un mecanismo de seguridad para proteger información sensible, ya que cualquiera que tenga acceso a los contratos derivados puede acceder a esas funciones y variables.

## Resumen en una línea
La palabra clave "internal" en Solidity permite que funciones y variables sean accesibles solo dentro del contrato y sus contratos derivados, promoviendo la encapsulación y la reutilización de código.