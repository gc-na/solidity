<!--
Meta Description: # Entendendo o Modificador "internal" em Solidity ## Sinopse O modificador `internal` em Solidity é utilizado para especificar a visibilidade de funçõ...
Meta Keywords: internal, que, solidity, contratos, contrato
-->

# Entendendo o Modificador "internal" em Solidity

## Sinopse
O modificador `internal` em Solidity é utilizado para especificar a visibilidade de funções e variáveis dentro de contratos inteligentes, permitindo que sejam acessadas apenas por contratos que herdam ou estão dentro do mesmo contrato.

## Documentação
O modificador `internal` é um dos níveis de visibilidade em Solidity, que define como e onde as funções e variáveis podem ser acessadas. Quando uma função ou variável é marcada como `internal`, ela só pode ser chamada ou acessada dentro do contrato onde foi definida, ou em contratos que herdam desse contrato.

### Propósito
O propósito do modificador `internal` é fornecer um nível de encapsulamento, permitindo que os desenvolvedores protejam a lógica interna de um contrato e suas variáveis de acesso externo, enquanto ainda permitem que subclasses ou contratos relacionados interajam com esses elementos.

### Uso
O modificador `internal` é utilizado na definição de funções e variáveis dentro de um contrato. Para definir uma função ou variável como `internal`, você deve precedê-la com a palavra-chave `internal`.

```solidity
contract Exemplo {
    uint internal numero;

    function definirNumero(uint _numero) internal {
        numero = _numero;
    }
}
```

## Exemplos
Aqui estão alguns exemplos de como usar o modificador `internal` em Solidity:

### Exemplo 1: Função Internal
```solidity
pragma solidity ^0.8.0;

contract Base {
    uint internal valor;

    function setValor(uint _valor) internal {
        valor = _valor;
    }
}

contract Derivada is Base {
    function atualizarValor(uint _novoValor) public {
        setValor(_novoValor);
    }
}
```
Neste exemplo, a função `setValor` é marcada como `internal`, permitindo que a `Derivada` a acesse.

### Exemplo 2: Variável Internal
```solidity
pragma solidity ^0.8.0;

contract Conta {
    uint internal saldo;

    function depositar(uint _valor) internal {
        saldo += _valor;
    }
}
```
A variável `saldo` é `internal`, o que significa que só pode ser acessada dentro do contrato `Conta` ou por contratos que herdam dele.

## Explicação
É importante entender que, embora o modificador `internal` permita acesso a contratos derivados, ele não permite acesso a contratos externos ou aos usuários diretamente. Isso pode levar a erros de lógica se um desenvolvedor não estiver ciente dessa restrição ao projetar a interação entre contratos.

### Armadilhas Comuns
- **Acesso Não Permitido**: Tentar acessar uma função ou variável `internal` a partir de um contrato que não herda do contrato original resultará em um erro de compilação.
- **Confusão com External**: Não confundir `internal` com `public` ou `external`. Enquanto `public` permite acesso de qualquer lugar, `internal` é restrito a contratos e funções relacionadas.

## Resumo em Uma Frase
O modificador `internal` em Solidity restringe o acesso a funções e variáveis a contratos que herdam ou estão dentro do mesmo contrato, promovendo encapsulamento e segurança.