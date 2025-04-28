<!--
Meta Description: # Override trong Solidity: Hiểu Biết Cần Thiết cho Lập Trình Hợp Đồng Thông Minh ## Tóm tắt `override` là một từ khóa quan trọng trong ngôn ngữ lập tr...
Meta Keywords: hàm, hợp, đồng, ghi, trong
-->

# Override trong Solidity: Hiểu Biết Cần Thiết cho Lập Trình Hợp Đồng Thông Minh

## Tóm tắt
`override` là một từ khóa quan trọng trong ngôn ngữ lập trình Solidity, cho phép lập trình viên ghi đè các hàm từ các hợp đồng cha trong các hợp đồng con, giúp tăng cường khả năng mở rộng và tái sử dụng mã.

## Tài liệu
### Mục đích
Từ khóa `override` được sử dụng khi bạn muốn ghi đè một hàm đã được định nghĩa trong một hợp đồng cha. Điều này rất hữu ích cho việc kế thừa, cho phép các hợp đồng con thay đổi hoặc mở rộng hành vi của hợp đồng cha mà không cần phải viết lại mã hoàn toàn.

### Cách sử dụng
Khi bạn định nghĩa một hàm trong hợp đồng con với cùng tên và cùng tham số như một hàm trong hợp đồng cha, bạn cần sử dụng từ khóa `override`. Đây là cách mà Solidity đảm bảo rằng bạn có ý định ghi đè hàm đó.

Cú pháp cơ bản:
```solidity
contract Parent {
    function exampleFunction() virtual public returns (string memory) {
        return "Parent";
    }
}

contract Child is Parent {
    function exampleFunction() override public returns (string memory) {
        return "Child";
    }
}
```

### Chi tiết
- Từ khóa `virtual` phải được sử dụng trong hợp đồng cha để cho biết rằng hàm có thể bị ghi đè.
- Khi bạn ghi đè một hàm, bạn cũng có thể gọi hàm của hợp đồng cha bằng cách sử dụng `super`.

## Ví dụ
### Ví dụ 1: Ghi đè hàm đơn giản
```solidity
pragma solidity ^0.8.0;

contract Animal {
    function sound() virtual public pure returns (string memory) {
        return "Some sound";
    }
}

contract Dog is Animal {
    function sound() override public pure returns (string memory) {
        return "Woof!";
    }
}
```

### Ví dụ 2: Ghi đè và gọi hàm cha
```solidity
pragma solidity ^0.8.0;

contract Vehicle {
    function start() virtual public pure returns (string memory) {
        return "Vehicle started";
    }
}

contract Car is Vehicle {
    function start() override public pure returns (string memory) {
        return string(abi.encodePacked(super.start(), " and Car started"));
    }
}
```

## Giải thích
### Những điều cần lưu ý
- **Bắt buộc sử dụng `virtual`**: Nếu bạn không định nghĩa hàm trong hợp đồng cha là `virtual`, bạn sẽ không thể ghi đè nó trong hợp đồng con.
- **Không ghi đè hàm không công khai**: Bạn chỉ có thể ghi đè các hàm có độ truy cập công khai (`public`) hoặc nội bộ (`internal`).
- **Nhiều cấp kế thừa**: Khi có nhiều cấp kế thừa, bạn phải chú ý đến thứ tự ghi đè hàm.

## Tóm tắt một dòng
Từ khóa `override` trong Solidity cho phép các hợp đồng con ghi đè các hàm từ hợp đồng cha, cung cấp tính năng mở rộng và tái sử dụng mã hiệu quả.