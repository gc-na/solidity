<!--
Meta Description: # Constructor en Solidity: Guía Completa y Ejemplos ## Sinopsis El constructor en Solidity es un método especial que se ejecuta una vez al momento de ...
Meta Keywords: constructor, que, contrato, solidity, del
-->

# Constructor en Solidity: Guía Completa y Ejemplos

## Sinopsis
El constructor en Solidity es un método especial que se ejecuta una vez al momento de desplegar un contrato, permitiendo inicializar el estado del contrato y establecer parámetros esenciales.

## Documentación
El constructor en Solidity es una función que se utiliza para inicializar un contrato cuando se despliega en la blockchain. A diferencia de las funciones comunes, el constructor no tiene un nombre, ya que comparte el mismo nombre que el contrato. Esto significa que se invoca automáticamente al crear una instancia del contrato. 

### Propósito
El propósito principal de un constructor es establecer el estado inicial de un contrato, permitiendo definir variables y realizar configuraciones críticas que el contrato necesitará durante su ejecución.

### Uso
En Solidity, un constructor se define utilizando la palabra clave `constructor`. Puede aceptar parámetros para personalizar la inicialización del contrato. A continuación, se presenta la estructura básica del constructor:

```solidity
contract NombreDelContrato {
    // Variables de estado
    uint public numero;

    // Constructor
    constructor(uint _numero) {
        numero = _numero; // Inicializa la variable de estado
    }
}
```

### Detalles
- **Visibilidad**: Por defecto, la visibilidad de un constructor es pública. Sin embargo, los constructores también pueden ser marcados como `internal` si no se desea que otros contratos puedan crear instancias del contrato.
- **Sobrecarga**: Solidity no permite la sobrecarga de constructores, lo que significa que no puedes tener múltiples constructores con diferentes parámetros en un mismo contrato.
- **Despliegue**: Un contrato puede tener solo un constructor, y este se ejecuta una única vez, al momento de despliegar el contrato.

## Ejemplos
### Ejemplo Básico
```solidity
pragma solidity ^0.8.0;

contract EjemploConstructor {
    string public nombre;

    constructor(string memory _nombre) {
        nombre = _nombre;
    }
}
```
En este ejemplo, el contrato `EjemploConstructor` tiene un constructor que inicializa la variable `nombre` al momento de ser desplegado.

### Ejemplo con Parámetros
```solidity
pragma solidity ^0.8.0;

contract Almacen {
    uint public valor;

    constructor(uint _valorInicial) {
        valor = _valorInicial;
    }
}
```
Aquí, el contrato `Almacen` recibe un parámetro `_valorInicial` que se utiliza para establecer el valor de la variable `valor`.

## Explicación
### Errores Comunes
- **Olvidar Inicializar Variables**: Es esencial inicializar todas las variables de estado necesarias en el constructor, de lo contrario, pueden quedar con valores predeterminados inesperados.
- **Intentar Llamar al Constructor Después del Despliegue**: Una vez que el contrato ha sido desplegado, no se puede volver a invocar el constructor, lo que puede causar confusión si se intenta hacer.

### Notas Adicionales
Es importante recordar que los constructores no pueden ser utilizados para ejecutar lógica que dependa de llamadas externas, ya que estas pueden fallar y revertir el despliegue del contrato. También se recomienda mantener la lógica del constructor simple para evitar problemas en el despliegue.

## Resumen en Una Línea
El constructor en Solidity es una función especial que inicializa el estado de un contrato en el momento de su despliegue.