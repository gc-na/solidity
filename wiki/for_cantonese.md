<!--
Meta Description: # Solidity 中的 "for" 循環：用法與示例 ## 概述 在 Solidity 編程語言中，`for` 循環是一種用於重複執行一段代碼的控制結構。它對於處理數組、計算和重複任務非常有用。 ## 文檔 `for` 循環的基本語法如下： ```solidity for (初始化; 條件; 更...
Meta Keywords: uint256, solidity, numbers, sum, public
-->

# Solidity 中的 "for" 循環：用法與示例

## 概述
在 Solidity 編程語言中，`for` 循環是一種用於重複執行一段代碼的控制結構。它對於處理數組、計算和重複任務非常有用。

## 文檔
`for` 循環的基本語法如下：

```solidity
for (初始化; 條件; 更新) {
    // 執行的代碼
}
```

### 目的
`for` 循環允許開發者在特定條件下重複執行代碼塊，這在處理集合或需要重複計算的場景中非常常見。

### 用法
- **初始化**：設置一個變量，通常用於計數。
- **條件**：循環將在此條件為真時執行。
- **更新**：每次循環結束後的變量更新。

### 詳細說明
`for` 循環在 Solidity 中的運作方式與其他編程語言相似，但需注意在智能合約中使用循環的成本和 Gas 限制。

## 示例
以下是一些基本的 `for` 循環用法示例：

### 示例 1：計算總和
```solidity
pragma solidity ^0.8.0;

contract Sum {
    function calculateSum(uint256 n) public pure returns (uint256) {
        uint256 sum = 0;
        for (uint256 i = 1; i <= n; i++) {
            sum += i;
        }
        return sum;
    }
}
```

### 示例 2：遍歷數組
```solidity
pragma solidity ^0.8.0;

contract ArrayExample {
    uint256[] public numbers;

    function addNumber(uint256 number) public {
        numbers.push(number);
    }

    function getNumbers() public view returns (uint256[] memory) {
        uint256[] memory result = new uint256[](numbers.length);
        for (uint256 i = 0; i < numbers.length; i++) {
            result[i] = numbers[i];
        }
        return result;
    }
}
```

## 解釋
在使用 `for` 循環時，開發者需要注意以下幾點：
- **Gas 成本**：循環的次數會影響執行成本，過多的循環可能導致交易失敗。
- **條件設定**：確保循環條件能正確終止，以防止無限循環。
- **數據類型**：使用合適的數據類型以避免溢出，特別是在計算總和等操作時。

## 總結
`for` 循環是一種靈活且強大的工具，可以幫助 Solidity 開發者高效地處理重複性任務。