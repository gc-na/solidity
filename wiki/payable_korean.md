<!--
Meta Description: # Solidity의 "payable": 스마트 계약에서 이더를 수신하는 방법 ## 개요 Solidity에서 "payable"은 이더를 수신할 수 있도록 함수나 주소를 지정하는 키워드입니다. 이 키워드는 스마트 계약이 이더를 전송받고 처리할 수 있게 하며, 효율적이고 ...
Meta Keywords: payable, 이더를, 합니다, msg, sender
-->

# Solidity의 "payable": 스마트 계약에서 이더를 수신하는 방법

## 개요
Solidity에서 "payable"은 이더를 수신할 수 있도록 함수나 주소를 지정하는 키워드입니다. 이 키워드는 스마트 계약이 이더를 전송받고 처리할 수 있게 하며, 효율적이고 안전한 자산 관리가 가능하게 합니다.

## 문서화
### 목적
"payable" 키워드는 주로 이더를 전송받거나 스마트 계약 내에서 금전 거래를 가능하게 하는 데 사용됩니다. 이 키워드를 사용하지 않으면, 해당 함수나 주소는 이더를 수신할 수 없습니다.

### 사용법
"payable"은 다음 두 가지 경우에 사용됩니다:
1. **함수**: 특정 함수가 이더를 받을 수 있도록 설정합니다.
   ```solidity
   function receiveFunds() public payable {
       // 이더를 수신하는 로직
   }
   ```

2. **주소**: 특정 주소가 이더를 수신할 수 있도록 설정합니다.
   ```solidity
   address payable recipient = payable(msg.sender);
   ```

### 세부사항
- **receive() 함수**: 이더가 계약에 직접 전송될 때 호출되는 특별한 함수입니다. 이 함수는 "payable"로 정의되어야 합니다.
- **fallback() 함수**: 존재하지 않는 함수가 호출되거나 이더가 전송될 때 호출됩니다. 이 함수도 "payable"로 정의되어야 합니다.
- **정확한 타입**: "payable" 주소는 일반 주소 타입과는 다릅니다. 이더를 전송하기 위해서는 반드시 "payable"로 선언해야 합니다.

## 예제
### 기본 사용 예제
```solidity
pragma solidity ^0.8.0;

contract SimpleBank {
    mapping(address => uint) public balances;

    function deposit() public payable {
        require(msg.value > 0, "You need to send some Ether");
        balances[msg.sender] += msg.value;
    }

    function withdraw(uint amount) public {
        require(balances[msg.sender] >= amount, "Insufficient balance");
        payable(msg.sender).transfer(amount);
        balances[msg.sender] -= amount;
    }
}
```

## 설명
### 일반적인 함정 및 주의사항
- **이더 전송 실패**: "payable" 함수에서 이더를 수신하기 전, 반드시 조건을 확인해야 합니다. 예를 들어, 이더가 0이 아닌지 확인해야 합니다.
- **가스 한도 초과**: 이더를 전송할 때 가스 한도를 초과하면 거래가 실패할 수 있습니다. 가스 사용량을 미리 계산하고 조정해야 합니다.
- **대체 가능한 주소**: "payable" 주소는 일반 주소와 다르므로, 변환 없이 사용할 수 없습니다. 주소를 "payable"로 변환할 때는 `payable(address)` 구문을 사용해야 합니다.

## 한 줄 요약
Solidity의 "payable" 키워드는 스마트 계약이 이더를 수신할 수 있도록 함수나 주소를 지정하는 중요한 기능입니다.