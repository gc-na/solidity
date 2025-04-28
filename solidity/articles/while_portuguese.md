<!--
Meta Description: # Laço "while" em Solidity: Uso e Exemplos ## Sinopse O laço "while" em Solidity é uma estrutura de controle que permite a execução repetida de um blo...
Meta Keywords: laço, while, que, condição, uma
-->

# Laço "while" em Solidity: Uso e Exemplos

## Sinopse
O laço "while" em Solidity é uma estrutura de controle que permite a execução repetida de um bloco de código enquanto uma condição especificada for verdadeira. É uma ferramenta essencial para a implementação de lógicas que dependem de iterações dinâmicas.

## Documentação
O laço "while" é utilizado para executar um conjunto de instruções repetidamente, até que uma condição se torne falsa. A sintaxe básica do laço "while" é a seguinte:

```solidity
while (condição) {
    // bloco de código a ser executado
}
```

### Propósito
O propósito do laço "while" é permitir que o desenvolvedor execute um bloco de código repetidamente sem precisar saber previamente o número exato de iterações. Isso é especialmente útil em casos onde a condição de término depende de um estado que muda durante a execução do laço.

### Uso
Para utilizar o laço "while", você deve definir uma condição que será avaliada antes de cada iteração. Se a condição for verdadeira, o bloco de código dentro do laço será executado. Após cada execução, a condição é reavaliada. Caso a condição se torne falsa, o laço é encerrado.

### Detalhes
- **Sobrecarga de Gas:** Como o laço "while" pode potencialmente executar um número indefinido de iterações, é crucial tomar cuidado com a lógica implementada para evitar o esgotamento do gas.
- **Segurança:** Sempre certifique-se de que a condição do laço eventualmente se tornará falsa para evitar loops infinitos, que podem causar falhas na execução do contrato inteligente.

## Exemplos

### Exemplo 1: Contador Simples
```solidity
pragma solidity ^0.8.0;

contract Contador {
    uint public contador;

    function incrementar(uint limite) public {
        while (contador < limite) {
            contador++;
        }
    }
}
```
Neste exemplo, a função `incrementar` utiliza um laço "while" para incrementar a variável `contador` até que ela atinja o valor do `limite` fornecido.

### Exemplo 2: Acumulando Valores
```solidity
pragma solidity ^0.8.0;

contract Acumulador {
    uint public soma;

    function somar(uint limite) public {
        uint i = 0;
        while (i < limite) {
            soma += i;
            i++;
        }
    }
}
```
Aqui, o laço "while" é usado para somar todos os números de 0 até o `limite` especificado, acumulando o resultado na variável `soma`.

## Explicação
Um dos erros mais comuns ao usar o laço "while" é não garantir que a condição eventualmente se tornará falsa. Isso resulta em um loop infinito, que pode levar a uma falha no contrato devido ao consumo excessivo de gas. Além disso, é importante considerar o impacto da execução do laço no custo total de gas da transação.

Ao implementar laços "while", é recomendável incluir verificações adicionais ou limites para evitar problemas de execução. Sempre teste suas funções em um ambiente seguro antes de implantá-las em uma rede principal.

## Resumo em Uma Linha
O laço "while" em Solidity permite executar repetidamente um bloco de código enquanto uma condição especificada for verdadeira, sendo crucial para lógicas dinâmicas e iterativas.