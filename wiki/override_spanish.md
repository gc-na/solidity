<!--
Meta Description: # Override en Solidity: Guía Completa sobre la Sobreescritura de Funciones ## Sinopsis El modificador `override` en Solidity permite que una función e...
Meta Keywords: override, contrato, que, funciones, una
-->

# Override en Solidity: Guía Completa sobre la Sobreescritura de Funciones

## Sinopsis
El modificador `override` en Solidity permite que una función en un contrato hijo reemplace o modifique el comportamiento de una función definida en un contrato padre. Esta funcionalidad es esencial para la programación orientada a objetos, ya que permite la personalización de la lógica del contrato.

## Documentación
En Solidity, el uso de `override` se aplica en el contexto de herencia de contratos. Cuando un contrato hereda de otro, puede implementar o modificar funciones que ya están definidas en el contrato padre. Para indicar que una función está sobrescribiendo una función base, se utiliza el modificador `override` en la declaración de la función.

### Propósito
El propósito principal de `override` es garantizar que el programador sea explícito sobre la intención de sobrescribir funciones, lo que ayuda a evitar errores y mejora la legibilidad del código.

### Uso
Para usar el modificador `override`, se debe:
1. Definir una función en un contrato padre.
2. En el contrato hijo, declarar la misma función y añadir el modificador `override`.

### Detalles
- Se puede usar `override` en funciones que están marcadas como `virtual` en el contrato padre.
- Es posible sobrescribir múltiples funciones utilizando `override` en una sola declaración, separando los nombres de las funciones por comas.

## Ejemplos
### Ejemplo 1: Sobrescritura Básica
```solidity
pragma solidity ^0.8.0;

contract Padre {
    function saludar() public virtual returns (string memory) {
        return "Hola desde el contrato padre.";
    }
}

contract Hijo is Padre {
    function saludar() public override returns (string memory) {
        return "Hola desde el contrato hijo.";
    }
}
```

### Ejemplo 2: Sobrescribir Múltiples Funciones
```solidity
pragma solidity ^0.8.0;

contract Base {
    function funcionA() public virtual returns (string memory) {
        return "Funcion A de Base";
    }
    
    function funcionB() public virtual returns (string memory) {
        return "Funcion B de Base";
    }
}

contract Derivada is Base {
    function funcionA() public override returns (string memory) {
        return "Funcion A de Derivada";
    }

    function funcionB() public override returns (string memory) {
        return "Funcion B de Derivada";
    }
}
```

## Explicación
### Errores Comunes
1. **No usar el modificador `virtual`**: Si una función en el contrato padre no está marcada como `virtual`, no se puede sobrescribir.
2. **Olvidar `override`**: No utilizar el modificador `override` en el contrato hijo resultará en un error de compilación, ya que Solidity requiere que se declare explícitamente la intención de sobrescribir.

### Notas Adicionales
- La sobrescritura de funciones es una característica clave en la programación orientada a objetos que permite a los desarrolladores extender y personalizar la funcionalidad de los contratos.
- Se recomienda una buena práctica de nombrar funciones que sobrescriben de manera que se comprenda claramente la intención del cambio.

## Resumen en una Línea
El modificador `override` en Solidity permite que un contrato hijo sobrescriba funciones de un contrato padre, mejorando la personalización y la claridad del código.