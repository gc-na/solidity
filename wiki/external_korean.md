<!--
Meta Description: # Solidity의 "external" 키워드: 외부 함수의 활용 ## 개요 Solidity에서 "external" 키워드는 계약의 외부 함수를 정의할 때 사용됩니다. 외부 함수는 계약 외부에서만 호출할 수 있으며, 특정 상황에서 가스 비용을 절감할 수 있는 장점을 ...
Meta Keywords: external, 함수는, 함수를, 호출할, 있습니다
-->

# Solidity의 "external" 키워드: 외부 함수의 활용

## 개요
Solidity에서 "external" 키워드는 계약의 외부 함수를 정의할 때 사용됩니다. 외부 함수는 계약 외부에서만 호출할 수 있으며, 특정 상황에서 가스 비용을 절감할 수 있는 장점을 제공합니다.

## 문서화
"external" 키워드는 함수의 가시성(visibility)을 설정하는 데 사용됩니다. Solidity에서는 다음과 같은 네 가지 가시성 키워드가 있습니다: `public`, `private`, `internal`, `external`. 이 중 `external`은 함수가 계약의 외부에서만 호출될 수 있도록 제한합니다.

### 목적
- **가시성 제한**: 외부에서 호출할 수 있도록 하여 계약 외부의 사용자 또는 다른 계약과의 상호작용을 가능하게 합니다.
- **가스 효율성**: 외부 함수는 호출 시 인자 전송 방식으로 인해 가스 비용이 절감될 수 있습니다.

### 사용법
`external` 키워드를 사용하여 함수를 정의할 때는 다음과 같은 구문을 사용합니다:

```solidity
function functionName(parameters) external returns (returnType) {
    // 함수 구현
}
```

## 예제
```solidity
pragma solidity ^0.8.0;

contract Example {
    uint public data;

    // external 함수 정의
    function setData(uint _data) external {
        data = _data;
    }

    // external 함수를 호출하여 데이터 업데이트하는 다른 계약
    function updateData(address exampleContract, uint newData) public {
        Example(exampleContract).setData(newData);
    }
}
```

위의 예제에서는 `setData` 함수가 `external`로 정의되어 있으며, 이는 계약 외부에서 호출될 수 있습니다.

## 설명
- **호출 방식**: `external` 함수는 계약 외부에서 호출될 때 `this.functionName()` 같은 방식으로 호출할 수 없습니다. 대신 다른 계약 인스턴스를 통해 호출해야 합니다.
- **가스 비용**: `external` 함수는 인자를 직접 전달받기 때문에, `public` 함수보다 더 가스 효율적일 수 있습니다. 이는 인자가 메모리에서 스택으로 이동하는 방식 때문입니다.
- **제한 사항**: 내부 함수나 private 함수는 외부에서 호출할 수 없으므로, 호출 시 가시성을 잘 확인해야 합니다.

## 한 줄 요약
Solidity에서 "external" 키워드는 계약 외부에서만 호출 가능한 함수를 정의하는 데 사용되며, 가스 효율성을 높이는 데 도움을 줍니다.