<!--
Meta Description: # Mapeamentos em Solidity: O Guia Completo para Desenvolvedores ## Sinopse Os mapeamentos são uma estrutura de dados fundamental em Solidity que permi...
Meta Keywords: solidity, uint, mapeamentos, que, valor
-->

# Mapeamentos em Solidity: O Guia Completo para Desenvolvedores

## Sinopse
Os mapeamentos são uma estrutura de dados fundamental em Solidity que permitem o armazenamento eficiente de pares chave-valor. Eles são amplamente utilizados para gerenciar dados em contratos inteligentes na blockchain Ethereum.

## Documentação
### O que são Mapeamentos?
Em Solidity, um mapeamento é uma coleção de pares chave-valor, onde cada chave é única e está associada a um valor. Os mapeamentos são utilizados para armazenar dados de forma eficiente e acessá-los rapidamente.

### Sintaxe
A sintaxe básica para declarar um mapeamento em Solidity é a seguinte:
```solidity
mapping (tipoChave => tipoValor) nomeDoMapping;
```
- **tipoChave**: O tipo de dado que será usado como chave. Pode ser um tipo primitivo, como `uint`, `address`, ou mesmo um tipo definido pelo usuário.
- **tipoValor**: O tipo de dado que será armazenado como valor. Também pode ser um tipo primitivo ou um tipo definido pelo usuário.

### Inicialização
Os mapeamentos não precisam ser inicializados explicitamente. Quando um mapeamento é criado, todas as chaves têm um valor padrão. Por exemplo, um mapeamento de `uint` terá um valor padrão de 0.

### Uso
Os mapeamentos são utilizados para diversas finalidades em contratos inteligentes, como:
- Armazenar saldos de tokens.
- Manter o registro de usuários.
- Criar listas de permissões.

## Exemplos
### Exemplo 1: Mapeamento Simples
```solidity
pragma solidity ^0.8.0;

contract ExemploMapping {
    mapping(address => uint) public saldos;

    function depositar() public payable {
        saldos[msg.sender] += msg.value;
    }
    
    function obterSaldo() public view returns (uint) {
        return saldos[msg.sender];
    }
}
```

### Exemplo 2: Mapeamento de Estruturas
```solidity
pragma solidity ^0.8.0;

contract RegistroEstudantes {
    struct Estudante {
        string nome;
        uint idade;
    }

    mapping(uint => Estudante) public estudantes;

    function adicionarEstudante(uint id, string memory nome, uint idade) public {
        estudantes[id] = Estudante(nome, idade);
    }
    
    function obterEstudante(uint id) public view returns (string memory, uint) {
        Estudante memory estudante = estudantes[id];
        return (estudante.nome, estudante.idade);
    }
}
```

## Explicação
### Armadilhas Comuns
- **Chaves Não Existentes**: Ao acessar um valor para uma chave que não existe, o retorno será o valor padrão do tipo, que pode ser confuso. Por exemplo, um `uint` retornará 0, mesmo que a chave nunca tenha sido definida.
- **Limitações de Chave**: Mapeamentos não podem ser iterados. Não existe uma maneira nativa em Solidity para obter todas as chaves de um mapeamento, o que pode limitar sua utilização em alguns casos.
- **Armazenamento em Gas**: Os mapeamentos são armazenados no armazenamento permanente da blockchain, o que pode aumentar o custo de gás. É importante otimizar o uso de mapeamentos para evitar custos desnecessários.

## Resumo em Uma Linha
Os mapeamentos em Solidity são uma estrutura de dados que permite armazenar e acessar pares chave-valor de forma eficiente em contratos inteligentes.