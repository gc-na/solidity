<!--
Meta Description: # while-Schleifen in Solidity: Eine umfassende Anleitung ## Synopsis Die `while`-Schleife in Solidity ermöglicht es Entwicklern, Codeblöcke wiederholt...
Meta Keywords: die, while, ist, solidity, bedingung
-->

# while-Schleifen in Solidity: Eine umfassende Anleitung

## Synopsis
Die `while`-Schleife in Solidity ermöglicht es Entwicklern, Codeblöcke wiederholt auszuführen, solange eine bestimmte Bedingung wahr ist. Dies ist besonders nützlich für iterative Prozesse, bei denen die Anzahl der Durchläufe im Voraus nicht bekannt ist.

## Dokumentation
Die `while`-Schleife ist eine Kontrollstruktur, die in Solidity verwendet wird, um Anweisungen so lange auszuführen, wie eine bestimmte Bedingung erfüllt ist. Die allgemeine Syntax lautet:

```solidity
while (Bedingung) {
    // Anweisungen
}
```

### Zweck
Die `while`-Schleife ist nützlich, um Aufgaben zu automatisieren, bei denen die Anzahl der Wiederholungen von einer Bedingung abhängt, z. B. beim Durchlaufen von Arrays oder beim Warten auf bestimmte Bedingungen in Smart Contracts.

### Verwendung
Die `while`-Schleife wird verwendet, um einen Block von Anweisungen so lange auszuführen, wie die angegebene Bedingung `true` ist. Es ist wichtig, sicherzustellen, dass die Bedingung irgendwann `false` wird, um eine Endlosschleife zu vermeiden.

### Details
- **Bedingung**: Ein boolescher Ausdruck, der vor jedem Schleifendurchlauf evaluiert wird.
- **Endlosschleife**: Wenn die Bedingung nie `false` wird, kann dies zu einem Ausfall des Smart Contracts führen. Deshalb sollte die Schleifenbedingung gut durchdacht sein.

## Beispiele

### Beispiel 1: Grundlegende while-Schleife
```solidity
pragma solidity ^0.8.0;

contract WhileExample {
    uint256 public count;

    function incrementUntil(uint256 max) public {
        count = 0;
        while (count < max) {
            count++;
        }
    }
}
```
In diesem Beispiel wird die `incrementUntil`-Funktion verwendet, um `count` so lange zu erhöhen, bis es den Wert `max` erreicht.

### Beispiel 2: Verwendung mit Arrays
```solidity
pragma solidity ^0.8.0;

contract ArrayExample {
    uint256[] public numbers;

    function addNumbers(uint256[] memory newNumbers) public {
        uint256 i = 0;
        while (i < newNumbers.length) {
            numbers.push(newNumbers[i]);
            i++;
        }
    }
}
```
Hier wird eine `while`-Schleife verwendet, um eine Liste von Zahlen zu einem Array hinzuzufügen.

## Erklärung
Ein häufiges Problem bei der Verwendung von `while`-Schleifen ist das Risiko einer Endlosschleife. Entwickler sollten sicherstellen, dass die Bedingung, die die Schleife steuert, im Verlauf der Ausführung auf `false` gesetzt wird. Ein weiterer Punkt ist, dass die Schleife in Solidity Gas kosten kann, was bedeutet, dass lange Ausführungen zu hohen Transaktionskosten führen können. Es ist daher ratsam, `while`-Schleifen sparsam und mit Bedacht einzusetzen.

## Ein-Satz-Zusammenfassung
Die `while`-Schleife in Solidity ermöglicht es, Anweisungen wiederholt auszuführen, solange eine angegebene Bedingung erfüllt ist, und sollte mit Vorsicht verwendet werden, um Endlosschleifen zu vermeiden.