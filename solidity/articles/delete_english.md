<!--
Meta Description: # Understanding the "delete" Keyword in Solidity: A Comprehensive Guide ## Synopsis The `delete` keyword in Solidity is used to reset variables to the...
Meta Keywords: delete, solidity, storage, data, resets
-->

# Understanding the "delete" Keyword in Solidity: A Comprehensive Guide

## Synopsis
The `delete` keyword in Solidity is used to reset variables to their default values, effectively removing their values from storage. This feature is crucial for memory management and optimizing gas costs in smart contracts.

## Documentation
### Purpose
The `delete` keyword allows developers to clear data stored in state variables, local variables, or storage arrays. When a variable is deleted, it reverts to its default state, which varies based on the variable type.

### Usage
The `delete` keyword can be used in the following contexts:
- **State Variables**: To reset variables stored on the blockchain.
- **Local Variables**: To reset temporary variables within functions.
- **Storage Arrays and Mappings**: To remove elements or reset entire arrays/mappings.

The syntax for using `delete` is straightforward:
```solidity
delete variable;
```

### Details
- **Default Values**: The default values depend on the variable type:
  - `uint`, `int`, `bool`: Resets to `0` or `false`.
  - `address`: Resets to `0x0`.
  - `bytes` and `string`: Resets to an empty byte array or string.
  - Structs: Resets all members to their default values.
- **Storage vs Memory**: The `delete` operation behaves differently in `storage` and `memory`. In `storage`, it removes the data, whereas in `memory`, it simply resets the values.
- **Gas Costs**: Using `delete` can optimize gas costs, especially when clearing large arrays or mappings.

## Examples
### Example 1: Deleting a State Variable
```solidity
pragma solidity ^0.8.0;

contract Example {
    uint256 public value = 10;

    function resetValue() public {
        delete value; // value is now 0
    }
}
```

### Example 2: Deleting a Struct
```solidity
pragma solidity ^0.8.0;

contract Example {
    struct Data {
        uint256 id;
        string name;
    }

    Data public data = Data(1, "Alice");

    function resetData() public {
        delete data; // data.id is now 0 and data.name is now an empty string
    }
}
```

### Example 3: Deleting Elements from an Array
```solidity
pragma solidity ^0.8.0;

contract Example {
    uint256[] public numbers;

    function addNumber(uint256 num) public {
        numbers.push(num);
    }

    function clearLastNumber() public {
        delete numbers[numbers.length - 1]; // Resets the last element to 0
    }
}
```

## Explanation
### Common Pitfalls
- **Deleting from Storage**: When using `delete` on storage arrays, remember that the size of the array remains unchanged. It only resets the element at the specified index.
- **Memory Arrays**: In memory, deleting an array or a variable may lead to unexpected behavior, as it does not entirely remove the reference but resets the values.
- **Mappings**: Deleting a mapping entry does not reduce the size of the mapping, but it resets the value associated with the key to its default.

### Additional Notes
- The `delete` keyword is a powerful tool for managing state and optimizing smart contracts. However, it should be used judiciously, as unnecessary deletions may lead to increased gas costs.

## One Line Summary
The `delete` keyword in Solidity is used to reset variables to their default values, optimizing storage management and gas costs in smart contracts.