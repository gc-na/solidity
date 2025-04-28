<!--
Meta Description: # Der "new"-Befehl in Solidity: Instanziierung von Verträgen und Strukturen ## Synopsis Der `new`-Befehl in Solidity wird verwendet, um neue Instanzen...
Meta Keywords: der, new, die, befehl, von
-->

# Der "new"-Befehl in Solidity: Instanziierung von Verträgen und Strukturen

## Synopsis
Der `new`-Befehl in Solidity wird verwendet, um neue Instanzen von Verträgen oder Strukturen zu erstellen. Dies ist ein grundlegendes Konzept in der objektorientierten Programmierung und spielt eine zentrale Rolle in der Funktionsweise von Smart Contracts auf der Ethereum-Blockchain.

## Dokumentation
Der `new`-Befehl ermöglicht es Entwicklern, neue Instanzen von Verträgen oder Datenstrukturen zu generieren. Dies ist wichtig, um mehrere separate Kopien eines bestimmten Vertrages oder einer Struktur zu erstellen, die unabhängig voneinander interagieren können.

### Zweck
- **Instanziierung**: Erstellen neuer Objekte (Verträge oder Strukturen).
- **Speicherverwaltung**: Der `new`-Befehl reserviert Speicher für die neue Instanz im Ethereum-Netzwerk.

### Verwendung
Der `new`-Befehl wird typischerweise in der Funktion oder dem Konstruktor eines bestehenden Vertrages verwendet. Die allgemeine Syntax lautet:

```solidity
ContractName instanceName = new ContractName(arguments);
```

Hierbei ist `ContractName` der Name des Vertrages, `instanceName` der Name der neuen Instanz, und `arguments` sind die Parameter, die gegebenenfalls an den Konstruktor des Vertrages übergeben werden.

### Details
- Eine Instanz eines Vertrages wird im Ethereum-Speicher angelegt und erhält eine einzigartige Adresse.
- Der `new`-Befehl kann nicht verwendet werden, um bestehende Instanzen zu verändern; jede Instanz ist unabhängig.
- Die Erstellung von Instanzen kann Gas kosten, und die Höhe der Kosten hängt von der Komplexität des Vertrages ab.

## Beispiele
### Beispiel 1: Erstellen einer neuen Vertragsinstanz
```solidity
pragma solidity ^0.8.0;

contract Sample {
    uint public value;

    constructor(uint _value) {
        value = _value;
    }
}

contract Factory {
    Sample public sampleInstance;

    function createSample(uint _value) public {
        sampleInstance = new Sample(_value);
    }
}
```
In diesem Beispiel erstellt der `Factory`-Vertrag eine neue Instanz des `Sample`-Vertrags mit einem spezifischen Wert.

### Beispiel 2: Erstellen von Strukturen
```solidity
pragma solidity ^0.8.0;

contract StructureExample {
    struct Person {
        string name;
        uint age;
    }

    Person public person;

    function createPerson(string memory _name, uint _age) public {
        person = Person(_name, _age);
    }
}
```
Hier wird eine Struktur erstellt, ohne den `new`-Befehl, aber es zeigt, wie eine Instanz einer Struktur innerhalb des Vertrags definiert werden kann.

## Erklärung
- **Häufige Fallstricke**: Ein häufiger Fehler ist die Annahme, dass der `new`-Befehl in jedem Kontext verwendet werden kann. Er kann nur innerhalb von Funktionen oder Konstruktoren aufgerufen werden.
- **Speicher vs. Speicher**: Bei der Verwendung des `new`-Befehls wird der Speicher im Ethereum-Netzwerk belegt, was bedeutet, dass jede Instanz mit Kosten verbunden ist.
- **Sichtbarkeit**: Stellt sicher, dass die Sichtbarkeit der Variablen und Funktionen klar definiert ist, um unerwünschte Zugriffe zu vermeiden.

## Ein-Satz-Zusammenfassung
Der `new`-Befehl in Solidity wird verwendet, um neue Instanzen von Verträgen oder Strukturen zu erstellen, die im Ethereum-Netzwerk unabhängig operieren.