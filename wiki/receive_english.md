<!--
Meta Description: # Understanding the `receive` Function in Solidity: A Comprehensive Guide ## Synopsis The `receive` function in Solidity is a special function designe...
Meta Keywords: function, receive, ether, contract, solidity
-->

# Understanding the `receive` Function in Solidity: A Comprehensive Guide

## Synopsis
The `receive` function in Solidity is a special function designed to handle incoming Ether transfers. It provides a straightforward mechanism for smart contracts to accept Ether without requiring additional data.

## Documentation
The `receive` function is a built-in function in Solidity that allows a contract to react to Ether being sent to it. It is executed when a contract receives Ether with no data attached to the transaction. The `receive` function is particularly useful for contracts that are intended to act as wallets or for those that need to accept payments.

### Purpose
The primary purpose of the `receive` function is to enable contracts to accept Ether directly. It serves as a fallback function specifically for handling simple Ether transfers and is executed when a contract is sent Ether without any accompanying data.

### Usage
In Solidity, the `receive` function can be defined as follows:

```solidity
receive() external payable {
    // Custom logic for handling Ether reception
}
```

- The function must be marked as `external`.
- It must be `payable` to allow the contract to accept Ether.
- There can only be one `receive` function in a contract.

### Details
- If a contract does not define a `receive` function, any incoming Ether will be rejected unless a fallback function is provided.
- The `receive` function is called automatically when Ether is sent to the contract without any data, making it a convenient way to handle simple payments.
- If the transaction includes data, the `receive` function will not be executed; instead, the fallback function (if defined) will be invoked.

## Examples
### Example 1: Basic Receive Function
```solidity
pragma solidity ^0.8.0;

contract SimpleWallet {
    event Received(address, uint);

    receive() external payable {
        emit Received(msg.sender, msg.value);
    }
}
```
In this example, the contract `SimpleWallet` defines a `receive` function that emits an event every time Ether is received.

### Example 2: Receive Function with Custom Logic
```solidity
pragma solidity ^0.8.0;

contract Fundraiser {
    uint public totalFunds;

    receive() external payable {
        totalFunds += msg.value; // Accumulate funds received
    }
}
```
This `Fundraiser` contract accumulates total funds received through the `receive` function.

## Explanation
### Common Pitfalls
- **No Receive Function Defined**: If a contract does not have a `receive` function or a fallback function, it will reject any Ether sent to it.
- **Incorrect Function Signature**: The `receive` function must be `external` and `payable`. Failing to adhere to these rules will result in compilation errors.
- **Gas Limit**: Keep in mind that the `receive` function should execute quickly, as it has a gas limit. Long-running operations can lead to transaction failures.

### Gotchas
- **Fallback Function Interaction**: If both a `receive` function and a fallback function are defined, the `receive` function will only be executed for plain Ether transfers, while the fallback function handles calls with data.
- **Reentrancy**: Be cautious of reentrancy attacks when implementing logic in the `receive` function. Consider using the Checks-Effects-Interactions pattern or employing reentrancy guards.

## One Line Summary
The `receive` function in Solidity allows contracts to accept Ether transfers without data, providing a simple mechanism for handling incoming funds.