<!--
Meta Description: # Understanding "error" in Solidity: Custom Error Handling ## Synopsis In Solidity, the `error` keyword is utilized to define custom error types, allo...
Meta Keywords: error, custom, solidity, errors, can
-->

# Understanding "error" in Solidity: Custom Error Handling

## Synopsis
In Solidity, the `error` keyword is utilized to define custom error types, allowing developers to create more informative and gas-efficient error handling in smart contracts.

## Documentation
### Purpose
The `error` keyword in Solidity enables developers to define custom error types that can be used to signal specific failures in smart contracts. Unlike traditional `require` or `revert` statements, which may only provide a string message, custom errors allow for more gas-efficient error handling and clearer communication about the nature of the failure.

### Usage
To define a custom error, you use the syntax:
```solidity
error ErrorName(parameterType parameterName);
```
Once defined, you can revert transactions using the custom error by calling `revert` followed by the error name and any parameters.

### Details
- **Gas Efficiency**: Custom errors save gas compared to string-based error messages because they do not store the error message in the contract's bytecode.
- **Type Safety**: By defining parameters for your custom errors, you can provide additional context for the error that can be programmatically checked by the caller.

## Examples
Here are basic examples demonstrating the usage of custom errors in Solidity.

### Example 1: Basic Custom Error Definition
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract Example {
    error InsufficientFunds(uint256 requested, uint256 available);

    function withdraw(uint256 amount) external {
        uint256 balance = address(this).balance;
        if (amount > balance) {
            revert InsufficientFunds(amount, balance);
        }
        // Logic for withdrawal
    }
}
```

### Example 2: Custom Error with Multiple Parameters
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract Voting {
    error NotAuthorized(address caller);
    
    function castVote() external {
        if (!isAuthorized(msg.sender)) {
            revert NotAuthorized(msg.sender);
        }
        // Logic for casting a vote
    }

    function isAuthorized(address voter) internal view returns (bool) {
        // Check if the voter is authorized
        return true; // Example condition
    }
}
```

## Explanation
### Common Pitfalls
- **Omitting Parameters**: Defining a custom error without parameters can lead to less informative error handling. Always consider what context is necessary to adequately convey the error.
- **Error Naming**: Choose clear and descriptive names for your errors to improve readability and maintainability of your code. A well-named error can help future developers understand the contract's logic quickly.

### Gotchas
- **Version Support**: Custom errors are supported in Solidity 0.8.0 and above. Ensure your development environment is set to the correct version.
- **Error Propagation**: When a custom error is reverted, it can still be caught in external contract calls, but the catching mechanism will differ from standard string-based errors. Be sure to handle custom errors appropriately in your application logic.

## One Line Summary
The `error` keyword in Solidity allows for efficient and clear custom error handling in smart contracts, enhancing both gas usage and debugging capabilities.