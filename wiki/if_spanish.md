<!--
Meta Description: # La sentencia "if" en Solidity: Control de flujo en contratos inteligentes ## Sinopsis La sentencia "if" en Solidity es una estructura de control que...
Meta Keywords: solidity, código, else, condición, una
-->

# La sentencia "if" en Solidity: Control de flujo en contratos inteligentes

## Sinopsis
La sentencia "if" en Solidity es una estructura de control que permite ejecutar fragmentos de código basados en condiciones específicas. Es fundamental para la toma de decisiones dentro de los contratos inteligentes y mejora la lógica de programación en el entorno de Ethereum.

## Documentación
La sentencia "if" se utiliza para evaluar una expresión booleana y ejecutar un bloque de código si la condición es verdadera. Solidity permite el uso de "if" en combinación con "else" y "else if" para manejar múltiples condiciones.

### Propósito
El propósito principal de la sentencia "if" es facilitar la toma de decisiones en el código, permitiendo que el programa responda de manera diferente según las condiciones evaluadas.

### Uso
La sintaxis básica de la sentencia "if" es la siguiente:

```solidity
if (condición) {
    // Código a ejecutar si la condición es verdadera
} else if (otraCondición) {
    // Código a ejecutar si la otra condición es verdadera
} else {
    // Código a ejecutar si ninguna de las condiciones anteriores es verdadera
}
```

### Detalles
- **Condición**: Una expresión que se evalúa como verdadera (true) o falsa (false).
- **Bloques de código**: El código dentro de las llaves `{}` se ejecuta dependiendo del resultado de la evaluación de la condición.
- **Anidación**: Las sentencias "if" pueden anidarse para evaluar condiciones más complejas.

## Ejemplos
### Ejemplo básico de uso de "if"

```solidity
pragma solidity ^0.8.0;

contract EjemploIf {
    uint public saldo;

    constructor() {
        saldo = 100;
    }

    function verificarSaldo(uint cantidad) public view returns (string memory) {
        if (cantidad > saldo) {
            return "Fondos insuficientes";
        } else {
            return "Transacción autorizada";
        }
    }
}
```

### Ejemplo con "else if" y "else"

```solidity
pragma solidity ^0.8.0;

contract EjemploIfElse {
    uint public edad;

    constructor(uint _edad) {
        edad = _edad;
    }

    function clasificarEdad() public view returns (string memory) {
        if (edad < 13) {
            return "Niño";
        } else if (edad < 20) {
            return "Adolescente";
        } else {
            return "Adulto";
        }
    }
}
```

## Explicación
### Errores comunes
- **Olvidar las llaves**: Si no se utilizan llaves `{}`, solo la primera línea después de la condición será considerada parte del bloque.
- **Confusión con tipos**: Asegúrate de que las condiciones sean booleanas, ya que una expresión no booleana puede generar errores de compilación.
- **Anidación incorrecta**: Al anidar sentencias "if", es fácil perder la claridad en la lógica; siempre organiza el código adecuadamente.

### Notas adicionales
- Solidity no admite la declaración de variables dentro de una condición "if" si no se ha inicializado previamente.
- Es recomendable utilizar "require" para validar condiciones críticas, ya que revertirá la transacción si falla.

## Resumen en una línea
La sentencia "if" en Solidity es una estructura de control que permite ejecutar código condicionalmente, mejorando la lógica en contratos inteligentes.