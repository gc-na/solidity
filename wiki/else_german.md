<!--
Meta Description: # "else" in Solidity: Bedingte Anweisungen verstehen ## Synopsis Das Schlüsselwort "else" in Solidity ermöglicht es Entwicklern, alternative Ausführun...
Meta Keywords: else, die, solidity, wird, ist
-->

# "else" in Solidity: Bedingte Anweisungen verstehen

## Synopsis
Das Schlüsselwort "else" in Solidity ermöglicht es Entwicklern, alternative Ausführungspfade innerhalb von bedingten Anweisungen zu definieren, wodurch die Logik von Smart Contracts flexibler und anpassungsfähiger gestaltet wird.

## Dokumentation
In Solidity, einer Programmiersprache für die Entwicklung von Smart Contracts auf der Ethereum-Blockchain, wird das Schlüsselwort "else" häufig in Verbindung mit der "if"-Anweisung verwendet. Es dient dazu, eine alternative Ausführung zu ermöglichen, wenn die Bedingung der "if"-Anweisung nicht erfüllt ist.

### Zweck
Der Hauptzweck von "else" ist die Steuerung des Programmflusses. Wenn die Bedingung einer "if"-Anweisung falsch ist, wird der Code im "else"-Block ausgeführt. Dies ist besonders nützlich, um unterschiedliche Logiken für verschiedene Bedingungen zu implementieren.

### Verwendung
Die grundlegende Syntax einer "if-else"-Struktur in Solidity sieht wie folgt aus:

```solidity
if (Bedingung) {
    // Code, der ausgeführt wird, wenn die Bedingung wahr ist
} else {
    // Code, der ausgeführt wird, wenn die Bedingung falsch ist
}
```

Zusätzlich kann auch eine "else if"-Klausel verwendet werden, um mehrere Bedingungen zu prüfen:

```solidity
if (Bedingung1) {
    // Code für Bedingung1
} else if (Bedingung2) {
    // Code für Bedingung2
} else {
    // Code, der ausgeführt wird, wenn keine der Bedingungen wahr ist
}
```

## Beispiele
Hier sind einige grundlegende Beispiele zur Verwendung von "else" in Solidity:

### Beispiel 1: Einfaches if-else
```solidity
pragma solidity ^0.8.0;

contract Beispiel {
    uint public zahl;

    function setZahl(uint _zahl) public {
        if (_zahl > 10) {
            zahl = _zahl;
        } else {
            zahl = 0;
        }
    }
}
```
In diesem Beispiel wird die Variable `zahl` nur gesetzt, wenn `_zahl` größer als 10 ist. Andernfalls wird `zahl` auf 0 gesetzt.

### Beispiel 2: if-else mit else if
```solidity
pragma solidity ^0.8.0;

contract Beispiel {
    uint public wert;

    function bewertung(uint _punktzahl) public {
        if (_punktzahl > 90) {
            wert = 1; // Sehr gut
        } else if (_punktzahl > 75) {
            wert = 2; // Gut
        } else {
            wert = 3; // Verbesserungsbedarf
        }
    }
}
```
Hier wird die Punktzahl in eine Bewertung umgewandelt, basierend auf den gegebenen Bedingungen.

## Erklärung
Eine häufige Falle beim Arbeiten mit "else" ist die falsche Anordnung von Bedingungen. Entwickler sollten sicherstellen, dass die Bedingungen in der richtigen Reihenfolge geprüft werden und dass alle möglichen Fälle abgedeckt sind. Ein weiterer Punkt ist, dass der Code im "else"-Block nur ausgeführt wird, wenn die "if"-Bedingung falsch ist - dies kann zu unerwarteten Ergebnissen führen, wenn die Logik nicht sorgfältig durchdacht wird.

### Zusätzliche Hinweise
- Die Verwendung von geschachtelten "if-else"-Anweisungen kann den Code komplizierter machen. Es ist ratsam, die Lesbarkeit des Codes zu priorisieren.
- Achten Sie darauf, die Bedingungen klar und prägnant zu formulieren, um Missverständnisse zu vermeiden.

## Ein-Satz-Zusammenfassung
Das "else"-Schlüsselwort in Solidity ermöglicht es Entwicklern, alternative Ausführungspfade in bedingten Anweisungen zu definieren, wodurch die Logik von Smart Contracts flexibler gestaltet wird.