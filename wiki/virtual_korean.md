<!--
Meta Description: # Solidity에서 'virtual' 키워드 이해하기: 상속 및 함수 오버라이딩 ## 개요 Solidity에서 'virtual' 키워드는 스마트 계약의 함수가 상속될 때 오버라이딩될 수 있음을 나타내는 중요한 키워드입니다. 이 키워드는 특히 계약의 계층 구조에서 다...
Meta Keywords: virtual, 계약에서, 키워드는, 계약의, solidity에서
-->

# Solidity에서 'virtual' 키워드 이해하기: 상속 및 함수 오버라이딩

## 개요
Solidity에서 'virtual' 키워드는 스마트 계약의 함수가 상속될 때 오버라이딩될 수 있음을 나타내는 중요한 키워드입니다. 이 키워드는 특히 계약의 계층 구조에서 다형성을 활용할 수 있게 해 주며, 더 유연한 코드 작성이 가능합니다.

## 문서화
### 목적
'virtual' 키워드는 Solidity에서 상속받은 계약이 특정 함수의 기능을 변경하거나 확장할 수 있도록 허용합니다. 기본 계약에서 정의된 함수가 'virtual'로 선언되면, 파생 계약에서 해당 함수를 재정의(override)하여 새로운 동작을 추가할 수 있습니다.

### 사용법
'virtual' 키워드는 함수 정의 시 사용되며, 다음과 같은 형식으로 작성됩니다:

```solidity
function functionName() public virtual {
    // 함수 본문
}
```

### 세부사항
- **상속 구조**: 'virtual' 키워드를 사용하면 계약 간의 관계를 설정할 수 있습니다. 기본 계약이 자식 계약에 의해 확장될 수 있게 됩니다.
- **오버라이딩**: 자식 계약은 'override' 키워드를 사용하여 부모 계약에서 정의된 'virtual' 함수를 재정의할 수 있습니다.
- **다형성 지원**: 이를 통해 개발자는 다양한 계약에서 같은 함수 이름을 사용하더라도 각기 다른 구현을 제공할 수 있습니다.

## 예시
다음은 'virtual' 키워드를 사용하는 간단한 예시입니다.

```solidity
pragma solidity ^0.8.0;

contract Base {
    function greet() public virtual returns (string memory) {
        return "Hello from Base!";
    }
}

contract Derived is Base {
    function greet() public override returns (string memory) {
        return "Hello from Derived!";
    }
}
```

위 코드에서 `Base` 계약의 `greet` 함수는 'virtual'로 선언되어 있으며, `Derived` 계약에서 오버라이딩 되어 사용됩니다.

## 설명
### 일반적인 실수 및 주의사항
- 'virtual'로 선언하지 않은 함수는 재정의할 수 없으며, 이로 인해 기능 확장이 불가능합니다.
- 자식 계약에서 부모 계약의 'virtual' 함수를 오버라이드할 때, 반드시 'override' 키워드를 사용해야 합니다. 이를 잊으면 컴파일 오류가 발생합니다.
- 다중 상속을 사용할 경우, 어떤 부모 계약의 함수를 오버라이드할지 주의해야 하며, 충돌 가능성을 고려해야 합니다.

## 한 줄 요약
Solidity에서 'virtual' 키워드는 함수가 상속될 때 오버라이딩 가능성을 표시하여 다형성을 지원하는 기능입니다.