<!--
Meta Description: # Imutável em Solidity: Compreendendo a Palavra-Chave `immutable` ## Sinopse A palavra-chave `immutable` em Solidity permite que variáveis de estado s...
Meta Keywords: immutable, solidity, variáveis, uma, que
-->

# Imutável em Solidity: Compreendendo a Palavra-Chave `immutable`

## Sinopse
A palavra-chave `immutable` em Solidity permite que variáveis de estado sejam definidas como imutáveis, ou seja, seus valores podem ser atribuídos apenas uma vez durante a construção do contrato e não podem ser alterados posteriormente. Isso oferece uma maneira de otimizar o consumo de gás e garantir a integridade dos dados.

## Documentação
A palavra-chave `immutable` foi introduzida no Solidity 0.6.0 e serve para declarar variáveis que são definidas uma única vez no momento da construção do contrato. Ao contrário das variáveis de estado tradicionais, que podem ser alteradas a qualquer momento, variáveis imutáveis mantêm seu valor constante após a inicialização.

### Propósito
O principal propósito do `immutable` é proporcionar segurança e eficiência. Ao utilizar variáveis imutáveis, você pode reduzir o custo de armazenamento em Ethereum, pois o compilador sabe que esses valores não mudarão, permitindo otimizações.

### Uso
Para usar a palavra-chave `immutable`, você deve declará-la antes do tipo da variável. A atribuição do valor pode ser feita no construtor do contrato ou na declaração.

#### Sintaxe
```solidity
contract MeuContrato {
    uint256 public immutable meuValor;

    constructor(uint256 _valor) {
        meuValor = _valor;
    }
}
```

Neste exemplo, `meuValor` é uma variável imutável que é inicializada no construtor e não pode ser alterada depois.

## Exemplos

### Exemplo Básico
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract ExemploImutavel {
    address public immutable dono;

    constructor() {
        dono = msg.sender; // Atribuição feita no construtor
    }

    function obterDono() public view returns (address) {
        return dono; // Retorna o endereço do dono
    }
}
```

### Exemplo com Parâmetro
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract Configuracao {
    string public immutable nome;
    uint256 public immutable id;

    constructor(string memory _nome, uint256 _id) {
        nome = _nome; // Atribuição feita no construtor
        id = _id;     // Atribuição feita no construtor
    }
}
```

## Explicação
### Armadilhas Comuns
- **Tentativa de Alteração**: Um erro comum é tentar alterar o valor de uma variável imutável após sua inicialização. Isso resultará em um erro de compilação.
- **Inicialização fora do Construtor**: As variáveis imutáveis devem ser inicializadas no momento da construção ou na declaração. A tentativa de inicializá-las em uma função externa resultará em erro.
- **Simplicidade do Código**: Embora o uso de variáveis imutáveis possa simplificar o entendimento do código, é essencial que os desenvolvedores compreendam quando e como utilizá-las corretamente para evitar confusões.

## Resumo em Uma Linha
A palavra-chave `immutable` em Solidity permite a criação de variáveis de estado que são atribuídas uma única vez durante a construção do contrato, garantindo segurança e eficiência no consumo de gás.