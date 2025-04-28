<!--
Meta Description: # Sự kiện (Event) trong Solidity: Tìm hiểu và Ứng dụng ## Tóm tắt Sự kiện (Event) trong Solidity cho phép các hợp đồng thông minh (smart contracts) gh...
Meta Keywords: kiện, trong, dụng, các, được
-->

# Sự kiện (Event) trong Solidity: Tìm hiểu và Ứng dụng

## Tóm tắt
Sự kiện (Event) trong Solidity cho phép các hợp đồng thông minh (smart contracts) ghi lại và phát đi thông tin quan trọng, giúp các ứng dụng bên ngoài có thể lắng nghe và xử lý các thay đổi trạng thái trong hợp đồng.

## Tài liệu
### Mục đích
Sự kiện trong Solidity được sử dụng để ghi lại các hoạt động quan trọng của hợp đồng thông minh. Khi một sự kiện được kích hoạt, nó sẽ ghi lại thông tin vào blockchain, cho phép người dùng hoặc ứng dụng bên ngoài có thể theo dõi và phản hồi các thay đổi trạng thái.

### Cú pháp
Sự kiện được khai báo với từ khóa `event`, theo sau là tên sự kiện và các tham số cần thiết. Sau đó, sự kiện có thể được kích hoạt bằng cách sử dụng từ khóa `emit`.

```solidity
event EventName(Type1 param1, Type2 param2);
```

### Sử dụng
Để sử dụng sự kiện, trước tiên bạn cần khai báo sự kiện trong hợp đồng, sau đó phát đi sự kiện tại các điểm quan trọng trong mã nguồn hợp đồng.

### Ví dụ
Dưới đây là một ví dụ đơn giản về cách khai báo và sử dụng sự kiện trong Solidity:

```solidity
pragma solidity ^0.8.0;

contract SimpleStorage {
    uint256 public storedData;

    event DataStored(uint256 data);

    function set(uint256 x) public {
        storedData = x;
        emit DataStored(x);  // Phát đi sự kiện khi dữ liệu được lưu
    }
}
```

Trong ví dụ trên, sự kiện `DataStored` được phát đi mỗi khi hàm `set` được gọi, cho phép theo dõi sự thay đổi của `storedData`.

## Giải thích
### Những vấn đề thường gặp
1. **Sự kiện không được ghi lại**: Đảm bảo rằng bạn đã gọi từ khóa `emit` để phát đi sự kiện. Nếu không, sự kiện sẽ không được ghi lại trong blockchain.
2. **Quá nhiều tham số**: Mặc dù có thể thêm nhiều tham số vào sự kiện, nhưng việc này có thể làm tăng chi phí gas. Nên hạn chế số lượng tham số cần thiết.
3. **Khó khăn trong việc lọc sự kiện**: Khi sử dụng các ứng dụng bên ngoài để theo dõi sự kiện, cần phải sử dụng đúng các tham số để lọc sự kiện một cách chính xác.

### Ghi chú thêm
- Các sự kiện không thể được truy cập từ bên trong hợp đồng mà chỉ có thể được ghi lại và lắng nghe bên ngoài.
- Việc sử dụng sự kiện giúp tiết kiệm chi phí gas so với việc lưu trữ dữ liệu trực tiếp trên blockchain.

## Tóm tắt một dòng
Sự kiện trong Solidity cung cấp một cơ chế để ghi lại và phát đi thông tin quan trọng, giúp các ứng dụng bên ngoài theo dõi các thay đổi trạng thái trong hợp đồng thông minh.