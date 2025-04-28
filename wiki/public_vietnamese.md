<!--
Meta Description: # Từ Khóa "public" trong Solidity: Tính Năng và Cách Sử Dụng ## Tóm Tắt Từ khóa "public" trong Solidity được sử dụng để xác định mức độ truy cập của b...
Meta Keywords: public, contract, solidity, truy, cập
-->

# Từ Khóa "public" trong Solidity: Tính Năng và Cách Sử Dụng

## Tóm Tắt
Từ khóa "public" trong Solidity được sử dụng để xác định mức độ truy cập của biến, hàm và contract, cho phép chúng có thể được truy cập từ bên ngoài.

## Tài Liệu
Từ khóa "public" trong Solidity là một phần quan trọng của cơ chế kiểm soát quyền truy cập. Khi một biến hoặc hàm được khai báo là "public", nó có thể được truy cập và sử dụng từ bên ngoài contract. Điều này đặc biệt hữu ích khi bạn muốn cho phép các bên thứ ba, như dApps hoặc các contract khác, có thể tương tác với dữ liệu của mình.

### Mục Đích
- **Truy Cập Mở:** Cho phép bất kỳ ai cũng có thể gọi hàm hoặc truy cập biến.
- **Tạo Giao Diện:** Cung cấp giao diện dễ dàng cho người dùng hoặc các contract khác để tương tác với contract của bạn.

### Cách Sử Dụng
Để khai báo một biến hoặc hàm là "public", bạn chỉ cần thêm từ khóa "public" trước tên biến hoặc hàm. Dưới đây là cú pháp cơ bản:

```solidity
pragma solidity ^0.8.0;

contract MyContract {
    uint public myVariable;

    function myFunction() public {
        // logic
    }
}
```

Trong ví dụ trên, `myVariable` và `myFunction` đều có thể được truy cập từ bên ngoài contract.

## Ví Dụ
Dưới đây là một số ví dụ cụ thể về cách sử dụng từ khóa "public":

### Ví dụ 1: Khai Báo Biến Public
```solidity
pragma solidity ^0.8.0;

contract Example {
    uint public number;

    constructor(uint _number) {
        number = _number;
    }
}
```
Biến `number` có thể được truy cập từ bên ngoài contract.

### Ví dụ 2: Khai Báo Hàm Public
```solidity
pragma solidity ^0.8.0;

contract Example {
    uint private total;

    function add(uint _value) public {
        total += _value;
    }

    function getTotal() public view returns (uint) {
        return total;
    }
}
```
Hàm `add` và `getTotal` có thể được gọi từ bên ngoài contract.

## Giải Thích
Mặc dù từ khóa "public" rất dễ sử dụng, có một số điều cần lưu ý:
- **Bảo Mật:** Nếu bạn không muốn cho phép truy cập từ bên ngoài, bạn nên sử dụng từ khóa "private" hoặc "internal" để bảo vệ dữ liệu của mình.
- **Gas Cost:** Các hàm public có thể tốn gas khi được gọi từ một contract khác, vì vậy nên cân nhắc trước khi thiết kế.

## Tóm Tắt Một Dòng
Từ khóa "public" trong Solidity cho phép các biến và hàm được truy cập từ bên ngoài contract, cung cấp giao diện tương tác dễ dàng cho các bên thứ ba.