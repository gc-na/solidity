<!--
Meta Description: # Solidity 中的 Struct：使用與示例 ## 簡介 在 Solidity 中，`struct` 是用來定義複雜數據結構的關鍵字，允許開發者將多個不同類型的數據組合在一起，形成一個新的數據類型。 ## 文件說明 `struct` 是 Solidity 的一種數據類型，用來創建自定義結構。...
Meta Keywords: struct, person, solidity, string, name
-->

# Solidity 中的 Struct：使用與示例

## 簡介
在 Solidity 中，`struct` 是用來定義複雜數據結構的關鍵字，允許開發者將多個不同類型的數據組合在一起，形成一個新的數據類型。

## 文件說明
`struct` 是 Solidity 的一種數據類型，用來創建自定義結構。它可以包含多個變量，這些變量可以是不同類型的數據。使用 `struct` 可以使合約的數據管理更加清晰和結構化。

### 目的
`struct` 主要用於組織和管理相關的數據，使得合約的數據更具可讀性和可維護性。它特別適合用於需要存儲複雜數據的場景，如用戶信息、商品詳情等。

### 用法
要定義一個 `struct`，可以使用以下語法：

```solidity
struct StructName {
    DataType1 variable1;
    DataType2 variable2;
    // 更多變量
}
```

定義完畢後，可以創建 `struct` 的實例並使用其屬性。

## 示例
以下是一個簡單的 `struct` 定義及其使用示例：

```solidity
pragma solidity ^0.8.0;

contract Example {
    struct Person {
        string name;
        uint age;
    }

    Person public person;

    function setPerson(string memory _name, uint _age) public {
        person = Person(_name, _age);
    }

    function getPerson() public view returns (string memory, uint) {
        return (person.name, person.age);
    }
}
```

在這個例子中，我們定義了一個名為 `Person` 的 `struct`，它包含 `name` 和 `age` 兩個屬性。我們還提供了設置和獲取 `Person` 信息的函數。

## 解釋
在使用 `struct` 時，開發者應留意以下幾點：

1. **存儲成本**：`struct` 會佔用存儲空間，因此應考慮其結構的大小。過大的 `struct` 可能會導致高昂的交易費用。
2. **可變性**：`struct` 的屬性默認是可變的，開發者應根據需求決定是否需要將某些屬性設置為 `constant` 或 `immutable`。
3. **初始化**：在 Solidity 中，未初始化的 `struct` 會有默認值，這可能導致數據錯誤，因此在使用前應確保正確初始化。

## 一句總結
`struct` 是 Solidity 中用來定義複雜數據結構的強大工具，使數據管理更加高效和結構化。