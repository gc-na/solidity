<!--
Meta Description: # La Palabra Clave "external" en Solidity: Definición y Uso ## Sinopsis La palabra clave "external" en Solidity se utiliza para especificar la visibil...
Meta Keywords: funciones, externas, desde, external, solidity
-->

# La Palabra Clave "external" en Solidity: Definición y Uso

## Sinopsis
La palabra clave "external" en Solidity se utiliza para especificar la visibilidad de funciones y permite que estas funciones sean llamadas desde fuera del contrato, lo que es fundamental para la interacción entre contratos en la blockchain.

## Documentación
En Solidity, la visibilidad de las funciones es un aspecto crucial que define cómo se pueden acceder a ellas. La palabra clave "external" se utiliza al declarar una función, indicando que esta función puede ser llamada solo desde fuera del contrato, es decir, no puede ser invocada internamente dentro de otro método del mismo contrato.

### Propósito
El propósito principal de "external" es optimizar el uso de gas y permitir la interacción con otros contratos y cuentas externas. Las funciones marcadas como externas son más eficientes en términos de gas cuando son llamadas desde fuera del contrato, en comparación con las funciones públicas.

### Uso
Para declarar una función externa, se utiliza la siguiente sintaxis:

```solidity
contract MiContrato {
    function miFuncionExterna() external {
        // lógica de la función
    }
}
```

### Detalles
- **Acceso**: Solo se puede acceder a funciones externas desde direcciones externas. Si se intenta llamarlas desde otras funciones dentro del mismo contrato, se generará un error de compilación.
- **Parámetros**: Las funciones externas pueden aceptar parámetros, al igual que las funciones públicas.
- **Gas**: Al utilizar "external", se optimiza el uso de gas cuando se hacen llamadas de contratos, ya que las funciones externas pueden recibir datos directamente desde la llamada sin necesidad de hacer copias innecesarias.

## Ejemplos
### Ejemplo 1: Función básica externa
```solidity
pragma solidity ^0.8.0;

contract Ejemplo {
    uint public numero;

    function establecerNumero(uint _numero) external {
        numero = _numero;
    }
}
```

### Ejemplo 2: Llamadas a funciones externas
```solidity
pragma solidity ^0.8.0;

contract ContratoA {
    function funcionExterna() external pure returns (string memory) {
        return "Hola desde ContratoA";
    }
}

contract ContratoB {
    ContratoA contratoA;

    constructor(address _contratoA) {
        contratoA = ContratoA(_contratoA);
    }

    function llamarFuncionExterna() external view returns (string memory) {
        return contratoA.funcionExterna();
    }
}
```

## Explicación
### Errores Comunes
- **Llamadas internas**: Intentar invocar una función externa desde otro método dentro del mismo contrato resultará en un error de compilación. Para ello, se debe considerar el uso de funciones públicas o internas.
- **Parámetros no permitidos**: Las funciones externas no pueden ser llamadas por el contrato mismo con `this`, ya que se considera una llamada externa. Esto puede llevar a confusión si no se comprende bien la distinción de visibilidad.

### Notas Adicionales
- **Gas y rendimiento**: Aunque las funciones externas pueden ser más eficientes en cuanto al gas cuando se llaman desde fuera, es importante diseñar los contratos de forma que minimicen las llamadas externas innecesarias.
- **Eventos**: Como en cualquier función de Solidity, se pueden emitir eventos desde funciones externas, lo que permite la trazabilidad de las acciones.

## Resumen en Una Línea
La palabra clave "external" en Solidity define funciones que pueden ser llamadas únicamente desde direcciones externas al contrato, optimizando su uso en interacciones entre contratos.