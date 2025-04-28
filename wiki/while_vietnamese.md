<!--
Meta Description: # Câu Lệnh "while" Trong Solidity: Cách Sử Dụng và Những Điều Cần Lưu Ý ## Tóm Tắt Câu lệnh "while" trong Solidity là một cấu trúc điều khiển lặp, cho...
Meta Keywords: điều, lặp, kiện, while, trong
-->

# Câu Lệnh "while" Trong Solidity: Cách Sử Dụng và Những Điều Cần Lưu Ý

## Tóm Tắt
Câu lệnh "while" trong Solidity là một cấu trúc điều khiển lặp, cho phép thực thi một khối mã nhiều lần miễn là điều kiện xác định là đúng.

## Tài Liệu
Câu lệnh "while" được sử dụng để lặp lại một khối mã cho đến khi điều kiện kiểm tra trở thành sai. Cú pháp cơ bản của câu lệnh "while" trong Solidity như sau:

```solidity
while (điều_kiện) {
    // Khối mã thực thi
}
```

### Mục Đích
- **Lặp lại mã**: "while" cho phép thực thi một đoạn mã cho đến khi điều kiện không còn đúng.
- **Tiết kiệm không gian**: Giúp giảm thiểu mã lặp lại bằng cách gom nhóm trong một khối.

### Cách Sử Dụng
1. **Đặt điều kiện**: Điều kiện phải trả về giá trị boolean (true hoặc false).
2. **Khối mã**: Khối mã bên trong sẽ được thực thi miễn là điều kiện vẫn là true.

## Ví Dụ
### Ví dụ 1: Lặp qua số
```solidity
pragma solidity ^0.8.0;

contract WhileExample {
    uint256 public count;

    function countToTen() public {
        count = 0;
        while (count < 10) {
            count++;
        }
    }
}
```
Trong ví dụ này, hàm `countToTen` sẽ tăng giá trị của biến `count` từ 0 đến 10 thông qua vòng lặp "while".

### Ví dụ 2: Tính tổng các số
```solidity
pragma solidity ^0.8.0;

contract SumExample {
    function sum(uint256 n) public pure returns (uint256) {
        uint256 total = 0;
        uint256 i = 0;

        while (i < n) {
            total += i;
            i++;
        }
        return total;
    }
}
```
Hàm `sum` tính tổng tất cả các số từ 0 đến n-1.

## Giải Thích
### Những Điều Cần Lưu Ý
- **Điều kiện không bao giờ sai**: Nếu điều kiện trong vòng lặp "while" không bao giờ trở thành false, sẽ gây ra lỗi tràn (out of gas) do vòng lặp vô hạn.
- **Sử dụng gas**: Mỗi lần lặp sẽ tiêu tốn gas, do đó cần cẩn trọng trong việc sử dụng vòng lặp trong các hàm có thể gọi từ bên ngoài.
- **Kiểm tra điều kiện**: Đảm bảo rằng điều kiện được cập nhật bên trong vòng lặp để tránh vòng lặp vô hạn.

## Tóm Tắt Một Câu
Câu lệnh "while" trong Solidity là một cấu trúc điều khiển lặp cho phép thực hiện một khối mã cho đến khi điều kiện trở thành sai, nhưng cần cẩn trọng với việc cập nhật điều kiện để tránh vòng lặp vô hạn.