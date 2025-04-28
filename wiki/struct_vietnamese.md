<!--
Meta Description: # Struct trong Solidity: Định nghĩa, Cách sử dụng và Ví dụ ## Tóm tắt Struct trong Solidity là một kiểu dữ liệu tùy chỉnh cho phép người dùng nhóm nhi...
Meta Keywords: struct, trong, các, solidity, dụng
-->

# Struct trong Solidity: Định nghĩa, Cách sử dụng và Ví dụ

## Tóm tắt
Struct trong Solidity là một kiểu dữ liệu tùy chỉnh cho phép người dùng nhóm nhiều biến khác nhau thành một thực thể duy nhất, giúp tổ chức và quản lý dữ liệu hiệu quả trong các hợp đồng thông minh.

## Tài liệu
### Mục đích
Struct được sử dụng để định nghĩa các kiểu dữ liệu phức tạp trong Solidity, cho phép lập trình viên tạo ra các đối tượng với nhiều thuộc tính khác nhau. Điều này giúp dễ dàng quản lý dữ liệu trong các ứng dụng phi tập trung (dApps).

### Cách sử dụng
Để định nghĩa một struct trong Solidity, bạn cần sử dụng từ khóa `struct`, theo sau là tên struct và các thuộc tính của nó. Sau khi định nghĩa, bạn có thể tạo các biến thuộc kiểu struct này và sử dụng chúng trong các hàm khác nhau.

```solidity
pragma solidity ^0.8.0;

contract MyContract {
    struct Person {
        string name;
        uint age;
    }

    Person public person;

    function setPerson(string memory _name, uint _age) public {
        person = Person(_name, _age);
    }

    function getPerson() public view returns (string memory, uint) {
        return (person.name, person.age);
    }
}
```

### Chi tiết
- **Định nghĩa**: Struct được định nghĩa với từ khóa `struct`, theo sau là tên của struct và danh sách các thuộc tính với kiểu dữ liệu tương ứng.
- **Khởi tạo**: Có thể khởi tạo một biến struct bằng cách gọi tên struct như một hàm và truyền các tham số tương ứng.
- **Truy cập**: Các thuộc tính của struct có thể được truy cập thông qua phép toán dấu chấm (dot notation).

## Ví dụ
Dưới đây là một ví dụ mở rộng về việc sử dụng struct trong Solidity:

```solidity
pragma solidity ^0.8.0;

contract School {
    struct Student {
        string name;
        uint grade;
        bool isGraduated;
    }

    mapping(uint => Student) public students;

    function addStudent(uint _id, string memory _name, uint _grade, bool _isGraduated) public {
        students[_id] = Student(_name, _grade, _isGraduated);
    }

    function getStudent(uint _id) public view returns (string memory, uint, bool) {
        Student memory student = students[_id];
        return (student.name, student.grade, student.isGraduated);
    }
}
```

## Giải thích
- **Lỗi phổ biến**: Một lỗi thường gặp khi sử dụng struct là không khởi tạo đúng các thuộc tính, dẫn đến việc truy cập vào các biến chưa được gán giá trị. 
- **Vấn đề về bộ nhớ**: Struct trong Solidity có thể được lưu trữ trong bộ nhớ (memory) hoặc trong trạng thái (storage). Cần chú ý đến điều này khi thiết kế hợp đồng.
- **Chi phí gas**: Việc sử dụng struct có thể ảnh hưởng đến chi phí gas, đặc biệt khi cấu trúc quá phức tạp hoặc chứa nhiều thuộc tính.

## Tóm tắt một dòng
Struct trong Solidity là một công cụ mạnh mẽ cho phép tạo ra các kiểu dữ liệu phức tạp để quản lý thông tin trong hợp đồng thông minh.