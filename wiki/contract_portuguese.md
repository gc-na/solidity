<!--
Meta Description: # Contratos em Solidity: A Base da Programação em Blockchain ## Sinopse Os contratos em Solidity são a estrutura fundamental usada para criar aplicati...
Meta Keywords: solidity, contratos, public, que, uint
-->

# Contratos em Solidity: A Base da Programação em Blockchain

## Sinopse
Os contratos em Solidity são a estrutura fundamental usada para criar aplicativos descentralizados na blockchain Ethereum. Eles permitem a execução automática de acordos e regras de negócios de forma segura e transparente.

## Documentação
Os contratos em Solidity são essencialmente programas que são executados na rede Ethereum. Eles são escritos na linguagem de programação Solidity, que é uma linguagem orientada a contratos e inspirada em JavaScript, Python e C++. Os contratos permitem que os desenvolvedores especifiquem a lógica de negócios e as condições de interação entre usuários e a blockchain.

### Propósito
O principal objetivo dos contratos em Solidity é automatizar a execução de acordos sem a necessidade de intermediários. Isso é alcançado através de funções, variáveis de estado e eventos que permitem que um contrato mantenha seu estado e interaja com outros contratos ou usuários.

### Uso
Para definir um contrato em Solidity, utiliza-se a palavra-chave `contract`, seguida do nome do contrato. Dentro do contrato, é possível declarar variáveis, funções e eventos. Os contratos podem ser implantados na blockchain, onde se tornam imutáveis e acessíveis para qualquer um que tenha a rede.

### Estrutura Básica de um Contrato
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract MeuContrato {
    uint public numero;

    function setNumero(uint _numero) public {
        numero = _numero;
    }

    function getNumero() public view returns (uint) {
        return numero;
    }
}
```

## Exemplos
### Exemplo 1: Armazenamento de um Número
Neste exemplo, o contrato permite armazenar e recuperar um número.

```solidity
pragma solidity ^0.8.0;

contract Armazenamento {
    uint public numero;

    function armazenarNumero(uint _numero) public {
        numero = _numero;
    }

    function recuperarNumero() public view returns (uint) {
        return numero;
    }
}
```

### Exemplo 2: Contador Simples
Um contrato que atua como um contador, permitindo incrementar e visualizar o valor.

```solidity
pragma solidity ^0.8.0;

contract Contador {
    uint public contagem;

    function incrementar() public {
        contagem += 1;
    }

    function obterContagem() public view returns (uint) {
        return contagem;
    }
}
```

## Explicação
Um dos principais desafios ao trabalhar com contratos em Solidity é entender a diferença entre variáveis de estado e variáveis locais. As variáveis de estado são armazenadas na blockchain e persistem entre as chamadas de função, enquanto as variáveis locais são criadas e destruídas com a execução da função.

Além disso, desenvolvedores devem estar atentos a problemas de segurança, como reentrância e overflow, que podem ser explorados se não forem tratados adequadamente. É essencial testar e auditar contratos antes de sua implantação.

## Resumo em Uma Linha
Contratos em Solidity são programas autoexecutáveis na blockchain Ethereum, permitindo a criação de aplicativos descentralizados de forma segura e transparente.