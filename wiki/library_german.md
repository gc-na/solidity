<!--
Meta Description: # Bibliotheken in Solidity: Eine umfassende Anleitung ## Synopsis In Solidity sind Bibliotheken eine spezielle Art von Smart Contracts, die Funktionen...
Meta Keywords: werden, die, bibliotheken, solidity, können
-->

# Bibliotheken in Solidity: Eine umfassende Anleitung

## Synopsis
In Solidity sind Bibliotheken eine spezielle Art von Smart Contracts, die Funktionen bereitstellen, die von anderen Verträgen aufgerufen werden können, ohne dass sie direkt instanziiert werden müssen.

## Dokumentation
### Zweck
Bibliotheken in Solidity dienen dazu, wiederverwendbare Code-Elemente zu erstellen, die von mehreren Verträgen genutzt werden können. Sie ermöglichen eine effiziente Organisation und Modularität des Codes und fördern die Wiederverwendbarkeit von Funktionen.

### Verwendung
Bibliotheken werden in Solidity durch das Schlüsselwort `library` definiert. Sie können Funktionen enthalten, die entweder als `internal` oder `public` deklariert sind. Funktionen in Bibliotheken werden nicht auf dem Blockchain-Zustand ausgeführt, sondern können nur durch andere Verträge aufgerufen werden. 

### Details
- **Deklaration**: Eine Bibliothek wird wie ein Vertrag deklariert, allerdings ohne die Möglichkeit, Instanzen zu erstellen.
- **Funktionale Nutzung**: Bibliotheksfunktionen können durch den Vertrag, der sie aufruft, direkt verwendet werden, ohne dass eine Instanz der Bibliothek benötigt wird.
- **Speicheroptimierung**: Da Bibliotheken keine eigenen Zustände haben, können sie den Speicherplatz optimieren und die Gas-Kosten senken.

## Beispiele
### Beispiel 1: Eine einfache Bibliothek
```solidity
pragma solidity ^0.8.0;

library Math {
    function add(uint a, uint b) internal pure returns (uint) {
        return a + b;
    }
}

contract Calculator {
    using Math for uint;

    function calculate(uint a, uint b) public pure returns (uint) {
        return a.add(b);
    }
}
```

### Beispiel 2: Verwendung von Bibliotheksfunktionen
```solidity
pragma solidity ^0.8.0;

library StringUtils {
    function concat(string memory str1, string memory str2) internal pure returns (string memory) {
        return string(abi.encodePacked(str1, str2));
    }
}

contract Greeter {
    using StringUtils for string;

    string public greeting;

    constructor(string memory _greeting) {
        greeting = _greeting;
    }

    function updateGreeting(string memory newGreeting) public {
        greeting = greeting.concat(newGreeting);
    }
}
```

## Erklärung
Ein häufiges Missverständnis bei der Verwendung von Bibliotheken ist, dass sie wie reguläre Verträge instanziiert werden können. Dies ist jedoch nicht der Fall. Bibliotheken sind dazu gedacht, als statische Funktionseinheiten zu fungieren, die in anderen Verträgen verwendet werden. 

Ein weiterer Punkt ist, dass alle Funktionen in einer Bibliothek `internal` oder `public` sein müssen. `private`-Funktionen sind nicht erlaubt, da sie nicht von anderen Verträgen aufgerufen werden können.

## Einzeilige Zusammenfassung
Bibliotheken in Solidity sind wiederverwendbare Codeeinheiten, die Funktionen bereitstellen, die von anderen Verträgen aufgerufen werden können, ohne dass sie instanziiert werden müssen.