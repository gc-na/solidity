<!--
Meta Description: # Função em Solidity: Compreendendo a Estrutura e Uso ## Sinopse As funções em Solidity são blocos fundamentais de código que permitem a execução de t...
Meta Keywords: funções, função, solidity, que, estado
-->

# Função em Solidity: Compreendendo a Estrutura e Uso

## Sinopse
As funções em Solidity são blocos fundamentais de código que permitem a execução de tarefas específicas, facilitando a modularidade e reutilização do código em contratos inteligentes.

## Documentação
Em Solidity, uma **função** é uma coleção de comandos que executam uma tarefa específica. As funções são essenciais para a organização do código e podem ser usadas para manipular dados, interagir com outros contratos, ou executar lógicas de negócios. Elas podem ser públicas, internas, externas ou privadas, dependendo da visibilidade desejada.

### Estrutura de uma Função
Uma função em Solidity é definida com a seguinte sintaxe básica:

```solidity
função nomeDaFuncao(tipoRetorno nomeDosParametros) public {
    // corpo da função
}
```

- **tipoRetorno**: O tipo de dado que a função retorna (por exemplo, `uint`, `string`, `address`, etc.). Se não houver retorno, pode-se usar `void`.
- **nomeDosParametros**: Parâmetros que a função aceita, especificando seu tipo e nome.
- **visibilidade**: O modificador de visibilidade (public, private, internal, external).

### Tipos de Funções
- **Funções de Estado**: Alteram o estado do contrato.
- **Funções de Visualização**: Não alteram o estado e podem ser chamadas sem custo de gás.
- **Funções Puras**: Não leem nem alteram o estado do contrato.

## Exemplos
### Exemplo Básico de uma Função

```solidity
pragma solidity ^0.8.0;

contract Exemplo {
    uint public numero;

    function definirNumero(uint _numero) public {
        numero = _numero;
    }

    function obterNumero() public view returns (uint) {
        return numero;
    }
}
```

Neste exemplo, `definirNumero` altera o estado do contrato, enquanto `obterNumero` permite a leitura do valor armazenado.

### Exemplo de Função com Parâmetros

```solidity
pragma solidity ^0.8.0;

contract Calculadora {
    function somar(uint a, uint b) public pure returns (uint) {
        return a + b;
    }
}
```

A função `somar` aceita dois parâmetros e retorna a soma deles sem alterar o estado do contrato.

## Explicação
Ao trabalhar com funções em Solidity, é importante estar ciente de alguns pontos críticos:

- **Visibilidade**: Escolher o modificador de visibilidade adequado é crucial. Usar `public` em funções que não deveriam ser acessíveis externamente pode comprometer a segurança do contrato.
- **Custo de Gás**: Funções que alteram o estado do contrato custam gás, enquanto funções de visualização não.
- **Retorno de Valores**: Sempre verifique se o tipo de retorno está correto para evitar erros de compilação.

### Armadilhas Comuns
- **Funções não executáveis**: Certifique-se de que a função seja chamada corretamente e que os parâmetros estejam sendo passados conforme o esperado.
- **Alteração de estado não intencional**: Funções que não devem alterar o estado devem ser marcadas como `view` ou `pure` para evitar mudanças indesejadas.

## Resumo em Uma Linha
As funções em Solidity são blocos de código que realizam tarefas específicas e são fundamentais para a estrutura e funcionalidade de contratos inteligentes.