<!--
Meta Description: # Solidity에서의 "new": 스마트 계약 객체 생성 ## 개요 Solidity에서 "new" 키워드는 스마트 계약의 인스턴스를 생성하는 데 사용됩니다. 이 키워드는 새로운 계약을 배포하고 그 계약의 주소를 반환하는 데 중요한 역할을 합니다. ## 문서화 "ne...
Meta Keywords: new, 계약의, 인스턴스를, 키워드는, 합니다
-->

# Solidity에서의 "new": 스마트 계약 객체 생성

## 개요
Solidity에서 "new" 키워드는 스마트 계약의 인스턴스를 생성하는 데 사용됩니다. 이 키워드는 새로운 계약을 배포하고 그 계약의 주소를 반환하는 데 중요한 역할을 합니다.

## 문서화
"new"는 Solidity에서 중요한 기능으로, 기존 계약의 인스턴스를 생성하여 사용할 수 있게 해줍니다. 이 명령어는 다음과 같은 목적과 사용 방법을 가지고 있습니다.

### 목적
- 스마트 계약의 새로운 인스턴스를 생성하여 배포합니다.
- 생성된 계약의 주소를 반환하여 다른 계약 또는 외부에서 접근할 수 있게 합니다.

### 사용법
"new" 키워드는 다음과 같은 형식으로 사용됩니다:

```solidity
ContractName instanceName = new ContractName(arguments);
```

여기서 `ContractName`은 생성할 계약의 이름이며, `instanceName`은 생성된 계약의 인스턴스를 참조하는 변수입니다. `arguments`는 생성자에 전달할 매개변수입니다.

### 세부사항
- "new" 키워드는 계약을 배포할 때 가스 비용이 발생합니다.
- 생성된 계약은 고유한 주소를 가지며, 이 주소는 블록체인에 영구적으로 저장됩니다.

## 예제
다음은 "new" 키워드를 사용하여 간단한 계약을 생성하는 예제입니다.

```solidity
pragma solidity ^0.8.0;

contract SimpleStorage {
    uint256 public storedData;

    constructor(uint256 initialValue) {
        storedData = initialValue;
    }
}

contract Factory {
    SimpleStorage public simpleStorageInstance;

    function createSimpleStorage(uint256 initialValue) public {
        simpleStorageInstance = new SimpleStorage(initialValue);
    }
}
```

위 코드에서 `Factory` 계약은 `SimpleStorage` 계약의 인스턴스를 생성합니다.

## 설명
"new" 키워드를 사용할 때 주의해야 할 몇 가지 사항이 있습니다:

- **가스 비용**: 계약을 생성할 때 발생하는 가스 비용을 고려해야 합니다. 가스가 부족하면 계약이 생성되지 않습니다.
- **생성자 매개변수**: 생성자에 필요한 매개변수를 정확히 전달해야 합니다. 잘못된 매개변수를 전달하면 계약 생성이 실패합니다.
- **계약 주소**: 생성된 계약의 주소는 고유하므로, 이를 저장하거나 다른 계약에서 참조할 수 있도록 관리해야 합니다.

## 한 줄 요약
"new" 키워드는 Solidity에서 새로운 스마트 계약 인스턴스를 생성하고 배포하는 데 사용됩니다.