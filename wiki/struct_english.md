<!--
Meta Description: # Understanding Structs in Solidity: A Comprehensive Guide ## Synopsis In Solidity, a `struct` is a user-defined data type that allows developers to g...
Meta Keywords: struct, structs, solidity, user, uint
-->

# Understanding Structs in Solidity: A Comprehensive Guide

## Synopsis
In Solidity, a `struct` is a user-defined data type that allows developers to group related variables together, enabling more organized and efficient management of complex data.

## Documentation
### Purpose
Structs in Solidity are designed to create custom data structures that group different types of variables under one name. This capability is essential for modeling complex entities within smart contracts, such as user profiles, financial records, or any other composite data types.

### Usage
To declare a `struct`, you use the `struct` keyword followed by the name of the struct and its properties. Once defined, you can create instances of the struct and manipulate its data.

### Syntax
```solidity
struct StructName {
    DataType1 variable1;
    DataType2 variable2;
    // Additional variables
}
```

### Example Declaration
```solidity
pragma solidity ^0.8.0;

contract Example {
    struct User {
        string name;
        uint age;
        address walletAddress;
    }

    User public user;

    function createUser(string memory _name, uint _age, address _walletAddress) public {
        user = User(_name, _age, _walletAddress);
    }
}
```

## Examples
### Basic Usage
Below is a simple example demonstrating the creation and usage of a struct in a Solidity contract.

```solidity
pragma solidity ^0.8.0;

contract Inventory {
    struct Item {
        string name;
        uint quantity;
        uint price;
    }

    Item[] public items;

    function addItem(string memory _name, uint _quantity, uint _price) public {
        items.push(Item(_name, _quantity, _price));
    }

    function getItem(uint _index) public view returns (string memory, uint, uint) {
        Item memory item = items[_index];
        return (item.name, item.quantity, item.price);
    }
}
```

### Accessing Struct Data
You can access struct fields using the dot notation.

```solidity
function getUserName() public view returns (string memory) {
    return user.name; // Accessing the 'name' field of the 'user' struct
}
```

## Explanation
### Common Pitfalls
1. **Visibility**: Structs do not have visibility modifiers (public, private, etc.). Instead, the visibility is determined by the variables inside the struct.
  
2. **Memory and Storage**: When using structs, it’s important to understand the difference between `memory` and `storage`. Structs defined in functions as `memory` are temporary and will not persist after the function execution. In contrast, struct instances stored in `storage` will maintain their state.

3. **Default Values**: When a struct is initialized, its fields are set to their default values (e.g., `0` for integers, `""` for strings, and `address(0)` for addresses).

4. **Nested Structs**: Structs can contain other structs, but care must be taken to manage their complexity and state correctly.

5. **Gas Costs**: Using large structs can increase gas costs. Be mindful of the size and complexity of your structs, especially when they are frequently modified or retrieved.

## One Line Summary
Structs in Solidity are powerful custom data types that allow developers to encapsulate related variables, enhancing code organization and efficiency in smart contracts.