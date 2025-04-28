<!--
Meta Description: # Solidity에서의 메모리 (Memory) 이해하기 ## 개요 Solidity에서 "메모리"는 데이터 저장소의 한 종류로, 계약이 실행되는 동안 임시 데이터 구조를 저장하는 데 사용됩니다. 메모리는 상대적으로 빠른 접근 속도를 가지며, 계약의 상태를 유지하지 않고...
Meta Keywords: memory, 데이터, uint, numbers, solidity에서
-->

# Solidity에서의 메모리 (Memory) 이해하기

## 개요
Solidity에서 "메모리"는 데이터 저장소의 한 종류로, 계약이 실행되는 동안 임시 데이터 구조를 저장하는 데 사용됩니다. 메모리는 상대적으로 빠른 접근 속도를 가지며, 계약의 상태를 유지하지 않고 함수 호출 간에만 존재합니다.

## 문서화

### 목적
메모리는 Solidity에서 동적으로 할당된 데이터 구조를 저장할 수 있는 공간입니다. 이는 특히 배열, 구조체와 같은 복잡한 데이터 타입을 처리할 때 유용합니다.

### 사용법
Solidity에서 메모리에 변수를 선언할 때는 `memory` 키워드를 사용합니다. 메모리는 함수 호출이 끝나면 자동으로 삭제되며, 데이터의 지속성이 필요 없는 경우에 적합합니다.

```solidity
pragma solidity ^0.8.0;

contract MemoryExample {
    function useMemory() public pure returns (uint[] memory) {
        uint[] memory numbers = new uint[](3);
        numbers[0] = 1;
        numbers[1] = 2;
        numbers[2] = 3;
        return numbers;
    }
}
```

## 예제
다음은 Solidity에서 메모리를 사용하는 간단한 예제입니다.

```solidity
pragma solidity ^0.8.0;

contract MemoryExample {
    function createArray() public pure returns (uint[] memory) {
        uint[] memory array = new uint[](5);
        for (uint i = 0; i < 5; i++) {
            array[i] = i + 1;
        }
        return array;
    }
}
```

이 예제에서는 `createArray` 함수가 메모리에 5개의 정수를 가진 배열을 생성하고 반환합니다.

## 설명
메모리를 사용할 때 주의해야 할 점은 다음과 같습니다.

- **영구적이지 않음**: 메모리에 저장된 데이터는 함수 호출이 끝나면 사라지므로, 상태 변수를 사용해야 하는 경우에는 `storage`를 사용해야 합니다.
- **가스 비용**: 메모리에 데이터를 할당할 때는 가스가 소모되며, 배열의 크기에 따라 비용이 달라질 수 있습니다.
- **복잡한 데이터 타입**: 구조체와 같은 복잡한 데이터 타입을 메모리에서 사용하려면, 해당 타입이 `memory`로 선언되어야 합니다.

## 한 줄 요약
Solidity의 메모리는 임시 데이터 저장소로, 함수 호출 중에만 존재하며 `memory` 키워드를 통해 사용됩니다.