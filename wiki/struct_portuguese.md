<!--
Meta Description: # Estruturas em Solidity: Como Utilizar Structs de Forma Eficiente ## Sinopse As estruturas (structs) em Solidity são tipos de dados personalizados qu...
Meta Keywords: struct, pessoa, solidity, structs, para
-->

# Estruturas em Solidity: Como Utilizar Structs de Forma Eficiente

## Sinopse
As estruturas (structs) em Solidity são tipos de dados personalizados que permitem agrupar diferentes informações sob um único nome. Elas são fundamentais para organizar dados de forma eficiente em contratos inteligentes.

## Documentação
Os structs em Solidity são usados para criar tipos de dados compostos, permitindo que os desenvolvedores definam suas próprias estruturas de dados. Cada struct pode conter diferentes tipos de variáveis, incluindo outros structs, arrays e tipos primitivos. Isso é especialmente útil para modelar entidades complexas no blockchain, como usuários, produtos ou transações.

### Definição de Struct
Um struct é definido utilizando a palavra-chave `struct`, seguida do nome do struct e suas variáveis. A sintaxe básica é a seguinte:

```solidity
struct NomeDoStruct {
    TipoDeDado1 nomeDaVariavel1;
    TipoDeDado2 nomeDaVariavel2;
}
```

### Uso de Structs
Uma vez definido, o struct pode ser usado para declarar variáveis e armazenar dados. Você pode criar instâncias do struct e acessar suas propriedades utilizando a notação de ponto.

## Exemplos
### Exemplo Básico de Struct
```solidity
pragma solidity ^0.8.0;

contract ExemploStruct {
    struct Pessoa {
        string nome;
        uint idade;
    }

    Pessoa public pessoa;

    function criarPessoa(string memory _nome, uint _idade) public {
        pessoa = Pessoa(_nome, _idade);
    }
}
```

Neste exemplo, definimos um struct chamado `Pessoa` com duas variáveis: `nome` e `idade`. A função `criarPessoa` permite criar uma nova instância de `Pessoa`.

### Exemplo com Array de Structs
```solidity
pragma solidity ^0.8.0;

contract RegistroPessoas {
    struct Pessoa {
        string nome;
        uint idade;
    }

    Pessoa[] public pessoas;

    function adicionarPessoa(string memory _nome, uint _idade) public {
        pessoas.push(Pessoa(_nome, _idade));
    }
}
```

Aqui, temos um array de `Pessoa`, permitindo que várias instâncias sejam armazenadas.

## Explicação
Ao trabalhar com structs, é importante estar ciente de alguns pontos:

1. **Limite de Tamanho**: O tamanho total de um struct pode afetar o custo de gás em transações. Estruturas muito grandes podem resultar em custos elevados.
  
2. **Transparência**: Structs são armazenadas na blockchain, portanto, qualquer dado que você armazenar será público. Cuidado com informações sensíveis.
  
3. **Complexidade**: Estruturas aninhadas podem aumentar a complexidade do código. É recomendável manter a simplicidade sempre que possível.

4. **Inicialização**: Quando um struct é declarado, suas variáveis são inicializadas com valores padrão (zero para inteiros, string vazia para strings, etc.).

## Resumo em Uma Frase
Os structs em Solidity são uma ferramenta poderosa para criar tipos de dados personalizados, permitindo a organização eficiente de informações em contratos inteligentes.