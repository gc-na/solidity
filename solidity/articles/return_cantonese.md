<!--
Meta Description: # Solidity 中的 "return" 關鍵字：功能與用法詳解 ## 簡介 在 Solidity 程式語言中，「return」關鍵字用來從函數中返回值。這個功能對於智能合約的開發至關重要，因為它允許函數在執行後返回結果，並在合約中進行進一步的操作。 ## 文檔 「return」關鍵字的主要用途...
Meta Keywords: solidity, return, uint, public, function
-->

# Solidity 中的 "return" 關鍵字：功能與用法詳解

## 簡介
在 Solidity 程式語言中，「return」關鍵字用來從函數中返回值。這個功能對於智能合約的開發至關重要，因為它允許函數在執行後返回結果，並在合約中進行進一步的操作。

## 文檔
「return」關鍵字的主要用途是從函數返回一個或多個值。使用「return」可以讓開發者獲取函數的計算結果，進而在程式中使用這些結果。

### 用法
- **基本語法**：
  ```solidity
  return value;
  ```
- **返回類型**：函數的返回類型必須在函數聲明中明確指定。例如：
  ```solidity
  function getValue() public pure returns (uint) {
      return 42;
  }
  ```

### 詳細說明
在 Solidity 中，函數可以定義返回值的數量和類型。函數的返回類型可以是基本數據類型（如 uint、int、address 等），也可以是自定義的結構體、數組或其他合約類型。

1. **多個返回值**：
   如果一個函數需要返回多個值，可以在返回類型中用逗號分隔。例如：
   ```solidity
   function getCoordinates() public pure returns (uint, uint) {
       return (10, 20);
   }
   ```

2. **內部函數和外部函數**：
   不同的函數可根據其訪問修飾符（如 public、private、internal、external）來規定其可見性，而返回值的使用方式也會根據函數的類型而有所不同。

## 範例
以下是一些基本的使用範例：

1. 單一返回值的函數範例：
   ```solidity
   pragma solidity ^0.8.0;

   contract Example {
       function returnHello() public pure returns (string memory) {
           return "Hello, Solidity!";
       }
   }
   ```

2. 多重返回值的函數範例：
   ```solidity
   pragma solidity ^0.8.0;

   contract Example {
       function returnValues() public pure returns (uint, uint) {
           return (1, 2);
       }
   }
   ```

## 說明
在使用「return」關鍵字時，開發者需要注意以下幾個常見問題：

- **返回類型不匹配**：如果函數聲明的返回類型與實際返回的值不一致，將導致編譯錯誤。
- **未返回值**：如果函數聲明需要返回值，但實際上沒有使用「return」返回任何值，則將導致錯誤。
- **不支持的類型**：某些類型（如映射）不能直接作為返回值。

## 一行總結
「return」關鍵字在 Solidity 中用來從函數返回值，對於智能合約開發至關重要。