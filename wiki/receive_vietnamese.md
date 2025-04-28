<!--
Meta Description: # Hàm "receive" trong Solidity: Cách Nhận Ether trong Hợp Đồng Thông Minh ## Tóm tắt Hàm `receive` trong Solidity là một hàm đặc biệt cho phép hợp đồn...
Meta Keywords: hàm, receive, hợp, đồng, không
-->

# Hàm "receive" trong Solidity: Cách Nhận Ether trong Hợp Đồng Thông Minh

## Tóm tắt
Hàm `receive` trong Solidity là một hàm đặc biệt cho phép hợp đồng thông minh nhận Ether trực tiếp mà không cần phải gọi hàm nào.

## Tài liệu
Hàm `receive` được giới thiệu trong phiên bản Solidity 0.6.0. Nó được sử dụng để xử lý các giao dịch gửi Ether đến hợp đồng mà không kèm theo dữ liệu. Khi một giao dịch gửi Ether đến hợp đồng mà không kèm theo thông tin, hàm `receive` sẽ được gọi tự động. Nếu không có hàm `receive`, giao dịch sẽ bị từ chối.

### Cú pháp
```solidity
receive() external payable {
    // logic here
}
```

### Mục đích
Mục đích chính của hàm `receive` là để cung cấp một cách đơn giản và hiệu quả để nhận Ether trong hợp đồng thông minh mà không cần phải có một hàm truyền thống. Điều này giúp giảm thiểu sự phức tạp trong việc xử lý các giao dịch đơn giản.

### Sử dụng
- Hàm `receive` là `external` và phải có từ khóa `payable` để cho phép nhận Ether.
- Chỉ có một hàm `receive` trong mỗi hợp đồng; nếu bạn định nghĩa nhiều hơn một, biên biên dịch sẽ báo lỗi.
- Nếu hợp đồng có hàm `fallback`, hàm này sẽ được gọi khi không có hàm `receive` phù hợp.

## Ví dụ
Dưới đây là một ví dụ đơn giản về cách sử dụng hàm `receive` trong hợp đồng thông minh:

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract MyContract {
    event Received(address sender, uint amount);

    receive() external payable {
        emit Received(msg.sender, msg.value);
    }
}
```

Trong ví dụ trên, mỗi lần hợp đồng nhận Ether, một sự kiện sẽ được phát ra với địa chỉ người gửi và số tiền đã nhận.

## Giải thích
### Những vấn đề thường gặp
- **Không có hàm `receive`**: Nếu hợp đồng không có hàm `receive` và có một giao dịch gửi Ether, giao dịch sẽ bị từ chối.
- **Giao dịch không có dữ liệu**: Hàm `receive` chỉ được gọi khi giao dịch không có dữ liệu. Nếu có dữ liệu, hàm `fallback` sẽ được gọi.
- **Giới hạn về gas**: Khi giao dịch gửi Ether đến hợp đồng, hãy đảm bảo rằng có đủ gas để thực thi hàm `receive`.

## Tóm tắt một câu
Hàm `receive` trong Solidity cho phép hợp đồng thông minh nhận Ether mà không cần phải gọi hàm cụ thể, giúp đơn giản hóa quá trình xử lý giao dịch.