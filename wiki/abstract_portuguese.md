<!--
Meta Description: # Abstract: Entendendo o Conceito de Contratos Abstratos em Solidity ## Sinopse O termo "abstract" em Solidity refere-se a contratos que não podem ser...
Meta Keywords: contrato, que, contratos, solidity, abstrato
-->

# Abstract: Entendendo o Conceito de Contratos Abstratos em Solidity

## Sinopse
O termo "abstract" em Solidity refere-se a contratos que não podem ser instanciados diretamente. Eles servem como base para outros contratos, permitindo implementar funcionalidades comuns e definir interfaces que devem ser seguidas nas implementações concretas.

## Documentação
### O que é um Contrato Abstrato?
Em Solidity, um contrato abstrato é um contrato que contém pelo menos uma função não implementada ou uma função que não possui corpo. Ele não pode ser implantado diretamente na blockchain, mas pode ser estendido por contratos concretos que implementam suas funções.

### Propósito
O principal objetivo de um contrato abstrato é fornecer uma estrutura que outros contratos podem herdar. Isso promove a reutilização de código e a definição de contratos de interface que garantem que certas funções sejam implementadas nas classes derivadas.

### Uso
Para declarar um contrato como abstrato, utiliza-se a palavra-chave `abstract` antes da declaração do contrato. Dentro desse contrato, você pode definir funções abstratas (sem implementação) que devem ser obrigatoriamente implementadas pelo contrato que herdar.

### Sintaxe
```solidity
abstract contract NomeDoContrato {
    function funcaoAbstrata() public virtual;
}
```

## Exemplos
### Exemplo Básico de Contrato Abstrato
```solidity
// Declaração de um contrato abstrato
abstract contract Animal {
    function emitirSom() public virtual returns (string memory);
}

// Implementação do contrato que herda do contrato abstraído
contract Cachorro is Animal {
    function emitirSom() public pure override returns (string memory) {
        return "Au Au";
    }
}
```

### Exemplo de Vários Contratos Abstratos
```solidity
abstract contract Veiculo {
    function acelerar() public virtual;
}

contract Carro is Veiculo {
    function acelerar() public override {
        // Lógica para acelerar o carro
    }
}

contract Moto is Veiculo {
    function acelerar() public override {
        // Lógica para acelerar a moto
    }
}
```

## Explicação
### Armadilhas Comuns
1. **Não Implementar Funções Abstratas**: Se um contrato concreto não implementar todas as funções abstratas, o compilador gerará um erro.
2. **Tentativa de Instanciar o Contrato Abstrato**: Tentar implantar um contrato abstrato diretamente resultará em erro. Sempre use contratos concretos derivados.
3. **Palavra-chave `virtual`**: Ao declarar funções nas classes filhas, é necessário usar a palavra-chave `override` para indicar que você está sobrescrevendo uma função abstrata.

### Notas Adicionais
- Os contratos abstratos são uma ferramenta poderosa para a criação de sistemas complexos, permitindo um design mais modular e escalável.
- Eles desempenham um papel importante na implementação de padrões de design em Solidity, como o padrão de contrato de fábrica e o padrão de proxy.

## Resumo em Uma Frase
Contratos abstratos em Solidity são fundamentais para a criação de estruturas reutilizáveis e definem contratos de interface que devem ser implementados por contratos concretos.