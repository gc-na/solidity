<!--
Meta Description: # Solidity에서의 Immutable 변수 이해하기 ## 개요 Solidity에서 `immutable` 키워드는 스마트 계약에서 변수의 값을 한 번 설정한 후 변경할 수 없도록 만드는 특징을 가지고 있습니다. 이는 주로 상태 변수를 초기화할 때 유용하며, 가스 비...
Meta Keywords: immutable, 변수를, 변수는, 변경할, uint256
-->

# Solidity에서의 Immutable 변수 이해하기

## 개요
Solidity에서 `immutable` 키워드는 스마트 계약에서 변수의 값을 한 번 설정한 후 변경할 수 없도록 만드는 특징을 가지고 있습니다. 이는 주로 상태 변수를 초기화할 때 유용하며, 가스 비용을 줄이고, 보안성을 높이는 데 기여합니다.

## 문서화
`immutable` 변수는 계약의 배포 시점에 값을 설정할 수 있는 상태 변수를 정의하는 데 사용됩니다. 이 변수는 계약이 배포된 후에는 변경할 수 없으며, 이는 변수를 초기화하는 데 필요한 가스 비용을 절감하고, 계약의 불변성을 보장합니다.

### 용도
- **가스 비용 절감**: `immutable` 변수를 사용하면, 해당 변수를 읽을 때의 가스 비용이 줄어듭니다. 이는 보통 상태 변수를 읽는 데 필요한 가스보다 적게 소모됩니다.
- **보안성 강화**: 한 번 설정된 값은 변경할 수 없으므로, 외부 공격으로부터 변수가 변경되는 것을 방지할 수 있습니다.

### 사용법
`immutable` 변수는 다음과 같이 선언됩니다:

```solidity
contract MyContract {
    uint256 public immutable myImmutableVar;

    constructor(uint256 _value) {
        myImmutableVar = _value;
    }
}
```

위의 예제에서 `myImmutableVar`는 계약 생성자에서 한 번만 값이 할당되며, 이후에는 절대 변경될 수 없습니다.

## 예제
다음은 `immutable` 변수를 사용하는 간단한 예제입니다:

```solidity
pragma solidity ^0.8.0;

contract Example {
    uint256 public immutable creationTime;

    constructor() {
        creationTime = block.timestamp; // 계약 생성 시 시간 저장
    }

    function getElapsedTime() public view returns (uint256) {
        return block.timestamp - creationTime; // 생성 이후의 시간 계산
    }
}
```

이 계약은 생성 시점의 타임스탬프를 저장하고, 이후 `getElapsedTime` 함수를 통해 경과 시간을 반환합니다.

## 설명
`immutable` 변수를 사용할 때 유의해야 할 점은 다음과 같습니다:

- **초기화 제한**: `immutable` 변수는 계약의 생성자에서만 초기화할 수 있으며, 그 이후에는 변경할 수 없습니다. 따라서 초기값을 설정할 때 신중하게 선택해야 합니다.
- **가시성**: `immutable` 변수가 `public`으로 선언되면, 해당 변수의 값은 자동으로 getter 함수를 생성하여 외부에서 접근할 수 있게 됩니다.
- **가스 최적화**: `immutable` 변수는 상태 변수가 아니라 상수로 취급되므로, 변수의 값이 변경되지 않는다는 점에서 가스 비용이 절감됩니다.

## 한 줄 요약
`immutable` 변수는 스마트 계약에서 초기화 후 변경할 수 없는 상태 변수를 정의하여 가스 비용을 절감하고 보안성을 높이는 데 도움을 줍니다.