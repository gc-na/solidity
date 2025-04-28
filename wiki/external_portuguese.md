<!--
Meta Description: # A Profundidade do Modificador "external" em Solidity ## Sinopse O modificador `external` em Solidity é utilizado para definir a visibilidade de funç...
Meta Keywords: external, solidity, que, chamadas, funções
-->

# A Profundidade do Modificador "external" em Solidity

## Sinopse
O modificador `external` em Solidity é utilizado para definir a visibilidade de funções e permite que elas sejam chamadas apenas externamente, sendo uma característica essencial para a segurança e eficiência em contratos inteligentes.

## Documentação
O modificador `external` é um dos quatro tipos de visibilidade disponíveis em Solidity, os outros sendo `public`, `internal` e `private`. Quando uma função é marcada como `external`, ela pode ser chamada apenas por contratos externos ou por transações diretas. Isso significa que funções `external` não podem ser chamadas internamente, ou seja, não podem ser invocadas de dentro do próprio contrato.

### Propósito
O principal objetivo do modificador `external` é restringir o acesso à função, permitindo que ela seja chamada apenas por fontes externas. Isso é útil para funções que devem ser acessíveis apenas por outros contratos ou usuários e não precisam ser chamadas internamente.

### Uso
Para utilizar o modificador `external`, basta declará-lo antes da assinatura da função. Veja a estrutura básica:

```solidity
pragma solidity ^0.8.0;

contract Exemplo {
    function minhaFuncaoExterna() external {
        // lógica da função
    }
}
```

## Exemplos
### Exemplo Básico
```solidity
pragma solidity ^0.8.0;

contract ContratoExterno {
    uint public valor;

    function setValor(uint _valor) external {
        valor = _valor;
    }
}
```

Neste exemplo, a função `setValor` é definida como `external`, permitindo que um contrato externo ou uma conta de usuário a invoque para alterar o valor armazenado.

### Chamadas Internas Não Permitidas
```solidity
pragma solidity ^0.8.0;

contract ContratoTeste {
    function chamaExterna() external {
        setValor(10); // Isso causará um erro de compilação
    }

    function setValor(uint _valor) external {
        // lógica da função
    }
}
```

Aqui, tentar chamar `setValor` de dentro da função `chamaExterna` resultará em um erro, pois `setValor` é `external`.

## Explicação
### Armadilhas Comuns
1. **Chamadas Internas**: Como mencionado, funções `external` não podem ser chamadas diretamente por outras funções dentro do mesmo contrato. Isso pode causar confusão para desenvolvedores que esperam que a função seja acessível internamente.
  
2. **Gás**: Funções `external` podem ser mais eficientes em termos de consumo de gás quando chamadas de contratos externos, já que não precisam de um contexto adicional para a chamada.

3. **Interface**: Ao implementar interfaces, as funções `external` são frequentemente utilizadas, pois permitem que o contrato receba chamadas de outros contratos de forma clara e segura.

## Resumo em Uma Frase
O modificador `external` em Solidity limita a invocação de funções a chamadas externas, promovendo segurança e eficiência em contratos inteligentes.