<!--
Meta Description: # Từ Khóa: Immutable trong Solidity - Đặc điểm và Cách Sử Dụng ## Tóm Tắt `immutable` là một từ khóa trong Solidity cho phép khai báo biến mà giá trị ...
Meta Keywords: biến, immutable, trong, constructor, được
-->

# Từ Khóa: Immutable trong Solidity - Đặc điểm và Cách Sử Dụng

## Tóm Tắt
`immutable` là một từ khóa trong Solidity cho phép khai báo biến mà giá trị của nó không thể thay đổi sau khi được khởi tạo trong constructor. Điều này giúp tối ưu hóa chi phí gas và bảo mật trong các hợp đồng thông minh.

## Tài Liệu
### Mục Đích
`immutable` được sử dụng để định nghĩa các biến mà không cần thiết phải thay đổi sau khi chúng đã được thiết lập. Biến `immutable` có thể được khởi tạo một lần duy nhất trong constructor của hợp đồng và mang lại lợi ích trong việc tiết kiệm chi phí gas so với biến `constant`.

### Cách Sử Dụng
Để khai báo một biến `immutable`, bạn sử dụng từ khóa `immutable` trước kiểu dữ liệu của biến. Ví dụ:

```solidity
pragma solidity ^0.8.0;

contract Example {
    uint256 public immutable myImmutableVar;

    constructor(uint256 _value) {
        myImmutableVar = _value;
    }
}
```

Trong đoạn mã trên, `myImmutableVar` sẽ giữ giá trị được truyền vào constructor và không thể thay đổi sau đó.

### Chi Tiết
- Biến `immutable` phải được khởi tạo trong constructor của hợp đồng.
- Sau khi constructor hoàn thành, giá trị của biến không thể thay đổi.
- Sử dụng `immutable` giúp tiết kiệm gas vì nó không yêu cầu lưu trữ giá trị biến trong trạng thái của hợp đồng.

## Ví Dụ
### Ví Dụ 1: Khởi Tạo Biến Immutable
```solidity
pragma solidity ^0.8.0;

contract Token {
    address public immutable owner;

    constructor() {
        owner = msg.sender; // Khởi tạo biến owner với địa chỉ của người gọi
    }
}
```

### Ví Dụ 2: Biến Immutable với Tham Số
```solidity
pragma solidity ^0.8.0;

contract Calculator {
    uint256 public immutable base;

    constructor(uint256 _base) {
        base = _base; // Khởi tạo biến base với giá trị được truyền vào
    }

    function add(uint256 value) public view returns (uint256) {
        return base + value; // Sử dụng biến immutable trong hàm
    }
}
```

## Giải Thích
### Lỗi Thường Gặp
- **Cố Gắng Thay Đổi Giá Trị**: Một khi biến `immutable` đã được khởi tạo trong constructor, cố gắng thay đổi giá trị của nó sẽ dẫn đến lỗi biên dịch.
- **Khởi Tạo Ngoài Constructor**: Nếu bạn cố gắng khởi tạo biến `immutable` bên ngoài constructor, bạn sẽ nhận được thông báo lỗi.

### Lưu Ý
- Biến `immutable` là một lựa chọn tốt hơn cho những giá trị không thay đổi, giúp tối ưu hóa chi phí gas so với việc sử dụng biến `constant` khi cần phải sử dụng giá trị đó trong các hàm.

## Tóm Tắt Một Câu
`immutable` trong Solidity là một từ khóa cho phép khai báo biến không thay đổi sau khi được thiết lập trong constructor, tối ưu hóa chi phí gas và tăng cường bảo mật cho hợp đồng thông minh.