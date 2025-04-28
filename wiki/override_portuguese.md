<!--
Meta Description: # Override em Solidity: Entendendo o Comando para Sobrescrever Funções ## Sinopse O comando **override** em Solidity é utilizado para sobrescrever fun...
Meta Keywords: override, que, solidity, função, funções
-->

# Override em Solidity: Entendendo o Comando para Sobrescrever Funções

## Sinopse
O comando **override** em Solidity é utilizado para sobrescrever funções de contratos base em contratos derivados, permitindo que desenvolvedores customize o comportamento de funções herdadas.

## Documentação
O **override** é uma palavra-chave essencial no Solidity, especialmente no contexto de herança de contratos. Quando um contrato herda de outro e deseja modificar uma função que já foi definida na classe pai, o desenvolvedor deve utilizar o modificador **override**. Isso garante que a nova implementação substitua a antiga, promovendo a flexibilidade e a reutilização de código.

### Propósito
O propósito do **override** é assegurar que a função na subclasse substitua a implementação da superclasse. Essa prática é comum em programação orientada a objetos, permitindo que contratos derivados alterem ou estendam o comportamento de contratos base.

### Uso
Para utilizar o **override**, a função na subclasse deve ter a mesma assinatura que a função na superclasse que se deseja sobrescrever. O uso incorreto ou a falta do modificador **override** resultará em um erro de compilação.

### Detalhes
- O **override** é obrigatório para funções que são marcadas como virtual na superclasse.
- Pode ser aplicado a funções públicas, internas e também em funções de eventos.
- Em versões mais recentes do Solidity, também é possível utilizar o **override** em interfaces.

## Exemplos
### Exemplo Básico 1: Sobrescrevendo uma Função
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract Base {
    function greet() public virtual pure returns (string memory) {
        return "Olá do contrato base!";
    }
}

contract Derived is Base {
    function greet() public override pure returns (string memory) {
        return "Olá do contrato derivado!";
    }
}
```

### Exemplo Básico 2: Múltiplos Overrides
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract A {
    function foo() public virtual pure returns (string memory) {
        return "Foo A";
    }
}

contract B is A {
    function foo() public virtual override pure returns (string memory) {
        return "Foo B";
    }
}

contract C is B {
    function foo() public override pure returns (string memory) {
        return "Foo C";
    }
}
```

## Explicação
Um erro comum ao usar **override** é não marcar a função da superclasse como **virtual**, o que fará com que o compilador não reconheça que a função está sendo sobrescrita. Além disso, a assinatura da função deve ser idêntica na subclasse e na superclasse, incluindo modificadores de visibilidade (public, internal). 

Outro ponto a ser observado é que se você tentar sobrescrever uma função que não foi marcada como **virtual**, o compilador retornará um erro, pois não é permitido modificar comportamentos de funções sem essa declaração.

## Resumo em Uma Frase
O comando **override** em Solidity é utilizado para sobrescrever funções herdadas, permitindo que contratos derivados personalizem seu comportamento.