<!--
Meta Description: # Solidity中的payable關鍵字：用途與範例 ## 概述 在Solidity中，`payable`是一個關鍵字，用於標記可以接收以太幣的函數或地址。此關鍵字對於建立去中心化應用程式（DApps）至關重要，因為它使智能合約能夠處理以太幣交易。 ## 文檔 `payable`的主要目的是允許...
Meta Keywords: payable, solidity, 在solidity中, function, public
-->

# Solidity中的payable關鍵字：用途與範例

## 概述
在Solidity中，`payable`是一個關鍵字，用於標記可以接收以太幣的函數或地址。此關鍵字對於建立去中心化應用程式（DApps）至關重要，因為它使智能合約能夠處理以太幣交易。

## 文檔
`payable`的主要目的是允許合約或函數接收以太幣。在Solidity中，任何函數如果需要能夠接收以太幣，都必須標記為`payable`。當用戶向合約發送以太幣時，這個標記讓合約能夠正確處理這些資金。

### 用法
- **函數**：當一個函數被標記為`payable`，它可以接收以太幣。這意味著在調用這個函數時，交易中可以包含以太幣。
- **地址**：當一個地址被標記為`payable`，它可以接收以太幣轉帳。

### 詳細信息
1. **函數聲明**：在函數的定義中加入`payable`關鍵字，例如：
   ```solidity
   function deposit() public payable {
       // 函數邏輯
   }
   ```
2. **以太幣轉帳**：使用`transfer`或`send`函數將以太幣發送到`payable`地址：
   ```solidity
   address payable recipient = payable(0x123...);
   recipient.transfer(1 ether);
   ```

## 範例
以下是使用`payable`的基本範例：

### 範例1：接收以太幣
```solidity
pragma solidity ^0.8.0;

contract SimpleWallet {
    receive() external payable {
        // 接收以太幣
    }
}
```

### 範例2：支付函數
```solidity
pragma solidity ^0.8.0;

contract Payment {
    function pay() public payable {
        require(msg.value > 0, "Must send Ether");
        // 處理支付邏輯
    }
}
```

## 解釋
在使用`payable`時，有一些常見的注意事項：
- **未標記的函數無法接收以太幣**：如果函數未標記為`payable`，則任何試圖發送以太幣的交易將會失敗。
- **安全性考量**：在處理以太幣時必須小心，避免重入攻擊等安全問題。
- **Gas限制**：調用`payable`函數時需要考慮Gas限制，因為以太坊網絡會有交易成本。

## 總結
`payable`關鍵字在Solidity中是接收以太幣的必要元素，確保智能合約能夠安全有效地處理以太幣交易。