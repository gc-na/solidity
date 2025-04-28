<!--
Meta Description: # Từ Khóa "external" trong Solidity: Định Nghĩa và Cách Sử Dụng ## Tóm Tắt Từ khóa "external" trong Solidity được sử dụng để định nghĩa các hàm có thể...
Meta Keywords: hàm, gọi, external, được, bên
-->

# Từ Khóa "external" trong Solidity: Định Nghĩa và Cách Sử Dụng

## Tóm Tắt
Từ khóa "external" trong Solidity được sử dụng để định nghĩa các hàm có thể được gọi từ bên ngoài hợp đồng thông minh, cho phép các hợp đồng khác và tài khoản bên ngoài tương tác với các hàm này.

## Tài Liệu
Trong Solidity, từ khóa "external" được áp dụng cho các hàm, cho phép chúng được gọi bởi các tài khoản bên ngoài hoặc các hợp đồng khác. Điều này là cần thiết khi bạn muốn cung cấp một giao diện cho người dùng hoặc hợp đồng khác để tương tác với hợp đồng của bạn.

### Mục Đích
- **Gọi từ bên ngoài**: Hàm được đánh dấu là "external" chỉ có thể được gọi từ bên ngoài, không thể được gọi từ bên trong hợp đồng (trừ khi thông qua `this`).
- **Tiết kiệm gas**: Khi hàm được gọi từ bên ngoài, Solidity tối ưu hóa việc sử dụng gas, giúp giảm chi phí giao dịch.

### Cách Sử Dụng
Để định nghĩa một hàm là "external", chỉ cần thêm từ khóa "external" trước tên hàm trong định nghĩa. Ví dụ:

```solidity
pragma solidity ^0.8.0;

contract MyContract {
    uint public value;

    function setValue(uint _value) external {
        value = _value;
    }
}
```

Trong ví dụ trên, hàm `setValue` có thể được gọi từ bên ngoài hợp đồng, cho phép thay đổi giá trị của biến `value`.

## Ví Dụ
### Ví Dụ Cơ Bản
```solidity
pragma solidity ^0.8.0;

contract Example {
    uint public count;

    function increaseCount() external {
        count += 1;
    }
}
```
Trong ví dụ này, hàm `increaseCount` có thể được gọi bởi bất kỳ ai, và khi được gọi, nó sẽ tăng giá trị của biến `count` lên 1.

### Gọi Hàm External Từ Hợp Đồng Khác
```solidity
pragma solidity ^0.8.0;

contract Caller {
    Example exampleContract;

    constructor(address _exampleAddress) {
        exampleContract = Example(_exampleAddress);
    }

    function callIncrease() external {
        exampleContract.increaseCount();
    }
}
```
Hợp đồng `Caller` có thể gọi hàm `increaseCount` từ hợp đồng `Example` nhờ vào từ khóa "external".

## Giải Thích
### Những Lưu Ý Chung
- **Không thể gọi từ bên trong**: Hàm "external" không thể được gọi trực tiếp từ các hàm khác trong cùng một hợp đồng mà không thông qua `this`.
- **Tối ưu hóa gas**: Hàm "external" có thể tiết kiệm gas hơn so với hàm "public" khi được gọi từ bên ngoài.

### Cái Bẫy Thường Gặp
- **Lỗi khi gọi từ bên trong**: Nếu bạn cố gắng gọi hàm "external" từ một hàm khác trong cùng hợp đồng mà không dùng `this`, bạn sẽ gặp lỗi biên dịch.
- **Không nhận giá trị trả về**: Hàm "external" không thể trả về giá trị trực tiếp nếu được gọi từ bên ngoài, bạn cần phải lưu giá trị trả về vào một biến.

## Tóm Tắt Một Câu
Từ khóa "external" trong Solidity cho phép định nghĩa các hàm có thể được gọi từ bên ngoài hợp đồng thông minh, giúp tối ưu hóa hiệu suất và tiết kiệm chi phí giao dịch.