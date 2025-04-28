<!--
Meta Description: # Solidity 的 Immutable 關鍵字：不可變的狀態變數 ## 摘要 在 Solidity 中，`immutable` 是一種關鍵字，用於定義在合約部署後無法改變的狀態變數。這些變數的值在合約建構時被設置，並且在合約的整個生命週期中保持不變。 ## 文檔 ### 目的 `immutab...
Meta Keywords: immutable, solidity, 關鍵字, uint256, public
-->

# Solidity 的 Immutable 關鍵字：不可變的狀態變數

## 摘要
在 Solidity 中，`immutable` 是一種關鍵字，用於定義在合約部署後無法改變的狀態變數。這些變數的值在合約建構時被設置，並且在合約的整個生命週期中保持不變。

## 文檔
### 目的
`immutable` 關鍵字的主要目的是提高合約的安全性和效率，因為一旦設置後，這些變數將不會再被更改。這不僅能夠防止意外的狀態變更，還可以在某些情況下減少交易的 gas 費用。

### 使用方法
要使用 `immutable` 關鍵字，您需要在合約中聲明變數時加上 `immutable`，並在建構函數中初始化它。以下是基本語法：

```solidity
pragma solidity ^0.8.0;

contract Example {
    // 定義不可變的狀態變數
    uint256 public immutable myImmutableVar;

    // 合約建構函數
    constructor(uint256 _value) {
        myImmutableVar = _value; // 初始化變數
    }
}
```

### 詳細信息
- `immutable` 變數只能在合約的建構函數中被賦值。
- 一旦賦值，這些變數將不可再改變。
- 使用 `immutable` 變數可以提升合約的可讀性和安全性，因為它明確表示該變數不會在合約執行期間變化。

## 範例
以下是一個簡單的範例，展示了如何在 Solidity 中使用 `immutable` 關鍵字：

```solidity
pragma solidity ^0.8.0;

contract Token {
    string public name;
    string public symbol;
    uint256 public immutable initialSupply;

    constructor(string memory _name, string memory _symbol, uint256 _initialSupply) {
        name = _name;
        symbol = _symbol;
        initialSupply = _initialSupply; // 初始化不可變變數
    }
}
```

在這個範例中，`initialSupply` 是一個不可變的狀態變數，它在合約部署時被設置，並且在合約的生命週期中不會改變。

## 解釋
### 常見陷阱
- **初始化**：`immutable` 變數必須在建構函數中初始化，否則會導致編譯錯誤。
- **不支持的賦值**：您不能在其他函數中賦值 `immutable` 變數，這會引起編譯錯誤。
- **版本限制**：確保使用的 Solidity 版本支援 `immutable` 關鍵字，通常從 0.6.5 開始支持。

### 附加說明
- `immutable` 變數的使用可以導致合約在某些情況下更省 gas，因為編譯器能夠優化這些不變的值。
- 這種特性對於需要在合約部署時設定常量的情況特別有用。

## 一行總結
在 Solidity 中，`immutable` 關鍵字用於定義在合約部署後不可變的狀態變數，以提高安全性和效率。