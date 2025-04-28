<!--
Meta Description: # Solidity의 매핑(Mapping) 이해하기: 스마트 계약에서 데이터 저장의 핵심 ## 개요 Solidity에서 매핑(mapping)은 키-값 쌍을 저장하는 데이터 구조로, 효율적인 데이터 접근을 가능하게 합니다. 이는 스마트 계약의 상태를 관리하고 다양한 데이...
Meta Keywords: 데이터, 매핑은, mapping, public, 스마트
-->

# Solidity의 매핑(Mapping) 이해하기: 스마트 계약에서 데이터 저장의 핵심

## 개요
Solidity에서 매핑(mapping)은 키-값 쌍을 저장하는 데이터 구조로, 효율적인 데이터 접근을 가능하게 합니다. 이는 스마트 계약의 상태를 관리하고 다양한 데이터 타입을 연결하는 데 필수적인 기능입니다.

## 문서화
매핑(mapping)은 Solidity에서 가장 중요한 데이터 구조 중 하나로, 다음과 같은 목적을 가지고 사용됩니다:

- **목적**: 매핑은 특정 키에 대해 값을 저장하고 조회하는 데 사용됩니다. 이는 해시 테이블과 유사한 방식으로 작동하여, 특정 키를 통해 직접적으로 값을 검색할 수 있게 해줍니다.
  
- **사용법**: 매핑은 다음과 같은 형식으로 선언됩니다:
  ```solidity
  mapping(KeyType => ValueType) public myMapping;
  ```
  여기서 `KeyType`은 키의 데이터 타입, `ValueType`은 저장할 값의 데이터 타입을 나타냅니다. 매핑은 기본적으로 비어 있는 상태로 시작되며, 키가 추가될 때마다 자동으로 값이 초기화됩니다.

- **상세 설명**:
  1. 매핑은 상태 변수로 선언되어 계약의 상태를 영구적으로 저장합니다.
  2. 매핑의 키는 유일해야 하며, 동일한 키에 대해 여러 값을 저장할 수 없습니다.
  3. 매핑은 순회(iteration)를 지원하지 않기 때문에, 키의 목록을 직접적으로 얻을 수는 없습니다.

## 예제
다음은 Solidity에서 매핑을 사용하는 간단한 예제입니다:

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
이 예제에서는 사용자 주소를 키로 사용하여 해당 사용자의 잔액을 저장하는 매핑을 생성하고 있습니다.

## 설명
매핑을 사용할 때 주의해야 할 점은 다음과 같습니다:
- **기본값**: 매핑은 초기화되지 않은 키에 대해 기본값을 반환합니다. 예를 들어, uint형 매핑의 경우, 값이 설정되지 않은 키에 대해 0을 반환합니다.
- **키의 타입 제한**: 매핑의 키로는 `uint`, `address`, `bytes32`와 같은 기본 데이터 타입만 사용할 수 있으며, 배열이나 구조체와 같은 복잡한 데이터 타입은 지원되지 않습니다.
- **가시성**: 매핑은 기본적으로 외부에서 직접 접근할 수 없으며, public으로 선언할 경우에만 자동으로 getter 함수가 생성됩니다.

## 한 줄 요약
Solidity의 매핑(mapping)은 키-값 쌍을 저장하는 데이터 구조로, 스마트 계약에서 효율적인 데이터 관리와 접근을 가능하게 합니다.