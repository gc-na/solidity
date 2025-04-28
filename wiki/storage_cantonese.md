<!--
Meta Description: # Solidity 存儲(Storage) 的全面指南 ## 概述 在 Solidity 程式語言中，"存儲" 指的是智能合約中數據的持久化方式。它是用來儲存合約的狀態變量，並在區塊鏈上進行長期保存。 ## 文檔 存儲是 Solidity 中的三種數據位置之一，其他兩種為 "記憶體(Memory)...
Meta Keywords: solidity, uint256, public, storeddata, gas
-->

# Solidity 存儲(Storage) 的全面指南

## 概述
在 Solidity 程式語言中，"存儲" 指的是智能合約中數據的持久化方式。它是用來儲存合約的狀態變量，並在區塊鏈上進行長期保存。

## 文檔
存儲是 Solidity 中的三種數據位置之一，其他兩種為 "記憶體(Memory)" 和 "堆疊(Stack)"。每個狀態變量都會被永久存儲在區塊鏈上，這意味著它們的值在合約的生命週期中是持久的。存儲的主要特點包括：

- **持久性**：存儲的數據在合約執行後仍然保留，直到被更新或合約被摧毀。
- **成本**：寫入存儲的操作需要支付 Gas 費用，這通常比在記憶體中操作要昂貴。
- **數據類型**：支持各種數據類型，包括基本數據類型（如 `uint`、`bool`）和自定義類型（如結構體、映射等）。

使用存儲的基本語法如下：
```solidity
contract Example {
    uint256 public number; // 存儲一個整數
}
```

## 示例
以下是使用存儲的基本範例：

```solidity
pragma solidity ^0.8.0;

contract StorageExample {
    // 宣告一個整數狀態變量
    uint256 public storedData;

    // 設置存儲數據的函數
    function set(uint256 x) public {
        storedData = x; // 將數據存入存儲
    }

    // 獲取存儲數據的函數
    function get() public view returns (uint256) {
        return storedData; // 從存儲中讀取數據
    }
}
```

在這個範例中，我們創建了一個合約 `StorageExample`，它有一個整數狀態變量 `storedData`，透過 `set` 和 `get` 函數來設置和獲取數據。

## 解釋
使用存儲時需注意以下幾點：

1. **Gas 成本**：每次將數據寫入存儲時，都需要支付相應的 Gas 費用，這可能會影響合約的經濟性。儘量減少不必要的寫入操作。
  
2. **數據更新**：每次更新存儲的狀態變量時，將會改變其在區塊鏈上的值。因此，應謹慎設計合約中的邏輯，避免不必要的數據更新。

3. **存儲大小**：存儲的數據會根據其類型和數量佔用不同的區塊鏈空間，尤其是使用映射和結構體時，需注意其潛在的存儲成本。

## 總結
在 Solidity 中，存儲是管理智能合約狀態的關鍵，理解其特性和成本對於有效開發合約至關重要。