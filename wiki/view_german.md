<!--
Meta Description: # Solidity "view" Modifikator: Alles, was Sie wissen müssen ## Synopsis Der "view" Modifikator in Solidity kennzeichnet Funktionen, die den Zustand de...
Meta Keywords: die, view, der, solidity, den
-->

# Solidity "view" Modifikator: Alles, was Sie wissen müssen

## Synopsis
Der "view" Modifikator in Solidity kennzeichnet Funktionen, die den Zustand des Smart Contracts lesen, jedoch nicht verändern. Diese Funktionalität ist entscheidend, um die Effizienz und Sicherheit von Smart Contracts zu gewährleisten.

## Dokumentation
### Zweck
Der "view" Modifikator wird verwendet, um Funktionen in Solidity zu definieren, die Daten aus dem Zustand eines Smart Contracts abrufen, ohne diesen direkt zu ändern. Solche Funktionen können als Leseoperationen betrachtet werden und sind wichtig für die Interaktion mit Smart Contracts, da sie es Benutzern ermöglichen, Informationen abzufragen, ohne Transaktionen auszuführen, die Gas kosten.

### Verwendung
Um eine Funktion als "view" zu kennzeichnen, wird der Modifikator vor der Funktionsdeklaration platziert. Hier ist die allgemeine Syntax:

```solidity
function functionName() public view returns (returnType) {
    // Funktion Body
}
```

In diesem Beispiel ist `functionName` der Name der Funktion, und `returnType` gibt den Datentyp des Wertes an, den die Funktion zurückgibt.

### Details
- **Gas-Kosten**: Funktionen, die mit dem "view" Modifikator gekennzeichnet sind, erfordern keine Gas-Kosten, wenn sie lokal im Ethereum-Netzwerk aufgerufen werden. Sie können jedoch Gas kosten, wenn sie über Transaktionen aufgerufen werden, die den Zustand des Netzwerks ändern.
- **Zugriffsmodifizierer**: "view" kann mit anderen Zugriffsmodifizierern wie "public" oder "private" kombiniert werden, um die Sichtbarkeit der Funktion zu steuern.
- **Rückgabewerte**: Funktionen mit dem "view" Modifikator können Werte zurückgeben, die auf den aktuellen Status des Vertrags basieren.

## Beispiele
Hier sind einige einfache Beispiele zur Veranschaulichung der Verwendung des "view" Modifikators:

### Beispiel 1: Abrufen eines Wertes
```solidity
pragma solidity ^0.8.0;

contract SimpleStorage {
    uint256 private storedData;

    function set(uint256 x) public {
        storedData = x;
    }

    function get() public view returns (uint256) {
        return storedData;
    }
}
```
In diesem Beispiel speichert die Funktion `set` einen Wert, während `get` den gespeicherten Wert zurückgibt, ohne ihn zu ändern.

### Beispiel 2: Komplexere Rückgaben
```solidity
pragma solidity ^0.8.0;

contract UserRegistry {
    struct User {
        string name;
        uint age;
    }

    mapping(address => User) private users;

    function register(string memory _name, uint _age) public {
        users[msg.sender] = User(_name, _age);
    }

    function getUser() public view returns (string memory, uint) {
        User memory user = users[msg.sender];
        return (user.name, user.age);
    }
}
```
Hier wird die Funktion `getUser` verwendet, um die Details eines registrierten Benutzers abzurufen.

## Erklärung
Eine häufige Falle bei der Verwendung des "view" Modifikators ist das Versehen, den Status des Smart Contracts zu ändern, während man glaubt, in einer "view" Funktion zu arbeiten. Funktionen, die den Zustand verändern, müssen als "non-payable" oder "pure" deklariert werden, um korrekt zu funktionieren. 

Ein weiterer Punkt ist, sicherzustellen, dass die Funktion tatsächlich nur Leseoperationen durchführt. Andernfalls könnte der Compiler einen Fehler ausgeben, wenn Änderungen am Zustand erkannt werden.

## Ein Satz Zusammenfassung
Der "view" Modifikator in Solidity ermöglicht es, Funktionen zu definieren, die den Zustand eines Smart Contracts lesen, ohne diesen zu verändern.