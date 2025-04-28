<!--
Meta Description: # Understanding the "new" Keyword in Solidity: Creating Smart Contract Instances ## Synopsis The `new` keyword in Solidity is used to create new insta...
Meta Keywords: new, contract, keyword, solidity, public
-->

# Understanding the "new" Keyword in Solidity: Creating Smart Contract Instances

## Synopsis
The `new` keyword in Solidity is used to create new instances of contracts and allocate memory for them on the Ethereum blockchain. This keyword is essential for deploying smart contracts dynamically from within other contracts or functions.

## Documentation

### Purpose
The `new` keyword serves the primary function of instantiating a new contract. When you create a new contract instance, it is deployed to the Ethereum network, allowing it to maintain its own state and logic independently of other contracts.

### Usage
The syntax for using the `new` keyword is straightforward:

```solidity
ContractType newContractInstance = new ContractType();
```

Here, `ContractType` refers to the name of the contract you wish to instantiate. The new instance can be assigned to a variable which can then be used to interact with the contract.

### Details
- **Storage Costs**: Deploying a new contract incurs gas costs, which are paid in Ether. It's important to keep this in mind when designing contracts, as unnecessary deployments can lead to high transaction costs.
- **Constructor Execution**: When using `new`, the constructor of the contract is called automatically, allowing you to pass parameters if required.
- **Visibility**: The created contract instance remains accessible only within the scope it was created, unless stored in a public or external variable.
- **Memory and Storage**: The `new` keyword allocates storage on the blockchain, making the contract persistent, as opposed to variables that are stored in memory, which are ephemeral.

## Examples

### Example 1: Creating a Simple Contract Instance

```solidity
pragma solidity ^0.8.0;

contract SimpleStorage {
    uint256 public data;

    constructor(uint256 _data) {
        data = _data;
    }
}

contract Factory {
    SimpleStorage public simpleStorageInstance;

    function createSimpleStorage(uint256 _data) public {
        simpleStorageInstance = new SimpleStorage(_data);
    }
}
```

### Example 2: Creating Multiple Instances

```solidity
pragma solidity ^0.8.0;

contract Token {
    string public name;

    constructor(string memory _name) {
        name = _name;
    }
}

contract TokenFactory {
    Token[] public tokens;

    function createToken(string memory _name) public {
        Token newToken = new Token(_name);
        tokens.push(newToken);
    }
}
```

## Explanation
### Common Pitfalls and Gotchas
1. **Gas Limit**: When deploying contracts using the `new` keyword, be aware of the gas limit imposed by Ethereum. If a contract is too complex or requires extensive storage, it may exceed the gas limit, causing the transaction to fail.
2. **Initialization**: If the constructor requires parameters, ensure you provide the correct arguments. Failing to do so will prevent the contract from being instantiated.
3. **Visibility**: Always consider the visibility of the created contract instance. If you need it to be accessed externally, declare the variable as `public` or `external`.

## One Line Summary
The `new` keyword in Solidity is used to create new instances of contracts, allowing for dynamic deployment and interaction on the Ethereum blockchain.