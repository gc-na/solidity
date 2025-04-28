<!--
Meta Description: # Solidity에서의 추상 클래스(abstract) 이해하기 ## 개요 Solidity의 "추상 클래스(abstract)"는 계약의 기본 구조를 정의하되, 이를 직접 인스턴스화할 수 없도록 하는 기능입니다. 주로 상속을 통해 다른 계약에서 구현되며, 재사용성과 코드...
Meta Keywords: 계약에서, 계약은, 메서드를, abstract, 클래스는
-->

# Solidity에서의 추상 클래스(abstract) 이해하기

## 개요
Solidity의 "추상 클래스(abstract)"는 계약의 기본 구조를 정의하되, 이를 직접 인스턴스화할 수 없도록 하는 기능입니다. 주로 상속을 통해 다른 계약에서 구현되며, 재사용성과 코드의 명확성을 높이는 데 기여합니다.

## 문서화
추상 클래스는 Solidity에서 최상위 계약을 정의하는 데 사용됩니다. 이러한 계약은 하나 이상의 추상 메서드를 포함할 수 있으며, 이 메서드는 하위 계약에서 반드시 구현해야 합니다. 추상 클래스는 다음과 같은 목적과 사용법을 가집니다:

### 목적
- 코드 재사용성: 공통된 기능이나 속성을 정의하여 여러 계약에서 재사용할 수 있습니다.
- 구조적 명확성: 특정 메서드의 구현을 강제하여 계약의 일관성을 유지합니다.

### 사용법
추상 클래스는 `abstract` 키워드를 사용하여 선언합니다. 이전에 명시된 추상 메서드는 하위 계약에서 반드시 구현되어야 합니다. 다음은 추상 클래스의 기본 사용법을 보여줍니다.

## 예제
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

abstract contract Animal {
    // 추상 메서드
    function makeSound() public view virtual returns (string memory);
}

contract Dog is Animal {
    // 추상 메서드 구현
    function makeSound() public view override returns (string memory) {
        return "Woof!";
    }
}

contract Cat is Animal {
    // 추상 메서드 구현
    function makeSound() public view override returns (string memory) {
        return "Meow!";
    }
}
```

위의 예제에서 `Animal` 계약은 추상 계약으로, `makeSound` 메서드를 정의합니다. `Dog`와 `Cat` 계약은 이 메서드를 각각 구현합니다.

## 설명
추상 클래스 사용 시 몇 가지 주의해야 할 점이 있습니다:

- **추상 메서드 구현 필수**: 하위 계약에서 모든 추상 메서드를 반드시 구현해야 합니다. 그렇지 않으면 해당 계약은 컴파일되지 않습니다.
- **인스턴스화 불가**: 추상 계약은 직접 인스턴스화할 수 없습니다. 반드시 하위 계약을 통해 인스턴스를 생성해야 합니다.
- **가독성**: 추상 계약을 사용하여 코드의 가독성을 높일 수 있지만, 지나치게 복잡한 상속 구조는 오히려 혼란을 초래할 수 있습니다.

## 한 줄 요약
Solidity의 추상 클래스는 계약의 기본 구조를 정의하며, 하위 계약에서 필수적으로 구현해야 하는 메서드를 설정하는 데 사용됩니다.