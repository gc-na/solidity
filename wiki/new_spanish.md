<!--
Meta Description: # Uso de "new" en Solidity: Creación de Instancias de Contratos ## Sinopsis El comando `new` en Solidity se utiliza para crear nuevas instancias de co...
Meta Keywords: contrato, que, instancias, contratos, new
-->

# Uso de "new" en Solidity: Creación de Instancias de Contratos

## Sinopsis
El comando `new` en Solidity se utiliza para crear nuevas instancias de contratos inteligentes en la blockchain. Es una función fundamental que permite la implementación de contratos en la red Ethereum.

## Documentación
### Propósito
El operador `new` permite a los desarrolladores instanciar contratos inteligentes, creando una copia única del mismo en la blockchain. Al utilizar este operador, se despliega un nuevo contrato, lo que permite que cada instancia tenga su propio estado y lógica.

### Uso
La sintaxis básica para usar `new` es la siguiente:

```solidity
ContratoNombre nuevaInstancia = new ContratoNombre(args);
```

Donde `ContratoNombre` es el nombre del contrato que deseas instanciar y `args` son los argumentos del constructor, si los hay.

### Detalles
- **Visibilidad**: La instancia creada es accesible únicamente a través de la variable que la almacena.
- **Pago de Gas**: La implementación de un nuevo contrato consume gas, así que es importante tener en cuenta los costos asociados al despliegue.
- **Constructor**: Si el contrato tiene un constructor, los argumentos deben ser proporcionados al momento de crear la instancia.
- **Dirección del Contrato**: Al crear un nuevo contrato, se genera una dirección única en la blockchain que puede ser utilizada para interactuar con la instancia.

## Ejemplos
### Ejemplo Básico
```solidity
pragma solidity ^0.8.0;

contract MiContrato {
    uint public valor;

    constructor(uint _valor) {
        valor = _valor;
    }
}

contract Gestor {
    MiContrato public instancia;

    function crearContrato(uint _valor) public {
        instancia = new MiContrato(_valor);
    }
}
```
En este ejemplo, el contrato `Gestor` crea una nueva instancia del contrato `MiContrato` con un valor inicial.

### Ejemplo con Múltiples Instancias
```solidity
pragma solidity ^0.8.0;

contract OtroContrato {
    string public nombre;

    constructor(string memory _nombre) {
        nombre = _nombre;
    }
}

contract Gestor {
    OtroContrato[] public contratos;

    function crearOtroContrato(string memory _nombre) public {
        OtroContrato nuevoContrato = new OtroContrato(_nombre);
        contratos.push(nuevoContrato);
    }
}
```
Aquí, el contrato `Gestor` crea múltiples instancias de `OtroContrato` y las almacena en un arreglo.

## Explicación
### Problemas Comunes
- **Costo de Gas**: Crear nuevas instancias de contratos puede ser costoso en términos de gas, especialmente si el contrato tiene una lógica compleja.
- **Visibilidad de Instancias**: Asegúrate de que las instancias sean accesibles según necesites; por ejemplo, si se declaran como `private`, no podrán ser accedidas desde fuera del contrato.
- **Errores en el Constructor**: Si hay un error en los parámetros pasados al constructor, la transacción fallará.

### Notas Adicionales
- Es importante tener en cuenta el contexto de la red (mainnet, testnet) en la que se despliega el contrato, ya que los costos de gas pueden variar.
- La creación de instancias de contratos puede generar eventos en la blockchain, que pueden ser útiles para el seguimiento y la auditoría.

## Resumen en una Línea
El operador `new` en Solidity permite la creación de nuevas instancias de contratos inteligentes, facilitando la implementación y gestión de la lógica del contrato en la blockchain.