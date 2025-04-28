<!--
Meta Description: # Public: Modificador de Visibilidad en Solidity ## Sinopsis El modificador de visibilidad `public` en Solidity es una de las cuatro visibilidades que...
Meta Keywords: que, public, solidity, puede, funciones
-->

# Public: Modificador de Visibilidad en Solidity

## Sinopsis
El modificador de visibilidad `public` en Solidity es una de las cuatro visibilidades que se pueden asignar a funciones y variables. Permite que las funciones y variables sean accesibles desde fuera del contrato, facilitando la interacción con otros contratos y aplicaciones.

## Documentación
El modificador `public` determina quién puede acceder a las funciones y variables en un contrato inteligente de Solidity. Cuando se declara una función o variable como `public`, cualquier cuenta, ya sea interna o externa, puede invocarla o leer su valor.

### Uso
- **Funciones**: Las funciones públicas pueden ser llamadas tanto desde dentro del contrato como desde contratos externos o cuentas externas.
- **Variables**: Las variables públicas generan automáticamente una función de getter, lo que permite obtener su valor sin necesidad de escribir una función adicional. 

### Detalles
- **Acceso**: Las funciones y variables públicas son accesibles por cualquier usuario, lo que puede ser útil para la transparencia de datos, pero también puede presentar riesgos de seguridad si se exponen datos sensibles.
- **Visibilidad**: Además de `public`, Solidity ofrece otros modificadores de visibilidad: `private`, `internal` y `external`, cada uno con diferentes niveles de acceso.
- **Ejemplo de declaración**:
  ```solidity
  pragma solidity ^0.8.0;

  contract MiContrato {
      uint public contador;

      function incrementar() public {
          contador++;
      }
  }
  ```

## Ejemplos
### Ejemplo 1: Función pública
```solidity
pragma solidity ^0.8.0;

contract Almacen {
    uint public valor;

    function establecerValor(uint _valor) public {
        valor = _valor;
    }
}
```
En este ejemplo, la función `establecerValor` puede ser llamada desde cualquier dirección para establecer el valor de la variable `valor`.

### Ejemplo 2: Variable pública
```solidity
pragma solidity ^0.8.0;

contract Contador {
    uint public total;

    function incrementar() public {
        total++;
    }
}
```
Aquí, la variable `total` es pública, así que se puede acceder a su valor directamente desde fuera del contrato.

## Explicación
Al utilizar `public`, es importante tener en cuenta que:
- Las funciones públicas pueden ser llamadas repetidamente, lo que puede afectar el estado del contrato.
- Exponer demasiada funcionalidad a través de funciones públicas puede llevar a vulnerabilidades. Por ejemplo, permitir que cualquier usuario llame a una función que modifica el estado sin restricciones puede ser riesgoso.
- Las variables públicas son accesibles a cualquier usuario, lo que significa que cualquier dato almacenado puede ser consultado por cualquier persona, lo que no es deseable en ciertos casos.

## Resumen en una línea
El modificador `public` en Solidity permite que funciones y variables sean accesibles desde fuera del contrato, facilitando la interacción pero con implicaciones de seguridad que deben considerarse.