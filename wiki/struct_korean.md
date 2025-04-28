<!--
Meta Description: # Solidity의 Struct: 사용자 정의 데이터 구조의 이해와 활용 ## 개요 Solidity에서의 `struct`는 복합 데이터 타입을 정의하기 위한 기능으로, 여러 관련 데이터 항목을 하나의 단위로 묶어 사용자 정의 데이터 구조를 생성할 수 있게 해줍니다. ...
Meta Keywords: struct, 데이터, string, 있습니다, book
-->

# Solidity의 Struct: 사용자 정의 데이터 구조의 이해와 활용

## 개요
Solidity에서의 `struct`는 복합 데이터 타입을 정의하기 위한 기능으로, 여러 관련 데이터 항목을 하나의 단위로 묶어 사용자 정의 데이터 구조를 생성할 수 있게 해줍니다. 이는 스마트 계약 내에서 더 복잡한 데이터를 효율적으로 관리할 수 있게 도와줍니다.

## 문서화
`struct`는 Solidity에서 데이터 구조를 정의하는 데 매우 유용한 도구입니다. 개발자는 `struct`를 사용하여 여러 개의 변수(예: 문자열, 정수 등)를 하나의 단위로 묶어 사용할 수 있습니다. 이를 통해 코드의 가독성이 향상되고, 다양한 데이터를 하나의 객체처럼 관리할 수 있습니다.

### 목적
`struct`의 주 목적은 복잡한 데이터 유형을 정의하고 이를 쉽게 다룰 수 있도록 하는 것입니다. 특히, 스마트 계약의 상태를 관리하거나, 다양한 속성을 가진 객체를 생성할 때 유용합니다.

### 사용법
`struct`를 정의하는 기본 문법은 다음과 같습니다:

```solidity
struct 구조체명 {
    데이터타입 변수명1;
    데이터타입 변수명2;
    // 추가 변수들...
}
```

그 후, `struct`를 사용하여 변수를 선언할 수 있습니다:

```solidity
struct Person {
    string name;
    uint age;
}

// 사용 예
Person public person1;
```

## 예제
다음은 `struct`를 사용하는 간단한 예제입니다:

```solidity
pragma solidity ^0.8.0;

contract Example {
    struct Book {
        string title;
        string author;
        uint256 yearPublished;
    }
    
    Book public myBook;

    function setBook(string memory _title, string memory _author, uint256 _yearPublished) public {
        myBook = Book(_title, _author, _yearPublished);
    }

    function getBook() public view returns (string memory, string memory, uint256) {
        return (myBook.title, myBook.author, myBook.yearPublished);
    }
}
```

이 예제에서는 `Book`이라는 구조체를 정의하고, 책의 제목, 저자, 출판 연도를 저장할 수 있는 기능을 제공합니다.

## 설명
`struct` 사용 시 주의해야 할 점은 다음과 같습니다:

1. **메모리와 저장소**: `struct`를 사용할 때는 메모리와 저장소 키워드를 잘 이해해야 합니다. 기본적으로 `struct`는 저장소에 저장되지만, 함수 내부에서 `memory` 키워드를 사용하여 임시 저장소로 사용할 수 있습니다.
   
2. **배열 및 맵과의 결합**: `struct`는 배열 또는 맵과 결합하여 사용할 수 있습니다. 예를 들어, `Book` 구조체의 배열을 만들어 여러 권의 책을 저장할 수 있습니다.

3. **가독성**: `struct`는 여러 변수를 하나로 묶어 코드의 가독성을 높여줍니다. 그러나 너무 많은 변수를 포함하는 경우에는 오히려 복잡성을 증가시킬 수 있으니 적절한 설계가 필요합니다.

4. **초기화**: `struct`를 초기화하지 않으면 모든 필드는 기본값으로 설정됩니다. 예를 들어, `string`은 빈 문자열, `uint`는 0입니다.

## 한 줄 요약
Solidity에서 `struct`는 여러 데이터 항목을 하나의 단위로 묶어 사용자 정의 데이터 구조를 생성하고 관리할 수 있는 강력한 도구입니다.