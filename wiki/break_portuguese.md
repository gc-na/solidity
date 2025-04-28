<!--
Meta Description: # Comando "break" em Solidity: Controle de Fluxo em Laços ## Sinopse O comando `break` em Solidity é utilizado para interromper a execução de laços, c...
Meta Keywords: break, laço, solidity, contador, quando
-->

# Comando "break" em Solidity: Controle de Fluxo em Laços

## Sinopse
O comando `break` em Solidity é utilizado para interromper a execução de laços, como `for`, `while` e `do-while`, permitindo que o código saia imediatamente do bloco de repetição ao atender a uma condição específica.

## Documentação
O `break` é uma instrução de controle de fluxo que serve para interromper a iteração de um laço. É especialmente útil quando uma condição é atendida e não é mais necessário continuar a execução do laço, economizando tempo e recursos computacionais.

### Uso
O `break` deve ser utilizado dentro de um laço. Quando a instrução `break` é alcançada, o controle do programa é transferido para a primeira linha de código após o laço. O `break` não pode ser utilizado fora de um contexto de laço.

#### Sintaxe:
```solidity
for (uint i = 0; i < 10; i++) {
    if (i == 5) {
        break; // Interrompe o laço quando i é igual a 5
    }
    // Código a ser executado
}
```

## Exemplos
### Exemplo 1: Uso básico do `break`
```solidity
pragma solidity ^0.8.0;

contract ExemploBreak {
    function encontrarNumero() public pure returns (uint) {
        for (uint i = 0; i < 10; i++) {
            if (i == 7) {
                break; // Interrompe o laço quando i é 7
            }
        }
        return i; // Retorna 7
    }
}
```

### Exemplo 2: Interrompendo um laço `while`
```solidity
pragma solidity ^0.8.0;

contract ExemploWhileBreak {
    function contarAteCinco() public pure returns (uint) {
        uint contador = 0;
        while (contador < 10) {
            if (contador == 5) {
                break; // Interrompe o laço quando contador é 5
            }
            contador++;
        }
        return contador; // Retorna 5
    }
}
```

## Explicação
Um dos erros comuns ao usar `break` é tentar utilizá-lo fora de um laço. Isso resultará em um erro de compilação, pois `break` não tem um contexto válido. Além disso, os desenvolvedores devem ter cuidado ao usar `break` dentro de laços aninhados, pois ele apenas interrompe o laço mais interno em que se encontra.

Outra armadilha potencial é a confusão entre o `break` e o `continue`. Enquanto `break` encerra o laço, `continue` apenas pula a iteração atual e passa para a próxima.

## Resumo em uma linha
O comando `break` em Solidity permite interromper a execução de laços, proporcionando controle sobre a iteração do código.