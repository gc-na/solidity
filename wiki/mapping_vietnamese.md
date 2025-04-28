<!--
Meta Description: # Mapping trong Solidity: Tìm Hiểu và Ứng Dụng ## Tóm Tắt Mapping là một cấu trúc dữ liệu quan trọng trong Solidity, cho phép người dùng lưu trữ và tr...
Meta Keywords: liệu, một, mapping, trong, thể
-->

# Mapping trong Solidity: Tìm Hiểu và Ứng Dụng

## Tóm Tắt
Mapping là một cấu trúc dữ liệu quan trọng trong Solidity, cho phép người dùng lưu trữ và truy xuất dữ liệu dưới dạng cặp key-value. Điều này giúp tối ưu hóa việc quản lý dữ liệu trong các hợp đồng thông minh.

## Tài Liệu
### Mục Đích
Mapping trong Solidity được sử dụng để lưu trữ các giá trị mà có thể truy cập thông qua một khóa duy nhất. Nó tương tự như một bảng băm (hash table) trong các ngôn ngữ lập trình khác.

### Cách Sử Dụng
Cú pháp khai báo một mapping như sau:
```solidity
mapping (type_key => type_value) name_mapping;
```
- `type_key`: kiểu dữ liệu của khóa (có thể là bất kỳ kiểu dữ liệu nào như `uint`, `address`, `bytes32`, v.v.).
- `type_value`: kiểu dữ liệu của giá trị (có thể là bất kỳ kiểu dữ liệu nào, bao gồm cả mapping khác hoặc struct).
- `name_mapping`: tên của mapping.

### Chi Tiết
- Mappings không có độ dài cố định; chúng có thể chứa bất kỳ số lượng phần tử nào.
- Khi bạn truy cập một khóa không tồn tại, nó sẽ trả về giá trị mặc định của kiểu dữ liệu đó (ví dụ: 0 cho `uint`, địa chỉ 0 cho `address`).
- Mappings không thể được lặp qua trực tiếp, vì vậy bạn cần một cấu trúc dữ liệu bổ sung (như array) để theo dõi các khóa.

## Ví Dụ
### Ví Dụ Cơ Bản
```solidity
pragma solidity ^0.8.0;

contract Example {
    mapping(address => uint) public balances;

    function deposit() public payable {
        balances[msg.sender] += msg.value;
    }

    function getBalance(address user) public view returns (uint) {
        return balances[user];
    }
}
```
Trong ví dụ trên, chúng ta khai báo một mapping `balances` để theo dõi số dư của mỗi địa chỉ. Hàm `deposit` cho phép người dùng gửi Ether, và hàm `getBalance` cho phép kiểm tra số dư của một địa chỉ.

## Giải Thích
### Những Điểm Cần Lưu Ý
- Không thể xóa một phần tử trong mapping; bạn chỉ có thể gán lại giá trị cho nó.
- Vì mappings không có độ dài cố định và không thể lặp qua, bạn nên lưu trữ các khóa trong một array nếu cần truy cập chúng sau này.
- Việc sử dụng mappings với các kiểu dữ liệu phức tạp như struct có thể làm cho mã trở nên khó hiểu, vì vậy hãy đảm bảo rằng bạn có chiến lược rõ ràng về cách tổ chức dữ liệu.

## Tóm Tắt Một Dòng
Mapping là một cấu trúc dữ liệu trong Solidity cho phép lưu trữ và truy xuất dữ liệu dưới dạng cặp key-value, giúp quản lý dữ liệu hiệu quả trong hợp đồng thông minh.