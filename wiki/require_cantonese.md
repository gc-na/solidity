<!--
Meta Description: # Solidity 中的 `require` 指令詳解 ## 簡介 `require` 是 Solidity 中的一個重要指令，用於檢查條件是否成立，確保合約中的執行邏輯正確。當條件不滿足時，`require` 將會停止合約執行並撤銷所有狀態變更。 ## 文檔 ### 目的 `require` 的...
Meta Keywords: require, solidity, gas, address, amount
-->

# Solidity 中的 `require` 指令詳解

## 簡介
`require` 是 Solidity 中的一個重要指令，用於檢查條件是否成立，確保合約中的執行邏輯正確。當條件不滿足時，`require` 將會停止合約執行並撤銷所有狀態變更。

## 文檔
### 目的
`require` 的主要目的是在合約執行過程中進行必要的驗證，確保合約的運行環境及參數的合法性。這有助於防止意外或惡意操作導致不良後果。

### 使用方法
`require` 的基本語法如下：
```solidity
require(condition, "Error message");
```
- `condition`: 一個布林表達式，若為 `false`，則執行將中止。
- `"Error message"`: 可選的錯誤信息，當條件不成立時，這信息將被返回。

### 詳細說明
在 Solidity 中，`require` 常用於：
- 驗證輸入參數的有效性。
- 確認合約狀態是否符合預期。
- 檢查合約調用者的權限。

當 `require` 條件失敗時，合約的執行會立即停止，所有狀態變更將不會被保存，並且會消耗掉所有的 gas。這使得 `require` 成為一個強大的工具，用於保護合約的邏輯。

## 範例
以下是使用 `require` 的基本範例：

### 範例 1: 驗證地址
```solidity
function transfer(address to, uint256 amount) public {
    require(to != address(0), "Invalid address");
    // 進一步的轉帳邏輯
}
```

### 範例 2: 驗證餘額
```solidity
function withdraw(uint256 amount) public {
    require(balance[msg.sender] >= amount, "Insufficient balance");
    // 提現邏輯
}
```

## 解釋
使用 `require` 時，開發者需注意以下幾點：
- **Gas 消耗**: 當 `require` 失敗時，所有已消耗的 gas 將不會退還。這意味著不應過度使用 `require`，以免造成不必要的成本。
- **錯誤信息**: 提供清晰的錯誤信息有助於調試和用戶理解問題。
- **邏輯順序**: 確保 `require` 的檢查在合約邏輯的正確執行之前，避免不必要的計算。

## 總結
`require` 是 Solidity 中用於檢查條件的重要工具，確保合約的執行邏輯正確且安全。