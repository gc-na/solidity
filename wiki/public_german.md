<!--
Meta Description: # Das Schlüsselwort "public" in Solidity: Eine umfassende Anleitung ## Synopsis In Solidity ist das Schlüsselwort "public" ein Zugriffsmodifikator, de...
Meta Keywords: public, die, von, und, solidity
-->

# Das Schlüsselwort "public" in Solidity: Eine umfassende Anleitung

## Synopsis
In Solidity ist das Schlüsselwort "public" ein Zugriffsmodifikator, der es ermöglicht, dass Funktionen und Variablen von überall im Smart Contract und externen Aufrufer zugänglich sind. Es spielt eine entscheidende Rolle für die Sichtbarkeit und Interaktion in Smart Contracts.

## Dokumentation
Das "public"-Schlüsselwort wird verwendet, um die Sichtbarkeit von Funktionen und Variablen in Solidity zu definieren. 

### Zweck
Der Hauptzweck von "public" besteht darin, die Interaktion mit Smart Contracts zu ermöglichen und die Zugänglichkeit von bestimmten Funktionen und Variablen zu steuern. 

### Verwendung
- **Funktionen**: Eine als "public" deklarierte Funktion kann von anderen Verträgen sowie von externen Konten aufgerufen werden.
- **Variablen**: Bei Variablen wird eine "public" deklarierte Variable automatisch mit einer Getter-Funktion versehen, die es ermöglicht, ihren Wert von außerhalb des Smart Contracts abzurufen.

### Details
- Wenn eine Funktion als "public" deklariert ist, kann sie von jedem aufgerufen werden, der die Adresse des Smart Contracts hat.
- "public" ist eine der vier Sichtbarkeitsebenen in Solidity, neben "private", "internal" und "external".
- Es ist wichtig zu beachten, dass "public" nicht für alle Typen von Datenstrukturen empfohlen wird, da dies die Sicherheit des Contracts gefährden könnte.

## Beispiele
### Beispiel 1: Öffentliche Funktion
```solidity
pragma solidity ^0.8.0;

contract Example {
    uint public value;

    function setValue(uint _value) public {
        value = _value;
    }
}
```
In diesem Beispiel kann die Funktion `setValue` von jedem aufgerufen werden, um den Wert der Variablen `value` zu setzen.

### Beispiel 2: Öffentliches Variablen-Getter
```solidity
pragma solidity ^0.8.0;

contract Example {
    uint public count;

    function increment() public {
        count++;
    }
}
```
Hier wird ein Getter für die Variable `count` automatisch generiert, sodass Benutzer den aktuellen Wert von `count` abfragen können.

## Erklärung
Ein häufiges Missverständnis besteht darin, dass "public" immer die beste Wahl für die Sichtbarkeit ist. In vielen Fällen sollten Funktionen und Variablen, die nicht für die öffentliche Nutzung bestimmt sind, als "private" oder "internal" deklariert werden, um Sicherheitsrisiken zu minimieren. Zudem kann die Verwendung von "public" zu höheren Gasgebühren führen, wenn öffentliche Funktionen von externen Konten aufgerufen werden, da diese Aufrufe oft teurer sind als interne Aufrufe.

## Ein-Satz-Zusammenfassung
Das "public"-Schlüsselwort in Solidity ermöglicht die öffentliche Zugänglichkeit von Funktionen und Variablen und spielt eine zentrale Rolle bei der Interaktion in Smart Contracts.