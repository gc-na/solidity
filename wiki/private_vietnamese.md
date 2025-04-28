<!--
Meta Description: # Từ Khóa "private" trong Solidity: Kiểm Soát Truy Cập Biến và Hàm ## Tóm tắt Từ khóa "private" trong Solidity được sử dụng để chỉ định quyền truy cập...
Meta Keywords: private, truy, cập, hợp, đồng
-->

# Từ Khóa "private" trong Solidity: Kiểm Soát Truy Cập Biến và Hàm

## Tóm tắt
Từ khóa "private" trong Solidity được sử dụng để chỉ định quyền truy cập cho các biến và hàm, chỉ cho phép chúng được truy cập từ bên trong hợp đồng mà chúng được định nghĩa. Điều này giúp bảo vệ dữ liệu và logic của hợp đồng thông minh.

## Tài liệu
### Mục đích
Từ khóa "private" trong Solidity được sử dụng để quản lý quyền truy cập, giúp bảo vệ các biến và hàm khỏi việc bị truy cập từ các hợp đồng khác hoặc từ bên ngoài.

### Cách sử dụng
Khi một biến hoặc hàm được định nghĩa với từ khóa "private", chỉ có thể truy cập chúng từ bên trong cùng một hợp đồng. Điều này khác với các mức độ truy cập khác như "public" (có thể truy cập từ bất kỳ đâu) và "internal" (có thể truy cập từ hợp đồng kế thừa).

### Cú pháp
```solidity
contract MyContract {
    uint private myPrivateVariable;

    function myPrivateFunction() private {
        // Logic here
    }
}
```

## Ví dụ
### Ví dụ 1: Biến private
```solidity
pragma solidity ^0.8.0;

contract Example {
    uint private secretNumber;

    function setSecretNumber(uint _number) public {
        secretNumber = _number;
    }

    function getSecretNumber() public view returns (uint) {
        return secretNumber;
    }
}
```
Trong ví dụ này, biến `secretNumber` được định nghĩa là private, do đó không thể truy cập từ bên ngoài hợp đồng.

### Ví dụ 2: Hàm private
```solidity
pragma solidity ^0.8.0;

contract Example {
    function externalFunction() public {
        myPrivateFunction();
    }

    function myPrivateFunction() private {
        // Logic chỉ có thể được gọi từ bên trong hợp đồng này
    }
}
```
Hàm `myPrivateFunction` chỉ có thể được gọi từ các hàm khác trong cùng một hợp đồng.

## Giải thích
### Những điều cần lưu ý
- **Không thể kế thừa:** Các biến và hàm được đánh dấu là private sẽ không thể được truy cập từ các hợp đồng con, điều này có thể gây ra sự nhầm lẫn cho những người mới bắt đầu.
- **Kiểm soát quyền truy cập:** Nên sử dụng từ khóa "private" một cách hợp lý để bảo vệ dữ liệu nhạy cảm và logic quan trọng trong hợp đồng thông minh.
- **Không có ảnh hưởng đến gas:** Từ khóa "private" không ảnh hưởng đến chi phí gas khi triển khai hoặc gọi hàm, nhưng nó có thể ảnh hưởng đến cách thiết kế hợp đồng.

## Tóm tắt một dòng
Từ khóa "private" trong Solidity giúp bảo vệ biến và hàm khỏi việc truy cập từ bên ngoài, đảm bảo tính bảo mật cho hợp đồng thông minh.