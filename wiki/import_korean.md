<!--
Meta Description: # Solidity에서의 import 명령어: 코드 재사용의 핵심 ## 개요 Solidity에서 `import`는 다른 파일에 정의된 계약, 라이브러리, 인터페이스 등을 가져오는 데 사용되는 명령어로, 코드의 재사용성과 유지보수성을 높이는 데 중요한 역할을 합니다. #...
Meta Keywords: import, solidity, sol, uint, 코드의
-->

# Solidity에서의 import 명령어: 코드 재사용의 핵심

## 개요
Solidity에서 `import`는 다른 파일에 정의된 계약, 라이브러리, 인터페이스 등을 가져오는 데 사용되는 명령어로, 코드의 재사용성과 유지보수성을 높이는 데 중요한 역할을 합니다.

## 문서화

### 목적
`import` 명령어는 Solidity 코드의 구조를 개선하고, 여러 파일로 나누어 관리할 수 있게 해줍니다. 이를 통해 프로젝트의 모듈성을 높이고, 코드의 중복을 줄이며, 팀원 간의 협업을 쉽게 합니다.

### 사용법
`import` 구문은 다음과 같은 형식으로 사용됩니다:

```solidity
import "파일경로";
```

파일 경로는 상대 경로 또는 절대 경로로 지정할 수 있으며, 주로 `.sol` 파일을 가져옵니다.

### 세부 사항
- Solidity는 여러 파일에서 동일한 계약이나 라이브러리를 참조할 수 있도록 하여 코드의 재사용성을 높입니다.
- `import`는 중첩하여 사용할 수 있으며, 다른 계약에서 가져온 계약을 기반으로 새로운 계약을 작성할 수 있습니다.
- Solidity는 기본적으로 `import`된 파일에서 모든 선언을 사용할 수 있으며, 필요에 따라 특정 계약이나 요소만 선택적으로 가져올 수도 있습니다.

## 예제

### 기본 사용 예제

1. 다른 계약 가져오기:

```solidity
// File: MyContract.sol
pragma solidity ^0.8.0;

import "./AnotherContract.sol";

contract MyContract is AnotherContract {
    // ...
}
```

2. 라이브러리 가져오기:

```solidity
// File: MyLibrary.sol
pragma solidity ^0.8.0;

library MyLibrary {
    function add(uint a, uint b) internal pure returns (uint) {
        return a + b;
    }
}

// File: MyContract.sol
pragma solidity ^0.8.0;

import "./MyLibrary.sol";

contract MyContract {
    function useAdd(uint a, uint b) public pure returns (uint) {
        return MyLibrary.add(a, b);
    }
}
```

## 설명

### 일반적인 함정 및 주의사항
- 파일 경로를 잘못 지정할 경우 컴파일 오류가 발생합니다. 경로는 대소문자를 구분하므로 정확히 입력해야 합니다.
- 상대 경로를 사용할 때는 현재 파일의 위치를 기준으로 경로를 설정해야 하며, 절대 경로를 사용하는 경우는 주의가 필요합니다.
- 동일한 계약을 여러 번 가져오는 경우, 중복 정의로 인해 오류가 발생할 수 있습니다. 이를 피하기 위해 각 파일에서 계약을 한 번만 정의해야 합니다.

## 한 줄 요약
Solidity의 `import` 명령어는 다른 파일의 계약, 라이브러리 및 인터페이스를 가져와 코드의 재사용성과 구조적 관리를 가능하게 합니다.