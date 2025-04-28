<!--
Meta Description: # Comando "receive" em Solidity: Entenda Como Funciona ## Sinopse O comando `receive` em Solidity é uma função especial utilizada para lidar com receb...
Meta Keywords: função, receive, ether, não, solidity
-->

# Comando "receive" em Solidity: Entenda Como Funciona

## Sinopse
O comando `receive` em Solidity é uma função especial utilizada para lidar com recebimentos de Ether em contratos inteligentes, permitindo que os contratos sejam capazes de receber transferências diretas de Ether.

## Documentação
### Propósito
A função `receive` é acionada quando um contrato recebe Ether e não há dados adicionais na transação. Este recurso é fundamental para contratos que necessitam gerenciar ou registrar as transferências de Ether de forma eficaz.

### Uso
A função `receive` deve ser declarada como uma função pública ou externa e não pode ter argumentos nem retornar valores. A assinatura básica da função é:

```solidity
receive() external payable {}
```

### Detalhes
- **Visibilidade**: A função deve ser `external`.
- **Payable**: A função deve ser marcada como `payable` para permitir que o contrato receba Ether.
- **Sem parâmetros e retorno**: Não pode ter parâmetros nem retornar valores.
- **Conflito com fallback**: Se uma função `fallback` também estiver presente, a função `receive` será chamada apenas quando a transação não incluir dados; caso contrário, a função `fallback` será chamada.

## Exemplos
### Exemplo Básico

```solidity
pragma solidity ^0.8.0;

contract MeuContrato {
    event Recebido(address remetente, uint valor);

    receive() external payable {
        emit Recebido(msg.sender, msg.value);
    }
}
```

Neste exemplo, sempre que o contrato `MeuContrato` receber Ether, um evento `Recebido` será emitido, registrando o remetente e o valor recebido.

### Exemplo com Rejeição de Valores

```solidity
pragma solidity ^0.8.0;

contract MeuContrato {
    receive() external payable {
        // A função recebe Ether, mas não realiza nenhuma ação
    }

    fallback() external payable {
        revert("Transação falhou: dados não permitidos.");
    }
}
```

Aqui, a função `receive` é implementada para aceitar Ether, enquanto a função `fallback` reverte qualquer tentativa de envio de dados.

## Explicação
### Armadilhas Comuns
- **Não implementar `payable`**: Se a função `receive` não for marcada como `payable`, o contrato não conseguirá receber Ether.
- **Conflito com a função `fallback`**: É importante entender a diferença entre `receive` e `fallback`. Se a função `fallback` estiver definida e a transação incluir dados, o código da função `receive` não será executado.
- **Limitações de gas**: Ao chamar um contrato com a função `receive`, tenha em mente as limitações de gas, especialmente se o contrato chamador tiver um limite de gas definido.

## Resumo em Uma Linha
A função `receive` em Solidity é uma maneira de aceitar Ether diretamente em contratos inteligentes, sem a necessidade de dados adicionais na transação.