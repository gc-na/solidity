<!--
Meta Description: # Solidity 中的 assert 指令：用途及最佳實踐 ## 摘要 `assert` 是 Solidity 語言中的一個關鍵字，用於檢查條件是否為真，並在條件不成立時觸發錯誤。這是一種用於驗證不應該出現的狀態的有力工具。 ## 文檔 在 Solidity 中，`assert` 用於檢查程式中...
Meta Keywords: assert, solidity, totalsupply, require, condition
-->

# Solidity 中的 assert 指令：用途及最佳實踐

## 摘要
`assert` 是 Solidity 語言中的一個關鍵字，用於檢查條件是否為真，並在條件不成立時觸發錯誤。這是一種用於驗證不應該出現的狀態的有力工具。

## 文檔
在 Solidity 中，`assert` 用於檢查程式中的不變條件。與 `require` 和 `revert` 不同，`assert` 通常用於檢查程式碼中的錯誤，這些錯誤是無法恢復的，代表程式碼存在嚴重問題。當 `assert` 的條件不成立時，將會導致交易失敗，並且所有的狀態變更將會被撤回。

### 用法
`assert` 的基本語法如下：
```solidity
assert(condition);
```
這裡的 `condition` 是一個布林表達式，如果其值為 `false`，則會觸發錯誤。

### 詳細說明
- **目的**：用於檢查不應該發生的情況，通常用於內部邏輯錯誤的檢查。
- **使用場合**：適合在開發階段進行測試，或用於檢查合約的關鍵不變性。
- **性能影響**：`assert` 會消耗較高的 gas，因為一旦條件不成立，交易將會被完全撤回。

## 範例
以下是一個簡單的範例，演示 `assert` 的使用：

```solidity
pragma solidity ^0.8.0;

contract Example {
    uint public totalSupply;

    function setTotalSupply(uint _supply) public {
        totalSupply = _supply;
        // 確保 totalSupply 不會為負數
        assert(totalSupply >= 0);
    }
}
```
在上面的範例中，若 `totalSupply` 被設置為負數，則會觸發 `assert`，導致交易失敗。

## 解釋
- **常見陷阱**：使用 `assert` 檢查用戶輸入的有效性是錯誤的，因為這些情況應該使用 `require` 來處理。`assert` 應僅用於檢查程式碼的邏輯錯誤。
- **狀態變更影響**：使用 `assert` 將導致所有狀態變更被撤回，這與 `require` 不同，後者會根據條件決定是否撤回狀態變更。
- **錯誤信息**：`assert` 不會提供錯誤信息，這使得調試變得更加困難，所以在開發過程中，應謹慎使用。

## 一句總結
`assert` 是 Solidity 中用於檢查不應發生的邏輯錯誤的重要工具，當條件不成立時會導致交易失敗。