<!--
Meta Description: # Solidity 中的 import 指令：導入合約與庫的完整指南 ## 概述 在 Solidity 中，`import` 指令允許開發者將其他合約或庫的代碼納入當前合約文件，這樣可以促進代碼的重用和模組化，提高開發效率。 ## 文件說明 `import` 指令的主要目的是讓開發者可以分割大型合...
Meta Keywords: import, solidity, sol, library, maincontract
-->

# Solidity 中的 import 指令：導入合約與庫的完整指南

## 概述
在 Solidity 中，`import` 指令允許開發者將其他合約或庫的代碼納入當前合約文件，這樣可以促進代碼的重用和模組化，提高開發效率。

## 文件說明
`import` 指令的主要目的是讓開發者可以分割大型合約，將其邏輯模組化，並能夠在多個合約之間共享代碼。這不僅提升了代碼的可讀性，還能夠減少重複代碼的出現。

### 語法
```solidity
import "路徑/文件名.sol";
```
或者使用相對路徑：
```solidity
import "./文件名.sol";
```

### 使用情境
- 導入外部庫以增加功能。
- 將共享邏輯分隔到不同的合約文件中。
- 方便進行版本管理和代碼維護。

## 示例
以下是一些基本的 `import` 用法示例：

### 導入單個合約
```solidity
// MainContract.sol
import "./Library.sol";

contract MainContract {
    Library lib;

    constructor() {
        lib = new Library();
    }
}
```

### 導入多個合約
```solidity
// MainContract.sol
import "./Library.sol";
import "./AnotherLibrary.sol";

contract MainContract {
    Library lib;
    AnotherLibrary anotherLib;

    constructor() {
        lib = new Library();
        anotherLib = new AnotherLibrary();
    }
}
```

### 導入特定功能
```solidity
// MainContract.sol
import { FunctionName } from "./Library.sol";

contract MainContract {
    function callFunction() public {
        FunctionName();
    }
}
```

## 解釋
在使用 `import` 指令時，開發者需注意以下幾點：

1. **路徑正確性**：確保導入的路徑正確，若路徑錯誤會導致編譯失敗。
2. **循環導入**：避免循環導入，這會導致無法編譯的錯誤。
3. **版本相容性**：導入的合約或庫應與當前合約使用的 Solidity 版本相容，否則可能會出現無法預期的行為。

## 總結
`import` 指令是 Solidity 中一個強大的功能，用於促進代碼重用和模組化，幫助開發者更高效地管理合約代碼。