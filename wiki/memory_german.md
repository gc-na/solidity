<!--
Meta Description: # Speicher in Solidity: Ein umfassender Leitfaden ## Synopsis In Solidity ist der "Speicher" (memory) ein dynamischer Datenspeicher, der zur temporäre...
Meta Keywords: der, speicher, ist, von, solidity
-->

# Speicher in Solidity: Ein umfassender Leitfaden

## Synopsis
In Solidity ist der "Speicher" (memory) ein dynamischer Datenspeicher, der zur temporären Speicherung von Daten während der Ausführung von Smart Contracts verwendet wird. Er ist flüchtig und wird gelöscht, sobald die Ausführung eines Funktionsaufrufs beendet ist.

## Dokumentation
### Zweck
Der Speicher in Solidity dient dazu, Daten temporär während der Ausführung von Funktionen zu speichern. Im Gegensatz zu "storage", wo Daten dauerhaft auf der Blockchain gespeichert werden, ist der Speicher kostengünstiger und schneller, jedoch flüchtig.

### Nutzung
Um den Speicher in Solidity zu verwenden, kann man ihn in Funktionsparametern oder lokal in der Funktion deklarieren. Der Speicher ist ideal für Arrays, Strukturen oder andere komplexe Datentypen, die nur während der Ausführung benötigt werden.

### Details
- **Deklaration**: Variablen, die im Speicher gespeichert werden, werden mit dem Schlüsselwort `memory` deklariert.
- **Lebensdauer**: Daten im Speicher existieren nur während der Ausführung der Funktion und werden danach verworfen.
- **Kosten**: Die Nutzung von Speicher ist in der Regel kostengünstiger als die Verwendung von "storage", jedoch teurer als die Verwendung von "stack", der für primitive Datentypen verwendet wird.

## Beispiele
### Beispiel 1: Verwendung von `memory` mit Arrays
```solidity
pragma solidity ^0.8.0;

contract MemoryExample {
    function createArray() public pure returns (uint[] memory) {
        uint[] memory tempArray = new uint[](3);
        tempArray[0] = 1;
        tempArray[1] = 2;
        tempArray[2] = 3;
        return tempArray;
    }
}
```

### Beispiel 2: Verwendung von `memory` mit Strukturen
```solidity
pragma solidity ^0.8.0;

contract StructExample {
    struct Person {
        string name;
        uint age;
    }
    
    function createPerson() public pure returns (Person memory) {
        Person memory newPerson = Person("Alice", 30);
        return newPerson;
    }
}
```

## Erklärung
Ein häufiges Missverständnis bei der Verwendung von `memory` ist die Annahme, dass die Daten dauerhaft gespeichert werden. Es ist wichtig zu beachten, dass alle im Speicher deklarierten Daten sofort nach dem Abschluss der Funktion gelöscht werden. Ein weiterer wichtiger Punkt ist, dass komplexe Datentypen, die im Speicher verwendet werden, nicht wie in "storage" referenziert werden können, was zu Verwirrung führen kann.

## Zusammenfassung in einem Satz
Der Speicher in Solidity ist ein flüchtiger Datenspeicher, der zur temporären Speicherung von Daten während der Ausführung von Funktionen verwendet wird und ideal für Arrays und Strukturen ist.