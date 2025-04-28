<!--
Meta Description: # Solidity의 enum: 열거형 데이터 타입에 대한 완벽 가이드 ## 개요 Solidity에서의 `enum`은 개발자가 정의한 데이터 타입으로, 특정 값을 명확하게 구분하기 위해 사용됩니다. 이 데이터 타입은 가독성을 높이고 코드의 의미를 분명히 하여, 스마트 ...
Meta Keywords: enum, light, state, currentlight, 있습니다
-->

# Solidity의 enum: 열거형 데이터 타입에 대한 완벽 가이드

## 개요
Solidity에서의 `enum`은 개발자가 정의한 데이터 타입으로, 특정 값을 명확하게 구분하기 위해 사용됩니다. 이 데이터 타입은 가독성을 높이고 코드의 의미를 분명히 하여, 스마트 계약의 유지보수를 용이하게 합니다.

## 문서
### 목적
`enum`은 특정 값의 집합을 정의하여 코드에서 상수 값을 잘 관리할 수 있도록 합니다. 이를 통해 가독성이 향상되고, 개발자가 실수로 잘못된 값을 사용하는 것을 방지할 수 있습니다.

### 사용법
`enum`은 다음과 같은 형식으로 선언됩니다:

```solidity
enum EnumName { Value1, Value2, Value3 }
```

여기서 `EnumName`은 열거형의 이름이며, `Value1`, `Value2`, `Value3`은 해당 열거형의 가능한 값들입니다. 각 값은 0부터 시작하는 정수로 자동으로 매핑됩니다.

#### 예제
1. 기본적인 enum 사용 예:
```solidity
pragma solidity ^0.8.0;

contract Example {
    enum State { Active, Inactive, Pending }
    State public state;

    constructor() {
        state = State.Active; // 기본값 설정
    }

    function setState(State _state) public {
        state = _state; // 상태 변경
    }
}
```

2. enum을 사용한 조건문:
```solidity
pragma solidity ^0.8.0;

contract TrafficLight {
    enum Light { Red, Yellow, Green }
    Light public currentLight;

    constructor() {
        currentLight = Light.Red; // 처음에는 Red로 설정
    }

    function changeLight() public {
        if (currentLight == Light.Red) {
            currentLight = Light.Green;
        } else if (currentLight == Light.Green) {
            currentLight = Light.Yellow;
        } else {
            currentLight = Light.Red;
        }
    }
}
```

## 설명
- **값의 자동 매핑**: `enum`의 각 값은 0부터 시작하는 자동 증가 정수로 매핑되며, 이러한 매핑을 통해 각 값을 쉽게 비교할 수 있습니다.
- **가독성**: `enum`을 사용하면 특정 상태나 옵션을 명확하게 지정할 수 있어 코드의 가독성이 높아집니다.
- **상태 관리**: 스마트 계약에서 상태를 관리하는 데 유용하며, 상태 변경을 쉽게 추적할 수 있습니다.

### 일반적인 함정
- **적절한 초기화**: 열거형 변수를 선언할 때 초기값을 설정하지 않으면 기본값(첫 번째 값)이 자동으로 설정됩니다. 이는 의도하지 않은 동작을 초래할 수 있습니다.
- **비교 시 주의**: 열거형 값과 정수 값을 비교할 때, 항상 열거형 값을 사용해야 하며, 정수로 직접 비교하는 것은 위험할 수 있습니다.

## 한 줄 요약
Solidity의 `enum`은 특정 값의 집합을 정의하여 코드의 가독성과 유지보수를 향상시키는 강력한 데이터 타입입니다.