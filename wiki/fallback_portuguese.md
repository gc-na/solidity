<!--
Meta Description: # Fallback em Solidity: Entendendo a Função de Retorno no Ethereum ## Sinopse A função fallback em Solidity é um recurso fundamental que permite que c...
Meta Keywords: função, fallback, que, solidity, não
-->

# Fallback em Solidity: Entendendo a Função de Retorno no Ethereum

## Sinopse
A função fallback em Solidity é um recurso fundamental que permite que contratos inteligentes respondam a chamadas que não correspondem a nenhuma função existente ou que recebam Ether.

## Documentação
A função fallback é uma função especial em Solidity que é executada em situações específicas. Ela pode ser definida de duas maneiras, dependendo da versão do Solidity utilizada. A função fallback é frequentemente utilizada para:

- Receber Ether enviado para o contrato.
- Capturar chamadas de função que não correspondem a nenhuma função definida no contrato.

### Estrutura da Função Fallback
A função fallback não aceita argumentos e não retorna nenhum valor. Na versão mais recente do Solidity, a definição da função fallback é feita da seguinte forma:

```solidity
fallback() external payable { 
    // lógica aqui
}
```

### Propósito e Uso
A função fallback é tipicamente utilizada para:

1. **Receber Ether:** Quando um usuário envia Ether para o contrato sem especificar uma função, a função fallback é invocada.
2. **Capturar Chamadas Inválidas:** Se uma chamada for feita a uma função que não existe no contrato, a função fallback é executada, permitindo o tratamento dessa situação.

### Considerações Importantes
- A função fallback deve ser marcada como `external` e pode ser `payable` se o contrato precisar aceitar Ether.
- Apenas uma função fallback pode ser definida em um contrato.

## Exemplos

### Exemplo Básico de Fallback
```solidity
pragma solidity ^0.8.0;

contract MeuContrato {
    event Recebido(address remetente, uint valor);

    fallback() external payable {
        emit Recebido(msg.sender, msg.value);
    }
}
```
Neste exemplo, cada vez que Ether é enviado para `MeuContrato`, um evento `Recebido` é emitido, registrando o remetente e o valor recebido.

### Exemplo de Captura de Chamadas Inválidas
```solidity
pragma solidity ^0.8.0;

contract MeuContrato {
    uint public valor;

    fallback() external payable {
        valor += msg.value;
    }

    function getValor() public view returns (uint) {
        return valor;
    }
}
```
Neste exemplo, a função fallback acumula o valor recebido sempre que Ether é enviado ao contrato, mesmo que não haja uma função correspondente sendo chamada.

## Explicação
### Armadilhas Comuns
- **Limitações de Gas:** Chamadas para a função fallback devem ser cuidadosas quanto ao uso de gas, pois não há garantias de que o contrato receberá gas suficiente em todas as situações.
- **Funções não Pagáveis:** Se a função fallback não for marcada como `payable`, ela não poderá receber Ether, resultando em falhas ao tentar enviar fundos.
- **Sobrecarga da Função:** A função fallback deve ser simples, pois não pode ter lógica complexa que consuma muito gas ou cause falhas.

## Resumo em Uma Linha
A função fallback em Solidity é uma função especial que permite que contratos recebam Ether e tratem chamadas de funções inexistentes.