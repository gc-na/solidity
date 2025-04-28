<!--
Meta Description: # Solidity 中的建構子 (Constructor)：定義與使用 ## 摘要 在 Solidity 編程語言中，建構子是合約的特殊函數，用於初始化合約的狀態和設置初始變量。建構子在合約部署時自動執行，確保合約在使用之前正確配置。 ## 文檔 ### 目的 建構子的主要目的是為合約提供初始設置...
Meta Keywords: solidity, uint, public, constructor, pragma
-->

# Solidity 中的建構子 (Constructor)：定義與使用

## 摘要
在 Solidity 編程語言中，建構子是合約的特殊函數，用於初始化合約的狀態和設置初始變量。建構子在合約部署時自動執行，確保合約在使用之前正確配置。

## 文檔
### 目的
建構子的主要目的是為合約提供初始設置。這是合約中執行的第一個函數，負責設置合約的狀態變量。

### 使用方式
建構子的語法與普通函數相似，但沒有返回類型，且其名稱必須與合約名稱相同。建構子只能被執行一次，即合約部署時。

```solidity
pragma solidity ^0.8.0;

contract MyContract {
    uint public value;

    // 建構子
    constructor(uint _value) {
        value = _value; // 將傳入的值設置為合約的狀態變量
    }
}
```

### 詳細說明
- **多個建構子**： Solidity 不支持多個建構子，因此每個合約只能有一個建構子。如果需要不同的初始化邏輯，通常會使用參數來控制。
- **默認建構子**： 如果合約中沒有定義建構子，Solidity 會自動生成一個默認建構子，該建構子不接收任何參數。
- **可見性**： 建構子的可見性默認為 `public`，不需要特別聲明，但可以顯式標記為 `public` 或 `internal`。

## 範例
以下是一些基本的建構子使用範例：

### 範例 1：簡單的建構子
```solidity
pragma solidity ^0.8.0;

contract SimpleStorage {
    uint public storedData;

    constructor(uint initialValue) {
        storedData = initialValue; // 存儲初始數據
    }
}
```

### 範例 2：帶有多個參數的建構子
```solidity
pragma solidity ^0.8.0;

contract UserProfile {
    string public name;
    uint public age;

    constructor(string memory _name, uint _age) {
        name = _name; // 設置姓名
        age = _age;   // 設置年齡
    }
}
```

## 解釋
- **常見陷阱**：如果在建構子中使用 `this` 來引用合約本身，可能會導致不必要的 gas 消耗，因為合約在部署前是無法直接調用的。
- **狀態變量的初始化**：狀態變量的初始值會在建構子執行前自動設置為其類型的默認值。因此，建構子主要用於覆蓋這些默認值。
- **合約的繼承**：若合約繼承自父合約，則子合約的建構子需調用父合約的建構子來確保父合約的狀態正確初始化。

## 一句總結
建構子是 Solidity 中用於初始化合約狀態的特殊函數，確保合約在部署後能正確運作。