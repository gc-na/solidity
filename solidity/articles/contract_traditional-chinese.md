<!--
Meta Description: # Solidity 合約：智能合約的基礎 ## 簡介 合約是 Solidity 的核心概念，代表著在以太坊區塊鏈上運行的自動執行的程式碼。這些合約可以用來實現各種應用，包括去中心化金融、遊戲、投票系統等。 ## 文檔 合約（Contract）是 Solidity 中的一種特殊類型，定義了一組狀態變...
Meta Keywords: solidity, uint, public, value, contract
-->

# Solidity 合約：智能合約的基礎

## 簡介
合約是 Solidity 的核心概念，代表著在以太坊區塊鏈上運行的自動執行的程式碼。這些合約可以用來實現各種應用，包括去中心化金融、遊戲、投票系統等。

## 文檔
合約（Contract）是 Solidity 中的一種特殊類型，定義了一組狀態變量和函數。合約允許開發者在以太坊網絡上創建和管理資產。每個合約都有其獨特的地址，並且能夠接收和發送以太幣（Ether）以及調用其他合約的函數。

### 目的
合約的主要目的是提供一個安全、透明的平台來執行和自動化各種交易和協議。合約中的代碼一經部署，就無法更改，這確保了執行的不可篡改性。

### 使用
合約的基本結構如下：

```solidity
pragma solidity ^0.8.0;

contract MyContract {
    // 狀態變量
    uint public value;

    // 構造函數
    constructor(uint _value) {
        value = _value;
    }

    // 函數
    function setValue(uint _value) public {
        value = _value;
    }
}
```

在這段代碼中：
- `pragma solidity ^0.8.0;` 指定了使用的 Solidity 版本。
- `contract MyContract` 定義了一個新的合約。
- `value` 是一個可公開訪問的狀態變量。
- `constructor` 是合約的構造函數，初始化狀態變量。
- `setValue` 是一個公共函數，用來修改 `value` 的值。

## 範例
以下是一個簡單的合約範例，展示了如何創建和使用合約：

```solidity
pragma solidity ^0.8.0;

contract SimpleStorage {
    uint storedData;

    function set(uint x) public {
        storedData = x;
    }

    function get() public view returns (uint) {
        return storedData;
    }
}
```

在這個範例中，`SimpleStorage` 合約允許使用者存儲和檢索一個整數數據。

## 解釋
在編寫合約時，開發者需注意以下幾點：
- **狀態變量的存儲成本**：在以太坊上，保存數據需要支付 Gas 費用，應謹慎使用狀態變量。
- **可見性**：函數和變量的可見性（如 `public`, `private`, `internal`, `external`）會影響其訪問權限，需根據需求合理設定。
- **重入攻擊**：在處理 Ether 的轉賬時，需防範重入攻擊，建議使用「檢查-效果-交流」模式。
- **合約升級**：一旦合約部署，代碼無法更改。對於需要更新的合約，建議使用代理模式來管理合約的升級。

## 一句話總結
合約是 Solidity 的基本構建塊，允許開發者在以太坊上創建自動執行的應用程序，確保交易的透明和安全。