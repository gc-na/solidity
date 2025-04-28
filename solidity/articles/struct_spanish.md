<!--
Meta Description: # Estructuras en Solidity: Guía Completa sobre el Uso de `struct` ## Sinopsis Las estructuras (`struct`) en Solidity son tipos de datos personalizados...
Meta Keywords: struct, una, que, datos, solidity
-->

# Estructuras en Solidity: Guía Completa sobre el Uso de `struct`

## Sinopsis
Las estructuras (`struct`) en Solidity son tipos de datos personalizados que permiten agrupar variables de diferentes tipos en una sola entidad, facilitando la organización y manejo de datos complejos en contratos inteligentes.

## Documentación
Las `struct` son una herramienta fundamental en Solidity que permite a los desarrolladores crear tipos de datos compuestos. Una `struct` puede contener variables de diferentes tipos, como enteros, cadenas y otros tipos de `struct`, lo que permite crear representaciones más complejas de datos dentro del contrato inteligente.

### Propósito
El propósito de las `struct` es agrupar información relacionada, lo que simplifica la gestión de datos y mejora la legibilidad del código. Son especialmente útiles al trabajar con colecciones de datos, como en el caso de sistemas de votación, juegos, y más.

### Uso
Para definir una `struct`, se utiliza la palabra clave `struct`, seguida del nombre de la estructura y su definición entre llaves. A continuación, se muestra un ejemplo de la sintaxis básica:

```solidity
struct NombreEstructura {
    tipoVariable1 nombreVariable1;
    tipoVariable2 nombreVariable2;
}
```

Una vez definida, se puede crear instancias de la `struct` y acceder a sus variables.

## Ejemplos
Aquí hay un ejemplo básico que ilustra cómo definir y utilizar una `struct` en Solidity:

```solidity
pragma solidity ^0.8.0;

contract EjemploStruct {
    struct Persona {
        string nombre;
        uint edad;
    }

    Persona public persona1;

    function establecerPersona(string memory _nombre, uint _edad) public {
        persona1 = Persona(_nombre, _edad);
    }

    function obtenerNombre() public view returns (string memory) {
        return persona1.nombre;
    }

    function obtenerEdad() public view returns (uint) {
        return persona1.edad;
    }
}
```

En este ejemplo, se define una `struct` llamada `Persona` que contiene un `string` para el nombre y un `uint` para la edad. Se proporciona una función para establecer los valores y dos para obtenerlos.

## Explicación
Al trabajar con `struct`, es importante tener en cuenta algunos aspectos:

- **Visibilidad**: Las variables dentro de una `struct` no tienen visibilidad por defecto, por lo que es recomendable establecer la visibilidad de cada variable según sea necesario.
- **Almacenamiento**: Las instancias de `struct` se pueden almacenar en memoria o en almacenamiento persistente (storage). La elección de almacenamiento puede afectar el costo del gas y la eficiencia del contrato.
- **Actualización**: Actualizar una `struct` requiere asignar nuevos valores a cada variable, lo que puede ser menos eficiente que cambiar una variable simple si no se utilizan punteros.
- **Anidación**: Las `struct` pueden contener otras `struct`, lo que puede llevar a una complejidad adicional en la gestión de datos.

## Resumen en una línea
Las `struct` en Solidity son tipos de datos personalizados que permiten agrupar variables de diferentes tipos, facilitando la gestión de datos complejos en contratos inteligentes.