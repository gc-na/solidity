<!--
Meta Description: # Solidity 中的 Mapping：一個深入的指南 ## 簡介 在 Solidity 中，mapping 是一種關鍵的數據結構，用來建立鍵值對的關係，類似於其他編程語言中的字典或哈希表。它能夠高效地儲存和檢索數據，並在智能合約中廣泛應用。 ## 文檔 ### 目的 Mapping 主要用於儲...
Meta Keywords: mapping, solidity, uint, public, balances
-->

# Solidity 中的 Mapping：一個深入的指南

## 簡介
在 Solidity 中，mapping 是一種關鍵的數據結構，用來建立鍵值對的關係，類似於其他編程語言中的字典或哈希表。它能夠高效地儲存和檢索數據，並在智能合約中廣泛應用。

## 文檔
### 目的
Mapping 主要用於儲存關聯數據。它允許開發者使用唯一的鍵來查找對應的值，這在智能合約的開發中非常重要，特別是在處理用戶資訊、資產和其他狀態時。

### 用法
Mapping 的基本語法如下：
```solidity
mapping(KeyType => ValueType) public name;
```
- **KeyType**：鍵的數據類型，可以是任何基礎類型（如 `uint`, `address`, `bytes32` 等）。
- **ValueType**：值的數據類型，可以是任何類型，包括其他 mapping、結構體或數組。

### 詳細說明
1. **聲明**：Mapping 必須在合約內部聲明。它不能是局部變量。
2. **預設值**：當 mapping 被創建時，所有鍵對應的值自動初始化為其類型的預設值。例如，`uint` 類型的值為 0，`address` 類型的值為零地址。
3. **訪問數據**：使用鍵來獲取對應的值，如：`name[someKey]`。
4. **無法遍歷**：Mapping 不支持直接的數據遍歷，開發者必須自己管理鍵的列表以便於遍歷。

## 示例
以下是使用 mapping 的基本示例：
```solidity
pragma solidity ^0.8.0;

contract SimpleStorage {
    mapping(address => uint) public balances;

    function setBalance(uint _balance) public {
        balances[msg.sender] = _balance;
    }

    function getBalance() public view returns (uint) {
        return balances[msg.sender];
    }
}
```
在這個示例中，`balances` mapping 存儲了每個地址的餘額。

## 解釋
### 常見陷阱
1. **鍵的唯一性**：確保每個鍵是唯一的，否則會覆蓋之前的值。
2. **預設值誤解**：注意 mapping 的預設值，當試圖讀取未設定的鍵時，將返回預設值。
3. **無法遍歷**：在設計合約時，考慮到 mapping 不能被遍歷，這可能影響到數據的管理和顯示。

### 附加提示
- 使用 `struct` 與 mapping 結合，可以存儲更複雜的數據。
- 在設計智能合約時，考慮到 gas 成本，儘量減少不必要的數據寫入操作。

## 總結
Mapping 是 Solidity 中一個強大的數據結構，能夠高效地管理和存儲鍵值對數據。