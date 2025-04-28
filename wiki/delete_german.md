<!--
Meta Description: # Das "delete"-Keyword in Solidity: Alles, was Sie wissen müssen ## Synopsis Das "delete"-Keyword in Solidity wird verwendet, um Speicherplatz freizug...
Meta Keywords: delete, das, solidity, auf, wird
-->

# Das "delete"-Keyword in Solidity: Alles, was Sie wissen müssen

## Synopsis
Das "delete"-Keyword in Solidity wird verwendet, um Speicherplatz freizugeben und Variablen auf ihren Standardwert zurückzusetzen. Es ist ein wichtiges Werkzeug für die Verwaltung von Speicher in Smart Contracts.

## Dokumentation
Das "delete"-Keyword wird in Solidity verwendet, um den Zustand einer Variablen zurückzusetzen und den zugehörigen Speicherplatz freizugeben. Wenn Sie "delete" auf eine Variable anwenden, wird deren Wert auf den Standardwert des Typs zurückgesetzt. Für primitive Datentypen wie `uint`, `bool` oder `address` bedeutet dies, dass sie auf `0`, `false` bzw. die Nulladresse zurückgesetzt werden. Für komplexe Datentypen wie Arrays oder Strukturen wird der gesamte Inhalt gelöscht.

### Verwendung
Das "delete"-Keyword kann auf verschiedene Datentypen angewendet werden:

- **Primitive Datentypen**: Reset auf den Standardwert.
- **Arrays**: Löschen aller Elemente.
- **Structs**: Alle Felder werden auf ihren Standardwert zurückgesetzt.
- **Mappings**: Löschen aller Zuordnungen zu einem Schlüssel.

### Details
- **Speicher**: Das "delete"-Keyword ist besonders nützlich bei der Arbeit mit Speicher und der Vermeidung von Speicherlecks.
- **Gas-Kosten**: Das Löschen von Variablen kann Gas sparen, da nicht mehr benötigter Speicher freigegeben wird.
- **Einschränkungen**: Das "delete"-Keyword kann nicht auf Konstanten oder unveränderliche Variablen angewendet werden.

## Beispiele
Hier sind einige grundlegende Anwendungsbeispiele für das "delete"-Keyword in Solidity:

### Beispiel 1: Löschen eines primitiven Typs
```solidity
pragma solidity ^0.8.0;

contract Example {
    uint public value = 10;

    function resetValue() public {
        delete value; // value wird auf 0 zurückgesetzt
    }
}
```

### Beispiel 2: Löschen eines Arrays
```solidity
pragma solidity ^0.8.0;

contract Example {
    uint[] public numbers;

    function addNumber(uint _number) public {
        numbers.push(_number);
    }

    function clearNumbers() public {
        delete numbers; // Das Array wird geleert
    }
}
```

### Beispiel 3: Löschen eines Structs
```solidity
pragma solidity ^0.8.0;

contract Example {
    struct Person {
        string name;
        uint age;
    }

    Person public person;

    function setPerson(string memory _name, uint _age) public {
        person = Person(_name, _age);
    }

    function resetPerson() public {
        delete person; // Alle Felder werden auf ihre Standardwerte zurückgesetzt
    }
}
```

## Erklärung
Beim Einsatz des "delete"-Keywords sollte darauf geachtet werden, dass es zu unerwarteten Ergebnissen führen kann, wenn es nicht korrekt verwendet wird. Besonders bei Arrays kann das Löschen den gesamten Inhalt entfernen, was nicht immer gewünscht ist. Außerdem wird bei der Verwendung in Mappings der gesamte Eintrag gelöscht, was die Datenintegrität gefährden kann, wenn nicht richtig verwaltet.

Ein häufiges Missverständnis ist, dass das "delete"-Keyword nicht den Speicherplatz sofort freigibt, sondern lediglich die Werte zurücksetzt. Der freigegebene Speicher wird erst bei der nächsten Garbage Collection durch die Ethereum Virtual Machine (EVM) verarbeitet.

## Ein Satz Zusammenfassung
Das "delete"-Keyword in Solidity dient dazu, Variablen auf ihren Standardwert zurückzusetzen und Speicherplatz effizient zu verwalten.