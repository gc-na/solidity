<!--
Meta Description: # Solidity 中的函數 (Function) ## 摘要 在 Solidity 中，函數是智能合約的基本構建單位，負責執行特定的操作或計算，並可被外部調用或內部使用。 ## 文檔 函數在 Solidity 中用於將代碼邏輯封裝為可重用的單元。開發者可以使用函數來執行計算、改變狀態或返回值。函...
Meta Keywords: solidity, uint256, function, public, returns
-->

# Solidity 中的函數 (Function)

## 摘要
在 Solidity 中，函數是智能合約的基本構建單位，負責執行特定的操作或計算，並可被外部調用或內部使用。

## 文檔
函數在 Solidity 中用於將代碼邏輯封裝為可重用的單元。開發者可以使用函數來執行計算、改變狀態或返回值。函數的基本語法如下：

```solidity
function functionName(parameters) visibility returns (returnType) {
    // 函數邏輯
}
```

### 主要組件

1. **名稱 (functionName)**: 函數的識別名稱，必須是唯一的。
2. **參數 (parameters)**: 輸入到函數的變數，支持多個參數。
3. **可見性 (visibility)**: 定義函數的可見性，常見選項有 `public`、`private`、`internal` 和 `external`。
4. **返回值 (returns)**: 定義函數的返回類型，可以是單一值或多個值。

### 函數修飾符
可選的修飾符如 `view`、`pure` 和 `payable` 提供了額外的功能：
- **view**: 表示函數不會改變狀態。
- **pure**: 表示函數不會讀取或改變狀態。
- **payable**: 允許函數接收以太幣。

## 示例
以下是幾個簡單的函數示例：

### 基本函數
```solidity
pragma solidity ^0.8.0;

contract Example {
    uint256 public value;

    function setValue(uint256 _value) public {
        value = _value;
    }

    function getValue() public view returns (uint256) {
        return value;
    }
}
```

### 帶有返回值的函數
```solidity
pragma solidity ^0.8.0;

contract Calculator {
    function add(uint256 a, uint256 b) public pure returns (uint256) {
        return a + b;
    }
}
```

## 解釋
在使用函數時，有幾個常見的陷阱和注意事項：
- **可見性**: 忘記設置可見性會導致編譯錯誤。
- **狀態變更**: 使用 `view` 和 `pure` 修飾符時，不應更改合約狀態。
- **參數類型**: 確保參數類型正確，否則可能導致運行時錯誤。
- **Gas費用**: 函數的執行會消耗Gas，複雜的計算可能導致高成本。

## 總結
函數是 Solidity 中的重要組件，幫助開發者分解代碼並提高可重用性與可讀性。