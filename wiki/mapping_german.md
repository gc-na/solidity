<!--
Meta Description: # Mapping in Solidity: Ein umfassender Leitfaden für Entwickler ## Synopsis Mappings in Solidity sind eine leistungsstarke Funktion, die es Entwickler...
Meta Keywords: solidity, ein, der, mapping, sie
-->

# Mapping in Solidity: Ein umfassender Leitfaden für Entwickler

## Synopsis
Mappings in Solidity sind eine leistungsstarke Funktion, die es Entwicklern ermöglicht, Daten in Form von Schlüssel-Wert-Paaren zu speichern, wobei der Schlüssel ein beliebiger Datentyp und der Wert ebenfalls ein beliebiger Datentyp sein kann.

## Dokumentation
Mappings sind eine der zentralen Datenstrukturen in Solidity, die verwendet werden, um assoziative Arrays zu erstellen. Sie ermöglichen eine effiziente und flexible Speicherung und den Zugriff auf Daten. Ein Mapping in Solidity wird definiert, indem der Schlüsseltyp und der Werttyp angegeben werden. Die Syntax lautet:

```solidity
mapping (Schlüsseltyp => Werttyp) public name;
```

### Zweck
Mappings dienen dazu, Daten unkompliziert zu speichern und abzurufen, indem sie einer bestimmten Adresse oder einem bestimmten Identifikator einen Wert zuweisen. Dies ist besonders nützlich in Szenarien wie der Speicherung von Salden, Benutzerinformationen oder anderen dynamischen Daten.

### Verwendung
Ein Mapping kann in einem Vertrag wie folgt deklariert werden:

```solidity
pragma solidity ^0.8.0;

contract Beispiel {
    mapping(address => uint) public salden;

    function einzahlen() public payable {
        salden[msg.sender] += msg.value;
    }

    function abheben(uint _betrag) public {
        require(salden[msg.sender] >= _betrag, "Unzureichender Saldo!");
        salden[msg.sender] -= _betrag;
        payable(msg.sender).transfer(_betrag);
    }
}
```

In diesem Beispiel wird ein Mapping verwendet, um die Salden von Benutzern zu verfolgen.

## Beispiele
Hier sind einige einfache Beispiele zur Veranschaulichung der Verwendung von Mappings:

1. **Speicherung von Benutzerpunkten:**
   ```solidity
   mapping(address => uint) public punkte;

   function punkteHinzufuegen(address _benutzer, uint _punkteZuHinzufuegen) public {
       punkte[_benutzer] += _punkteZuHinzufuegen;
   }
   ```

2. **Zugriff auf Werte:**
   ```solidity
   function getPunkte(address _benutzer) public view returns (uint) {
       return punkte[_benutzer];
   }
   ```

## Erklärung
Ein häufiger Fallstrick bei der Verwendung von Mappings ist, dass sie nicht iterierbar sind. Das bedeutet, dass Sie nicht durch alle Schlüssel oder Werte in einem Mapping iterieren können. Wenn Sie alle Adressen oder Werte speichern möchten, sollten Sie zusätzlich ein Array oder eine andere Datenstruktur verwenden.

Ein weiterer Punkt ist, dass Mappings in Solidity standardmäßig den Wert `0` für numerische Typen oder die "leere" Form für Referenztypen zurückgeben, wenn der Schlüssel nicht existiert. Entwickler müssen sicherstellen, dass sie entsprechende Überprüfungen durchführen, bevor sie auf Werte zugreifen.

## Ein-Satz-Zusammenfassung
Mappings in Solidity bieten eine effiziente Methode zur Speicherung und zum Zugriff auf Daten in Form von Schlüssel-Wert-Paaren, sind jedoch nicht iterierbar und erfordern besondere Beachtung bei der Handhabung nicht existierender Schlüssel.