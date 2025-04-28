<!--
Meta Description: # Fehlerbehandlung in Solidity: Der „error“-Befehl ## Synopsis Der „error“-Befehl in Solidity ist ein wichtiges Werkzeug zur Definition benutzerdefini...
Meta Keywords: solidity, der, fehler, error, die
-->

# Fehlerbehandlung in Solidity: Der „error“-Befehl

## Synopsis
Der „error“-Befehl in Solidity ist ein wichtiges Werkzeug zur Definition benutzerdefinierter Fehler, die in Smart Contracts verwendet werden, um spezifische Fehlermeldungen zu erzeugen und die Fehlerbehandlung zu verbessern.

## Dokumentation
In Solidity ist der „error“-Befehl eine Möglichkeit, benutzerdefinierte Fehler zu definieren, die in Smart Contracts geworfen werden können. Dies ermöglicht Entwicklern, klarere und präzisere Fehlermeldungen zu erstellen. Der Einsatz von „errors“ ist besonders vorteilhaft, da sie gas-effizient sind und die Lesbarkeit des Codes verbessern.

### Zweck
Der Hauptzweck des „error“-Befehls besteht darin, spezifische Fehlerzustände zu kennzeichnen, die während der Ausführung eines Smart Contracts auftreten können. Anstatt allgemeine Fehler wie „require failed“ zu verwenden, können Entwickler spezifische Fehler definieren, die mehr Kontext bieten.

### Verwendung
Um einen benutzerdefinierten Fehler in Solidity zu definieren, verwenden Sie die Syntax:
```solidity
error ErrorName(string message);
```
Nach der Definition kann der Fehler im Code wie folgt ausgelöst werden:
```solidity
errorName("Fehlermeldung");
```

## Beispiele
Hier sind einige grundlegende Beispiele zur Verwendung von „errors“ in Solidity:

### Beispiel 1: Einfacher Fehler
```solidity
pragma solidity ^0.8.0;

contract Beispiel {
    error Unauthorized(string message);

    function nurAdministrator() public {
        if (msg.sender != owner) {
            revert Unauthorized("Zugang verweigert: Nur Administratoren dürfen diesen Befehl ausführen.");
        }
    }
}
```

### Beispiel 2: Fehler mit Daten
```solidity
pragma solidity ^0.8.0;

contract Beispiel {
    error BetragZuHoch(uint256 requested, uint256 available);

    function abheben(uint256 amount) public {
        uint256 availableBalance = getBalance(msg.sender);
        if (amount > availableBalance) {
            revert BetragZuHoch(amount, availableBalance);
        }
        // Logik zum Abheben
    }
}
```

## Erklärung
Ein häufiges Problem bei der Verwendung des „error“-Befehls ist das Vergessen, den Fehler mit der `revert`-Anweisung auszulösen. Entwickler sollten sicherstellen, dass sie den Fehler in den Bedingungen korrekt überprüfen und auslösen. Ein weiterer Punkt ist, dass benutzerdefinierte Fehler in neueren Versionen von Solidity eingeführt wurden, daher sollte darauf geachtet werden, dass die verwendete Version diese Funktion unterstützt.

## Einzeilige Zusammenfassung
Der „error“-Befehl in Solidity ermöglicht die Definition von benutzerdefinierten Fehlern für eine präzisere und effizientere Fehlerbehandlung in Smart Contracts.