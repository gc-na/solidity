<!--
Meta Description: # Solidity 中的 require：使用與最佳實踐 ## 概述 `require` 是 Solidity 編程語言中的一個關鍵字，用於驗證條件並確保特定狀態或輸入滿足預期。當條件不成立時，`require` 會停止執行並撤銷所有狀態變更。 ## 文檔 ### 目的 `require` 的主要...
Meta Keywords: require, solidity, amount, balance, gas
-->

# Solidity 中的 require：使用與最佳實踐

## 概述
`require` 是 Solidity 編程語言中的一個關鍵字，用於驗證條件並確保特定狀態或輸入滿足預期。當條件不成立時，`require` 會停止執行並撤銷所有狀態變更。

## 文檔
### 目的
`require` 的主要目的是在執行智能合約時確保特定條件成立，這樣可以保護合約的完整性和安全性。

### 使用
`require` 函數的基本語法如下：

```solidity
require(condition, "Error message");
```

- **condition**：一個布爾表達式，當其為 `false` 時，交易將被撤銷。
- **Error message**：當條件不成立時，返回的錯誤消息，便於調試。

### 詳細說明
`require` 通常用於以下情況：
- 驗證輸入參數是否有效。
- 確保合約的狀態滿足某個條件，例如：檢查餘額是否足夠。
- 確認權限或身份驗證，例如：確保調用者是合約的擁有者。

當 `require` 的條件不成立時，所有狀態變更將被撤回，並且消耗的 gas 將不會退還給使用者。

## 範例
以下是 `require` 的基本使用範例：

```solidity
pragma solidity ^0.8.0;

contract Sample {
    uint public balance;

    function deposit(uint amount) public {
        require(amount > 0, "Deposit amount must be greater than 0");
        balance += amount;
    }

    function withdraw(uint amount) public {
        require(amount <= balance, "Insufficient funds");
        balance -= amount;
    }
}
```

在上述範例中：
- `deposit` 函數確保存入的金額必須大於零。
- `withdraw` 函數確保提取的金額不超過餘額。

## 說明
### 常見陷阱
1. **未檢查邊界條件**：使用 `require` 時，應確保所有邊界條件都已處理，否則可能導致不必要的交易失敗。
2. **錯誤消息不明確**：提供清晰的錯誤消息可以幫助開發者快速定位問題。
3. **Gas 消耗**：即使 `require` 失敗，已消耗的 gas 仍然不會退還，因此需要謹慎設計條件。

### 附加說明
- `require` 也可以用於檢查合約內部狀態或其他條件，這樣可以提高合約的安全性。
- 在 Solidity 0.8.0 版本及以後，`require` 的錯誤處理變得更加穩健，支持更詳細的錯誤消息。

## 一句總結
`require` 是 Solidity 中用於條件驗證的核心工具，確保合約執行的安全性和可靠性。