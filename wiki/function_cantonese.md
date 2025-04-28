<!--
Meta Description: # Solidity 中的函數 (Function) - 完整指南 ## 簡介 在 Solidity 中，函數是合約的基本組件之一，允許開發者定義可執行的代碼區塊，從而實現特定的邏輯和功能。函數是智能合約的核心，負責執行狀態變更、數據處理及操作。 ## 文檔 ### 目的 函數用於將重複使用的代碼組...
Meta Keywords: solidity, public, function, payable, uint
-->

# Solidity 中的函數 (Function) - 完整指南

## 簡介
在 Solidity 中，函數是合約的基本組件之一，允許開發者定義可執行的代碼區塊，從而實現特定的邏輯和功能。函數是智能合約的核心，負責執行狀態變更、數據處理及操作。

## 文檔
### 目的
函數用於將重複使用的代碼組織在一起，增強合約的可讀性與維護性。它們可以接收參數、返回值，並可設定訪問控制修飾符以限制誰可以調用這些函數。

### 使用方法
函數的基本語法如下：
```solidity
function functionName(parameters) visibility returns (returnType) {
    // 函數邏輯
}
```
- **functionName**: 函數的名稱。
- **parameters**: 函數接受的參數（可選）。
- **visibility**: 設定函數的可見性，如 `public`、`private`、`internal` 或 `external`。
- **returnType**: 函數返回值的類型（可選）。

### 詳細說明
1. **可見性**:
   - `public`: 可以被合約內部和外部調用。
   - `private`: 只能在定義該函數的合約內部調用。
   - `internal`: 可以在合約內部及其子合約中調用。
   - `external`: 只能被外部調用，且在合約內部無法直接引用。

2. **狀態變更**:
   - `view`: 只讀函數，不能改變合約的狀態。
   - `pure`: 不讀取或寫入合約狀態的函數。
   - `payable`: 允許函數接收以太幣。

## 示例
以下是一些基本用法的示例：

```solidity
pragma solidity ^0.8.0;

contract Example {
    uint public value;

    // 設定值的函數
    function setValue(uint _value) public {
        value = _value;
    }

    // 獲取值的函數
    function getValue() public view returns (uint) {
        return value;
    }

    // 可接收以太幣的函數
    function deposit() public payable {
        // 處理存款邏輯
    }
}
```

## 解釋
在使用函數時，開發者需注意以下幾點：
- 函數名稱必須唯一，並且應具有描述性，以提高可讀性。
- 適當地使用可見性修飾符，以保障合約的安全性。
- 小心使用 `payable` 函數，因為它們可以使合約接收以太幣，並可能導致資金損失。
- 考慮函數的 gas 成本，尤其是在循環或大型數據處理時。

## 一句話總結
在 Solidity 中，函數是定義合約邏輯的核心組件，通過明確的可見性和狀態修飾符來控制訪問和行為。