<!--
Meta Description: # Strukturen in Solidity: Definition, Verwendung und Beispiele ## Synopsis In Solidity sind Strukturen (structs) benutzerdefinierte Datentypen, die es...
Meta Keywords: solidity, strukturen, und, die, benutzer
-->

# Strukturen in Solidity: Definition, Verwendung und Beispiele

## Synopsis
In Solidity sind Strukturen (structs) benutzerdefinierte Datentypen, die es Entwicklern ermöglichen, mehrere Variablen unter einem einzigen Namen zu gruppieren, was die Organisation und Verwaltung von Daten vereinfacht.

## Dokumentation
Strukturen in Solidity dienen dazu, komplexe Datentypen zu erstellen, die aus verschiedenen primitiven Datentypen und anderen Strukturen bestehen können. Sie sind besonders nützlich, um Daten zusammenzufassen, die logisch zusammengehören. Zum Beispiel kann eine Struktur verwendet werden, um Informationen über einen Benutzer, einen Vertrag oder ein Produkt zu speichern.

### Definition einer Struktur
Eine Struktur wird mit dem Schlüsselwort `struct` definiert. Hier ist die grundlegende Syntax:

```solidity
struct StrukturName {
    Datentyp1 variable1;
    Datentyp2 variable2;
    ...
}
```

### Verwendung von Strukturen
Nachdem eine Struktur definiert wurde, kann sie instanziiert und verwendet werden. Strukturen können auch in Arrays gespeichert oder in Mapping-Datenstrukturen verwendet werden. 

#### Beispiel für eine Strukturdefinition:
```solidity
struct Benutzer {
    uint id;
    string name;
    address konto;
}
```

Sie können dann eine Variable vom Typ `Benutzer` erstellen:

```solidity
Benutzer public benutzer1 = Benutzer(1, "Max Mustermann", 0x1234567890abcdef1234567890abcdef12345678);
```

## Beispiele
Hier sind einige grundlegende Beispiele für die Verwendung von Strukturen in Solidity:

### Beispiel 1: Definition und Instanziierung
```solidity
pragma solidity ^0.8.0;

contract BenutzerVerwaltung {
    struct Benutzer {
        uint id;
        string name;
        address konto;
    }
    
    Benutzer public benutzer1;

    function setBenutzer(uint _id, string memory _name, address _konto) public {
        benutzer1 = Benutzer(_id, _name, _konto);
    }
}
```

### Beispiel 2: Verwendung von Arrays von Strukturen
```solidity
pragma solidity ^0.8.0;

contract ProduktVerwaltung {
    struct Produkt {
        string name;
        uint preis;
    }

    Produkt[] public produkte;

    function addProdukt(string memory _name, uint _preis) public {
        produkte.push(Produkt(_name, _preis));
    }
}
```

## Erklärung
Ein häufiges Problem beim Arbeiten mit Strukturen ist die Verwaltung des Speichers. In Solidity gibt es zwei Arten von Speicher: `storage` und `memory`. Variablen in `storage` sind dauerhaft und werden auf der Blockchain gespeichert, während `memory` temporär ist und nur während der Ausführung einer Funktion existiert. Dies kann zu Verwirrung führen, wenn Sie Strukturen als Parameter oder Rückgabewerte verwenden. 

Ein weiterer Punkt ist, dass Strukturen nicht in `mapping` verwendet werden können, um auf ihre Mitglieder direkt zuzugreifen. Sie müssen zuerst eine Instanz der Struktur erstellen, bevor Sie auf die einzelnen Mitglieder zugreifen können.

## Ein-Satz-Zusammenfassung
Strukturen in Solidity sind leistungsstarke benutzerdefinierte Datentypen, die es Entwicklern ermöglichen, mehrere verwandte Variablen in einer einzigen Einheit zu organisieren und zu verwalten.