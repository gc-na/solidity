<!--
Meta Description: # Solidity 存儲 (Storage) 的詳細指南 ## 摘要 在 Solidity 中，存儲（Storage）是智能合約中用來永久保存狀態的區域。它與記憶體（Memory）和堆疊（Stack）相對，存儲的數據在合約的生命週期內持久存在。 ## 文檔 ### 目的 存儲是 Solidity ...
Meta Keywords: solidity, public, function, gas, storage
-->

# Solidity 存儲 (Storage) 的詳細指南

## 摘要
在 Solidity 中，存儲（Storage）是智能合約中用來永久保存狀態的區域。它與記憶體（Memory）和堆疊（Stack）相對，存儲的數據在合約的生命週期內持久存在。

## 文檔
### 目的
存儲是 Solidity 中的主要數據持久性解決方案。所有在合約中定義的狀態變量都被儲存在區塊鏈上，這些變量的值在合約的每次執行中都能被訪問和修改。

### 用法
在 Solidity 中，存儲變量的聲明通常使用 `storage` 關鍵字，這些變量的數據會被寫入區塊鏈狀態。合約中的狀態變量會自動被指定為存儲類型。

```solidity
pragma solidity ^0.8.0;

contract StorageExample {
    uint256 public myNumber; // 這是一個存儲變量

    function setNumber(uint256 _num) public {
        myNumber = _num; // 將數字存儲到區塊鏈
    }

    function getNumber() public view returns (uint256) {
        return myNumber; // 從區塊鏈獲取數字
    }
}
```

### 詳細資訊
每當合約狀態變量的值被修改時，這些更改會被記錄在區塊鏈上，並且需要支付相應的交易費用。存儲的數據類型包括基本數據類型（如 `uint`, `int`, `bool`, `address`）以及複合數據類型（如 `struct`, `mapping`, `array`）。

- **狀態變量的特性**：
  - 存儲的數據在合約的生命週期內持久存在。
  - 每次變更狀態時都會消耗 Gas。

## 範例
以下是一個簡單的合約示例，展示如何使用存儲變量。

```solidity
pragma solidity ^0.8.0;

contract SimpleStorage {
    string public storedData; // 存儲變量

    function set(string memory x) public {
        storedData = x; // 將資料存儲在區塊鏈上
    }

    function get() public view returns (string memory) {
        return storedData; // 從存儲中獲取資料
    }
}
```

## 解釋
在使用存儲時，開發者需要注意以下幾個常見問題：

1. **Gas 成本**：每次寫入存儲變量都需要支付 Gas，這可能會使頻繁的更新變得昂貴。
2. **初始值**：狀態變量在合約創建時會自動初始化為其類型的零值（如 `0`、`false`、`""` 等）。
3. **複雜數據結構**：使用 `mapping` 或 `struct` 來管理複雜數據時，需特別注意查詢和修改的效率。

## 一句總結
存儲是 Solidity 中用於永久保存合約狀態的關鍵特性，並且與 Gas 成本密切相關。