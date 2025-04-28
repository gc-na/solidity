<!--
Meta Description: # `require`: Validación de Condiciones en Solidity ## Sinopsis El comando `require` en Solidity es una función esencial que permite validar condicione...
Meta Keywords: que, require, solidity, contrato, para
-->

# `require`: Validación de Condiciones en Solidity

## Sinopsis
El comando `require` en Solidity es una función esencial que permite validar condiciones y asegurar que ciertos criterios se cumplan antes de ejecutar el resto del código en un contrato inteligente. Es fundamental para la gestión de errores y la protección de la lógica de negocio.

## Documentación
El propósito de `require` es verificar que una condición sea verdadera. Si la condición evaluada es falsa, la ejecución del contrato se detiene y se revierte cualquier cambio realizado en el estado. Esto ayuda a prevenir estados inconsistentes y asegura que los contratos se comporten como se espera.

### Uso
La sintaxis básica de `require` es la siguiente:

```solidity
require(condición, "mensaje de error");
```

- **condición**: Una expresión booleana que debe ser verdadera para continuar la ejecución.
- **mensaje de error**: Un mensaje opcional que se muestra si la condición es falsa, lo que ayuda en la depuración.

Cuando se utiliza `require`, el gas utilizado hasta el momento de la llamada se consume, pero no se aplican cambios al estado del contrato si la condición no se cumple.

### Detalles
- `require` se utiliza comúnmente para validar entradas de funciones, asegurar que se cumplan condiciones en transacciones y verificar estados de variables.
- Es recomendable utilizar `require` para evitar que se realicen operaciones no deseadas o que se genere un estado inválido en el contrato.

## Ejemplos
A continuación se presentan ejemplos básicos del uso de `require` en un contrato inteligente:

### Ejemplo 1: Validación de un saldo suficiente
```solidity
pragma solidity ^0.8.0;

contract Banca {
    mapping(address => uint) public saldos;

    function retirar(uint monto) public {
        require(saldos[msg.sender] >= monto, "Saldo insuficiente");
        saldos[msg.sender] -= monto;
    }
}
```

### Ejemplo 2: Validación de una dirección válida
```solidity
pragma solidity ^0.8.0;

contract Registro {
    function registrar(address usuario) public {
        require(usuario != address(0), "La direccion no puede ser cero");
        // Lógica para registrar al usuario
    }
}
```

## Explicación
Uno de los errores comunes al usar `require` es no proporcionar un mensaje de error claro, lo que dificulta la depuración. Además, es importante recordar que `require` no solo detiene la ejecución del contrato, sino que también revierte cualquier cambio de estado, lo que puede ser útil para mantener la consistencia del contrato.

Otro punto a considerar es que el uso excesivo de `require` puede incrementar el costo de gas de la transacción, por lo que se debe utilizar de manera eficiente y solo para validar condiciones críticas.

## Resumen en una línea
El comando `require` en Solidity se utiliza para validar condiciones y asegurar que se cumplan criterios específicos antes de ejecutar acciones en un contrato inteligente.