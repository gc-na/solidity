<!--
Meta Description: # Solidity 中的「override」關鍵字：功能與用法 ## 概述 在 Solidity 中，「override」關鍵字用於子合約中重寫父合約的函數。這一功能使得合約的擴展和修改變得更加靈活，並提高了代碼重用性。 ## 文檔 ### 目的 「override」關鍵字的主要目的是允許開發者在...
Meta Keywords: override, solidity, virtual, child, function
-->

# Solidity 中的「override」關鍵字：功能與用法

## 概述
在 Solidity 中，「override」關鍵字用於子合約中重寫父合約的函數。這一功能使得合約的擴展和修改變得更加靈活，並提高了代碼重用性。

## 文檔
### 目的
「override」關鍵字的主要目的是允許開發者在繼承的合約中重寫父合約的函數。這在面對合約擴展和多重繼承時尤為重要，因為它能夠清晰地指出哪些函數已被重寫。

### 用法
在 Solidity 中，當你想要重寫一個繼承自父合約的函數時，需要在子合約中的函數定義中加入「override」關鍵字。這樣可以保證函數的行為被明確定義，並避免潛在的錯誤。

### 詳細說明
1. **基本語法**：
   ```solidity
   function functionName() public override returns (returnType) {
       // 函數實現
   }
   ```

2. **多重繼承**：
   當合約同時繼承多個父合約時，使用「override」關鍵字能幫助解決函數命名衝突的問題，確保正確的函數被調用。

3. **版本要求**：
   「override」關鍵字在 Solidity 0.6.0 版本中引入，因此在使用之前需確認合約的版本。

## 範例
### 基本用法
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract Parent {
    function greet() public virtual returns (string memory) {
        return "Hello from Parent";
    }
}

contract Child is Parent {
    function greet() public override returns (string memory) {
        return "Hello from Child";
    }
}

// 使用範例
// Child 合約中的 greet 函數會返回 "Hello from Child"
```

## 解釋
### 常見陷阱
- **未使用 virtual**：若父合約中的函數未標記為 `virtual`，則在子合約中不能使用 `override`，否則將會出現編譯錯誤。
- **多重繼承的複雜性**：在多重繼承的情況下，開發者需特別小心函數的重寫，否則可能導致意外的行為。

### 額外注意事項
- 在 Solidity 中，使用多個「override」關鍵字時，需確保所有相關的父合約的函數均已被正確標記為 `virtual`，以避免編譯錯誤。

## 總結
「override」關鍵字在 Solidity 中是用於重寫父合約函數的重要工具，確保了合約的靈活性和可維護性。