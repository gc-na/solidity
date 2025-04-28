<!--
Meta Description: # Understanding the "try" Expression in Solidity: Error Handling Made Easy ## Synopsis The `try` expression in Solidity is a powerful feature that all...
Meta Keywords: try, externalcontract, contract, function, solidity
-->

# Understanding the "try" Expression in Solidity: Error Handling Made Easy

## Synopsis
The `try` expression in Solidity is a powerful feature that allows developers to handle errors more gracefully when interacting with external contracts. It offers a structured approach to catching exceptions and managing failures, enhancing the robustness of smart contracts.

## Documentation

### Purpose
The `try` expression is designed to handle errors that may occur during function calls to other contracts. It provides a way to differentiate between successful executions and failures, thereby improving the error-handling mechanism in Solidity smart contracts.

### Usage
The `try` expression is primarily used when calling functions of external contracts. It allows developers to define a fallback mechanism if the call fails, hence avoiding unexpected crashes of the contract. The basic syntax is as follows:

```solidity
try contractInstance.functionName(arguments) returns (returnType) {
    // Code to execute on success
} catch {
    // Code to execute on failure
}
```

### Details
- **Contract Calls**: The `try` expression can only be used with external contract calls and not with internal function calls.
- **Error Handling**: If the function call within the `try` block fails, control is passed to the `catch` block where developers can implement fallback logic.
- **Return Values**: The `returns` keyword specifies the expected return type of the function being called. If the call fails, this return type is not available.
- **Catching Specific Errors**: Developers can also catch specific errors by specifying the type of the error in the `catch` block.

## Examples

### Basic Example

```solidity
pragma solidity ^0.8.0;

contract ExternalContract {
    function riskyFunction() public pure returns (uint) {
        require(false, "This function always fails");
        return 42;
    }
}

contract MainContract {
    ExternalContract externalContract;

    constructor(address _externalContractAddress) {
        externalContract = ExternalContract(_externalContractAddress);
    }

    function callRiskyFunction() public returns (uint) {
        try externalContract.riskyFunction() returns (uint result) {
            // Success case
            return result;
        } catch {
            // Failure case
            return 0; // Return a default value or handle error
        }
    }
}
```

### Catching Specific Errors

```solidity
pragma solidity ^0.8.0;

contract ExternalContract {
    function anotherRiskyFunction() public pure returns (uint) {
        revert("Explicit revert");
    }
}

contract MainContract {
    ExternalContract externalContract;

    constructor(address _externalContractAddress) {
        externalContract = ExternalContract(_externalContractAddress);
    }

    function callAnotherRiskyFunction() public returns (uint) {
        try externalContract.anotherRiskyFunction() returns (uint result) {
            return result;
        } catch (bytes memory reason) {
            // Handle specific error
            revert(string(reason)); // Revert with the original error message
        }
    }
}
```

## Explanation
While using the `try` expression greatly enhances error handling, developers need to be aware of a few common pitfalls:

- **State Changes**: The `try` expression does not revert the state of the contract if the called function fails. It's essential to ensure that your contract's state remains consistent regardless of success or failure of external calls.
- **Gas Costs**: The cost of gas for executing `try` can be higher due to the additional logic for error handling.
- **Limited Use Cases**: `try` can only be used with external calls. It cannot be used for calls made within the same contract.

## One Line Summary
The `try` expression in Solidity provides a structured way to handle errors from external contract calls, enhancing the robustness and reliability of smart contracts.