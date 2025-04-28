<!--
Meta Description: # Mapeos en Solidity: Guía Completa y Ejemplos Prácticos ## Sinopsis En Solidity, un **mapeo** es una estructura de datos que permite asociar claves c...
Meta Keywords: que, solidity, datos, mapeos, mapeo
-->

# Mapeos en Solidity: Guía Completa y Ejemplos Prácticos

## Sinopsis
En Solidity, un **mapeo** es una estructura de datos que permite asociar claves con valores, funcionando como un diccionario o un hash. Su uso es fundamental para el almacenamiento eficiente de datos en contratos inteligentes.

## Documentación
Los mapeos en Solidity son una de las estructuras de datos más útiles, permitiendo almacenar y recuperar información de manera rápida y eficiente. La sintaxis básica para declarar un mapeo es:

```solidity
mapping (tipo_clave => tipo_valor) nombre_mapeo;
```

### Propósito
El propósito principal de los mapeos es proporcionar una forma rápida de acceder a datos mediante una clave única. Esto es esencial en el desarrollo de contratos inteligentes donde el acceso a datos debe ser optimizado.

### Uso
Los mapeos pueden ser utilizados para almacenar cualquier tipo de datos, siempre que la clave sea un tipo de dato que lo permita (como `uint`, `address`, o `bytes32`). No es posible iterar sobre los mapeos, ya que no almacenan información sobre las claves que han sido utilizadas.

### Declaración de un mapeo
```solidity
mapping(address => uint) public balances;
```

En este ejemplo, estamos declarando un mapeo que asocia direcciones de Ethereum (`address`) con un número entero (`uint`), que podría representar el saldo de un usuario.

## Ejemplos
### Ejemplo básico de uso de mapeos
```solidity
pragma solidity ^0.8.0;

contract Almacenamiento {
    mapping(address => uint) public balances;

    function depositar() public payable {
        balances[msg.sender] += msg.value;
    }

    function obtenerSaldo() public view returns (uint) {
        return balances[msg.sender];
    }
}
```
En este contrato, los usuarios pueden depositar Ether y su saldo se almacena en el mapeo `balances`.

### Ejemplo con tipo de dato personalizado
```solidity
pragma solidity ^0.8.0;

contract Registro {
    struct Estudiante {
        string nombre;
        uint edad;
    }

    mapping(address => Estudiante) public estudiantes;

    function registrarEstudiante(string memory _nombre, uint _edad) public {
        estudiantes[msg.sender] = Estudiante(_nombre, _edad);
    }

    function obtenerEstudiante() public view returns (string memory, uint) {
        Estudiante memory estudiante = estudiantes[msg.sender];
        return (estudiante.nombre, estudiante.edad);
    }
}
```
En este contrato, se utiliza un mapeo para almacenar información sobre estudiantes, utilizando direcciones como claves.

## Explicación
### Errores Comunes y Notas Adicionales
- **Acceso a Datos No Existentes:** Si intentas acceder a una clave que no ha sido inicializada, Solidity devolverá un valor por defecto (0 para tipos numéricos, dirección 0 para `address`, etc.), lo que puede llevar a confusiones.
- **No Iterables:** A diferencia de otros lenguajes, no puedes iterar sobre un mapeo. Si necesitas realizar operaciones sobre todas las claves, considera usar un array adicional para almacenar las claves.
- **Gas Costs:** Ten en cuenta que cada operación que modifica un mapeo consume gas. Por lo tanto, es importante optimizar el uso de mapeos para evitar costos innecesarios.

## Resumen en una Línea
Los mapeos en Solidity son estructuras de datos que permiten asociar claves únicas con valores, facilitando el almacenamiento y acceso eficiente a datos en contratos inteligentes.