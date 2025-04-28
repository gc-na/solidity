<!--
Meta Description: # Solidity 的 enum：使用與範例 ## 摘要 在 Solidity 中，`enum` 是一種用於定義一組命名常量的數據類型，常用於增強代碼的可讀性和可維護性。 ## 文檔 `enum`（列舉型別）為 Solidity 提供了一種在智能合約中定義狀態或類別的方式。透過定義一組可選值，開發...
Meta Keywords: enum, taskstatus, solidity, notstarted, status
-->

# Solidity 的 enum：使用與範例

## 摘要
在 Solidity 中，`enum` 是一種用於定義一組命名常量的數據類型，常用於增強代碼的可讀性和可維護性。

## 文檔
`enum`（列舉型別）為 Solidity 提供了一種在智能合約中定義狀態或類別的方式。透過定義一組可選值，開發者可以清楚地表達變量的可能狀態，提高代碼的可讀性和安全性。

### 目的
使用 `enum` 可以讓開發者在代碼中使用具名常量來表示狀態，這比使用整數或字串更具可讀性，並且可以減少錯誤。

### 用法
`enum` 的基本語法如下：

```solidity
enum EnumName {
    Option1,
    Option2,
    Option3
}
```

在智能合約中，可以定義一個 `enum`，並且利用它來聲明變量。這些變量將只能被賦值為該 `enum` 中的選項。

### 範例
以下是一個簡單的 `enum` 使用範例：

```solidity
pragma solidity ^0.8.0;

contract TaskManager {
    enum TaskStatus { NotStarted, InProgress, Completed }

    struct Task {
        string name;
        TaskStatus status;
    }

    Task[] public tasks;

    function createTask(string memory _name) public {
        tasks.push(Task({
            name: _name,
            status: TaskStatus.NotStarted
        }));
    }

    function startTask(uint _taskIndex) public {
        tasks[_taskIndex].status = TaskStatus.InProgress;
    }

    function completeTask(uint _taskIndex) public {
        tasks[_taskIndex].status = TaskStatus.Completed;
    }
}
```

在這個範例中，我們定義了一個 `TaskStatus` 的 `enum`，用於表示任務的狀態。

## 解釋
在使用 `enum` 時，需要注意以下幾點：

- **預設值**：當一個 `enum` 變量被聲明但未被初始化時，會自動設為第一個選項（此例中是 `NotStarted`）。
- **整數值**：`enum` 的每個選項都有一個整數值，從 0 開始遞增。這意味著 `TaskStatus.NotStarted` 的值為 0，`TaskStatus.InProgress` 為 1，`TaskStatus.Completed` 為 2。
- **可擴展性**：在選項中添加新的值不會影響現有的值，但在合約已經部署後，無法刪除選項。
- **安全性**：使用 `enum` 可以防止不合法的狀態被賦值，這是使用整數或字串所無法提供的。

## 一句總結
`enum` 是 Solidity 中用於定義命名常量集合的數據類型，可增強代碼的可讀性和安全性。