<!--
Meta Description: # Das Schlüsselwort "external" in Solidity: Eine detaillierte Übersicht ## Synopsis Das Schlüsselwort "external" in Solidity ermöglicht es Smart Contr...
Meta Keywords: external, die, werden, funktion, solidity
-->

# Das Schlüsselwort "external" in Solidity: Eine detaillierte Übersicht

## Synopsis
Das Schlüsselwort "external" in Solidity ermöglicht es Smart Contracts, Funktionen zu definieren, die nur von externen Konten oder anderen Verträgen aufgerufen werden können. Es spielt eine wesentliche Rolle bei der Sichtbarkeit und Interaktion zwischen verschiedenen Verträgen.

## Dokumentation
In Solidity wird das Keyword "external" verwendet, um die Sichtbarkeit von Funktionen zu definieren. Eine Funktion, die als "external" deklariert ist, kann nur von außen aufgerufen werden, d.h. von anderen Verträgen oder externen Konten. Es ist wichtig zu beachten, dass "external" Funktionen nicht innerhalb des gleichen Vertrags aufgerufen werden können; stattdessen muss eine interne Funktion verwendet werden.

### Zweck
Der Hauptzweck der Verwendung von "external" ist es, die Interaktion zwischen Smart Contracts zu steuern und den Zugriff auf Funktionen zu beschränken. Dies erhöht die Sicherheit und ermöglicht eine klare Trennung zwischen internen und externen Aufrufen.

### Verwendung
Um eine Funktion als "external" zu deklarieren, wird das Schlüsselwort vor der Funktionsdefinition platziert. Hier ist ein einfaches Beispiel:

```solidity
pragma solidity ^0.8.0;

contract Beispiel {
    uint public wert;

    function setWert(uint _wert) external {
        wert = _wert;
    }
}
```

In diesem Beispiel kann die Funktion `setWert` nur von externen Konten oder anderen Verträgen aufgerufen werden.

## Beispiele
Hier sind einige grundlegende Beispiele für die Verwendung des "external"-Schlüsselworts:

### Beispiel 1: Einfache externe Funktion
```solidity
pragma solidity ^0.8.0;

contract ExterneFunktion {
    uint public zahl;

    function setZahl(uint _zahl) external {
        zahl = _zahl;
    }
}
```

### Beispiel 2: Externe Funktion mit Rückgabe
```solidity
pragma solidity ^0.8.0;

contract ExterneFunktionMitRückgabe {
    uint private wert;

    function setWert(uint _wert) external {
        wert = _wert;
    }

    function getWert() external view returns (uint) {
        return wert;
    }
}
```

## Erklärung
### Häufige Fallstricke
1. **Interne Aufrufe**: Eine externe Funktion kann nicht innerhalb des gleichen Vertrags über ihren Namen aufgerufen werden. Stattdessen sollte eine interne Funktion verwendet werden.
2. **Gas-Kosten**: Externe Funktionen verbrauchen in der Regel mehr Gas, wenn sie von einem anderen Vertrag aufgerufen werden, da sie den Aufruf über die EVM (Ethereum Virtual Machine) abwickeln müssen.
3. **Sichtbarkeit**: Es ist wichtig, die Sichtbarkeit der Funktionen zu verstehen. Verwenden Sie "external" nur, wenn Sie sicher sind, dass die Funktion nicht von anderen Funktionen innerhalb desselben Vertrags aufgerufen werden soll.

### Zusätzliche Hinweise
- Externe Funktionen sollten verwendet werden, wenn Sie sicherstellen möchten, dass die Funktion nur von außen aufgerufen wird, was die Sicherheit erhöhen kann.
- In bestimmten Fällen kann es vorteilhaft sein, eine Funktion sowohl als "external" als auch als "public" zu deklarieren, um maximale Flexibilität zu bieten.

## Ein-Satz-Zusammenfassung
Das Schlüsselwort "external" in Solidity definiert Funktionen, die nur von externen Konten oder anderen Verträgen aufgerufen werden können, wodurch die Interaktion zwischen Smart Contracts geregelt wird.