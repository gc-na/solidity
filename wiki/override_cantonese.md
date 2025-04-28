<!--
Meta Description: # Solidity 中的 Override 關鍵字：使用與注意事項 ## 摘要 在 Solidity 中，`override` 是一個關鍵字，用於重寫繼承合約中的函數。這個功能使得子合約能夠自定義或修改父合約中的行為，從而提供更大的靈活性和功能擴展。 ## 文檔 ### 目的 `override`...
Meta Keywords: override, solidity, virtual, function, public
-->

# Solidity 中的 Override 關鍵字：使用與注意事項

## 摘要
在 Solidity 中，`override` 是一個關鍵字，用於重寫繼承合約中的函數。這個功能使得子合約能夠自定義或修改父合約中的行為，從而提供更大的靈活性和功能擴展。

## 文檔
### 目的
`override` 關鍵字的主要目的是允許子合約覆蓋其父合約中定義的函數。這在合約繼承時非常重要，因為它確保了子合約能夠根據具體需求調整父合約的行為。

### 用法
在 Solidity 中，當你要在子合約中重寫父合約的函數時，必須在函數聲明中使用 `override` 關鍵字。此外，父合約中的函數也必須標記為 `virtual`，以便能夠被重寫。

### 詳細說明
- **語法**：
  ```solidity
  function functionName() public virtual override {
      // 你的代碼
  }
  ```

- **範例**：
  ```solidity
  // 父合約
  contract Parent {
      function sayHello() public virtual returns (string memory) {
          return "Hello from Parent";
      }
  }

  // 子合約
  contract Child is Parent {
      function sayHello() public override returns (string memory) {
          return "Hello from Child";
      }
  }
  ```

在上面的例子中，`Child` 合約重寫了 `Parent` 合約中的 `sayHello` 函數，並且返回不同的字符串。

## 示例
以下是更具體的示例，展示如何使用 `override` 關鍵字：

```solidity
// 根據 Solidity 0.8.x 語法
pragma solidity ^0.8.0;

contract Base {
    function greet() public virtual returns (string memory) {
        return "Greetings from Base";
    }
}

contract Derived is Base {
    function greet() public override returns (string memory) {
        return "Greetings from Derived";
    }
}
```
在這個例子中，`Derived` 合約覆蓋了 `Base` 合約的 `greet` 函數。

## 解析
在使用 `override` 時，有幾個常見的陷阱和注意事項：
- **虛擬函數**：確保父合約中的函數標記為 `virtual`，否則將無法被重寫。
- **多重繼承**：在多重繼承的情況下，必須清楚指出哪個父合約的函數正在被重寫，這可以通過 `override` 關鍵字來實現。
- **編譯錯誤**：如果未正確使用 `override` 或 `virtual`，編譯器會報錯，提示函數無法重寫。

## 一句總結
在 Solidity 中，`override` 關鍵字允許子合約重寫父合約的函數，從而實現靈活的功能擴展。