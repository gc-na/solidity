<!--
Meta Description: # tx: Compreendendo Transações em Solidity ## Sinopse No contexto da programação em Solidity, `tx` é uma variável global que fornece informações sobre...
Meta Keywords: transação, solidity, que, remetente, variável
-->

# tx: Compreendendo Transações em Solidity

## Sinopse
No contexto da programação em Solidity, `tx` é uma variável global que fornece informações sobre a transação em execução, incluindo detalhes sobre remetente, valor e outras propriedades relevantes. Essa funcionalidade é fundamental para o desenvolvimento de contratos inteligentes na blockchain Ethereum.

## Documentação
A variável global `tx` em Solidity é utilizada para acessar informações sobre a transação atual. Ela contém dados que podem ser cruciais para a lógica de um contrato inteligente. As propriedades mais comuns da variável `tx` incluem:

- **tx.origin**: Retorna o endereço do remetente original da transação. É importante notar que o `tx.origin` pode ser diferente do `msg.sender`, especialmente em chamadas de contratos.
- **tx.gasprice**: Retorna o preço do gás da transação em wei, o que é útil para calcular custos de execução de funções.
- **tx.value**: Representa a quantidade de Ether (em wei) que foi enviada junto com a transação.

Essas informações podem ser utilizadas para implementar funcionalidades de segurança e lógica de negócios em contratos inteligentes.

## Exemplos

### Exemplo 1: Acessando o Remetente da Transação
```solidity
pragma solidity ^0.8.0;

contract ExemploTx {
    address public remetente;

    function setRemetente() public {
        remetente = tx.origin;
    }
}
```
Neste exemplo, o contrato `ExemploTx` armazena o endereço do remetente original da transação na variável `remetente`.

### Exemplo 2: Verificando o Preço do Gás
```solidity
pragma solidity ^0.8.0;

contract GasPrice {
    uint public gasPreco;

    function armazenarGasPreco() public {
        gasPreco = tx.gasprice;
    }
}
```
Aqui, o contrato `GasPrice` armazena o preço do gás da transação na variável `gasPreco`.

### Exemplo 3: Verificando o Valor da Transação
```solidity
pragma solidity ^0.8.0;

contract ValorTransacao {
    uint public valorRecebido;

    function receberValor() public payable {
        valorRecebido = tx.value;
    }
}
```
Neste exemplo, o contrato `ValorTransacao` armazena o valor que foi enviado junto com a transação.

## Explicação
Embora a variável `tx` seja útil, seu uso deve ser feito com cautela. Aqui estão alguns pontos a considerar:

- **Segurança**: O uso de `tx.origin` pode levar a vulnerabilidades de segurança. É recomendado usar `msg.sender` para verificar o remetente da função, pois `tx.origin` pode ser manipulado em transações que envolvem múltiplos contratos.
- **Custo de Gás**: O preço do gás pode variar, e a execução de funções que dependem de `tx.gasprice` deve considerar que os valores podem mudar rapidamente.
- **Conformidade com a EIP**: Fique atento às atualizações do Ethereum Improvement Proposal (EIP) que podem afetar o comportamento de transações e a forma como a variável `tx` é utilizada.

## Resumo em Uma Linha
A variável `tx` em Solidity fornece informações cruciais sobre a transação atual, como remetente, preço do gás e valor, e deve ser usada com cautela para evitar vulnerabilidades.