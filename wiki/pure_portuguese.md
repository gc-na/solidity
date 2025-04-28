<!--
Meta Description: # A Keyword "pure" em Solidity: Entenda Seu Uso e Importância ## Sinopse O modificador "pure" em Solidity é utilizado para indicar que uma função não ...
Meta Keywords: pure, que, função, não, estado
-->

# A Keyword "pure" em Solidity: Entenda Seu Uso e Importância

## Sinopse
O modificador "pure" em Solidity é utilizado para indicar que uma função não lê nem modifica o estado do contrato. Este artigo explora o propósito, a utilização e os exemplos práticos desse modificador, além de alguns cuidados a serem tomados ao usá-lo.

## Documentação

### O que é "pure"?
No contexto da programação em Solidity, o modificador "pure" é uma declaração que indica que a função não interage com o estado da blockchain, ou seja, não lê nem altera variáveis de estado. Ele é usado para funções que realizam cálculos ou operações que dependem exclusivamente de seus parâmetros de entrada.

### Propósito
O principal objetivo do modificador "pure" é otimizar o código, garantindo que o compilador saiba que a função é auto-suficiente e não tem efeitos colaterais. Isso pode levar a uma execução mais eficiente e a uma melhor legibilidade do código.

### Uso
Para declarar uma função como "pure", você deve especificar o modificador antes da definição da função. Por exemplo:

```solidity
function calcularSoma(uint a, uint b) public pure returns (uint) {
    return a + b;
}
```

Neste exemplo, a função `calcularSoma` é marcada como "pure" porque ela não acessa ou modifica qualquer variável de estado do contrato.

## Exemplos

### Exemplo 1: Função "pure" Simples
```solidity
pragma solidity ^0.8.0;

contract Calculadora {
    function multiplicar(uint a, uint b) public pure returns (uint) {
        return a * b;
    }
}
```
Neste exemplo, a função `multiplicar` calcula o produto de dois números inteiros sem interagir com o estado do contrato.

### Exemplo 2: Função "pure" com Cálculo Condicional
```solidity
pragma solidity ^0.8.0;

contract Comparador {
    function maior(uint a, uint b) public pure returns (uint) {
        return a > b ? a : b;
    }
}
```
A função `maior` retorna o maior dos dois números fornecidos, demonstrando um uso prático do modificador "pure".

## Explicação

### Armadilhas Comuns
1. **Tentativa de Acesso ao Estado**: Uma função marcada como "pure" não pode acessar variáveis de estado. Tentar fazer isso resultará em um erro de compilação.
2. **Confusão com "view"**: É importante não confundir "pure" com "view". Enquanto "view" permite a leitura do estado, "pure" não permite nem leitura nem escrita.

### Notas Adicionais
- O uso de "pure" pode melhorar a segurança do contrato, já que garante que determinadas funções não afetarão o estado da blockchain.
- O modificador "pure" não implica que a função seja necessariamente mais rápida, mas sim que não realiza operações que possam alterar o estado.

## Resumo em Uma Linha
O modificador "pure" em Solidity é usado para declarar funções que não leem nem alteram o estado do contrato, garantindo eficiência e segurança no código.