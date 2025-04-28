<!--
Meta Description: # Solidity 中的 Struct：如何高效地定義複雜數據類型 ## 概述 在 Solidity 中，`struct` 是用來定義自訂的數據類型，允許開發者將多個不同類型的數據整合在一起，形成一個複雜的數據結構。這對於組織和管理合約中的數據非常重要。 ## 文檔 ### 目的 `struct`...
Meta Keywords: struct, person, solidity, string, uint
-->

# Solidity 中的 Struct：如何高效地定義複雜數據類型

## 概述
在 Solidity 中，`struct` 是用來定義自訂的數據類型，允許開發者將多個不同類型的數據整合在一起，形成一個複雜的數據結構。這對於組織和管理合約中的數據非常重要。

## 文檔
### 目的
`struct` 使開發者能夠創建複雜的數據結構，這些結構可以包含多個屬性，這些屬性可以是不同的數據類型。使用 `struct` 可以提高代碼的可讀性和可維護性。

### 用法
在 Solidity 中，定義 `struct` 的語法如下：
```solidity
struct StructName {
    DataType1 property1;
    DataType2 property2;
    // 其他屬性
}
```
定義後，可以在智能合約中創建 `struct` 的實例，並使用它們來存儲和操作數據。

### 詳細說明
- **定義**: 可以在合約內部或外部定義 `struct`，但通常在合約內部定義會更方便。
- **存儲**: `struct` 的實例可以存儲在狀態變量中，也可以作為函數的參數和返回值。
- **存取**: 可以通過點語法來存取 `struct` 的屬性，例如 `instance.property1`。

## 範例
以下是一個簡單的範例，展示如何定義和使用 `struct`：

```solidity
pragma solidity ^0.8.0;

contract ExampleContract {
    // 定義一個 struct
    struct Person {
        string name;
        uint age;
    }

    // 創建一個狀態變量來存儲 Person struct 的實例
    Person public person;

    // 函數來設置 Person 的屬性
    function setPerson(string memory _name, uint _age) public {
        person = Person(_name, _age);
    }

    // 函數來獲取 Person 的屬性
    function getPerson() public view returns (string memory, uint) {
        return (person.name, person.age);
    }
}
```

## 解釋
使用 `struct` 時，開發者應注意以下幾點：
- **初始值**: `struct` 的成員在創建時會自動初始化為其類型的默認值（例如，`uint` 為 0，`string` 為空）。
- **儲存成本**: 使用 `struct` 會佔用更多的儲存空間，因此在設計合約時需考慮儲存成本。
- **深拷貝**: 當將 `struct` 作為參數傳遞時，會進行深拷貝，這可能影響性能。

## 一句話總結
在 Solidity 中，`struct` 是一種強大的工具，用於定義複雜的數據結構，從而提高合約的可讀性和維護性。