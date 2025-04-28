<!--
Meta Description: # Solidity 映射 (Mapping) 的詳細介紹 ## 摘要 在 Solidity 中，映射（Mapping）是一種用於存儲鍵值對的數據結構，類似於其他編程語言中的哈希表或字典。它提供了一種高效的方式來關聯和檢索狀態變量。 ## 文檔 映射是 Solidity 中一種強大的數據結構，旨在存...
Meta Keywords: solidity, public, uint, mapping, function
-->

# Solidity 映射 (Mapping) 的詳細介紹

## 摘要
在 Solidity 中，映射（Mapping）是一種用於存儲鍵值對的數據結構，類似於其他編程語言中的哈希表或字典。它提供了一種高效的方式來關聯和檢索狀態變量。

## 文檔
映射是 Solidity 中一種強大的數據結構，旨在存儲和管理關聯數據。其基本語法為：
```solidity
mapping (keyType => valueType) public mappingName;
```
### 目的
映射用於創建一個可以根據唯一鍵快速查詢值的數據結構，使得狀態數據的管理變得更加簡單和高效。

### 用法
- **鍵類型**: 可以使用任何基本類型（如 `uint`, `address`, `bytes32` 等）作為鍵。
- **值類型**: 值可以是任何數據類型，包括基本類型、結構體、甚至是其他映射。
- **初始化**: 映射在首次訪問時自動初始化為其值類型的默認值。

### 詳細信息
- 映射不支持遍歷，這意味著無法獲得所有的鍵或值列表。
- 映射的大小不受限，並且對於每個鍵的查詢時間複雜度為 O(1)。

## 示例
以下是一些基本的映射用法示例：

### 範例 1: 基本映射
```solidity
pragma solidity ^0.8.0;

contract Example {
    mapping(address => uint) public balances;

    function setBalance(uint _balance) public {
        balances[msg.sender] = _balance;
    }

    function getBalance() public view returns (uint) {
        return balances[msg.sender];
    }
}
```

### 範例 2: 嵌套映射
```solidity
pragma solidity ^0.8.0;

contract NestedMapping {
    mapping(address => mapping(uint => string)) public userRecords;

    function setRecord(uint _id, string memory _record) public {
        userRecords[msg.sender][_id] = _record;
    }

    function getRecord(uint _id) public view returns (string memory) {
        return userRecords[msg.sender][_id];
    }
}
```

## 解釋
### 常見陷阱
- **無法遍歷**: 映射不支持直接遍歷，因此若需要保持所有鍵的列表，需要額外的數據結構來管理。
- **默認值**: 若訪問未被賦值的鍵，將返回值類型的默認值（例如 `0` 或空字符串），這可能會導致誤解。

### 注意事項
- 使用映射時，需考慮其鍵的獨特性，確保不會出現鍵重複的情況。
- 映射在內部結構上是基於雜湊的，這意味著可能存在潛在的安全風險，尤其是在大型合約中。

## 一句總結
Solidity 中的映射是一種高效的鍵值對數據結構，用於快速查詢和管理狀態變量。