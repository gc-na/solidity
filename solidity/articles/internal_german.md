<!--
Meta Description: # "internal" in Solidity: Zugriffssichtbarkeit für Smart Contracts ## Synopsis In Solidity bezeichnet der Schlüsselbegriff "internal" eine Zugriffsart...
Meta Keywords: internal, und, die, von, eine
-->

# "internal" in Solidity: Zugriffssichtbarkeit für Smart Contracts

## Synopsis
In Solidity bezeichnet der Schlüsselbegriff "internal" eine Zugriffsart, die für Funktionen und Variablen innerhalb eines Smart Contracts oder in abgeleiteten Verträgen zugänglich ist. Diese Sichtbarkeit ist entscheidend für die Strukturierung von Smart Contracts und spielt eine wichtige Rolle bei der Sicherheit und Modularität.

## Dokumentation
Die Sichtbarkeit "internal" ist eine der vier verfügbaren Sichtbarkeiten in Solidity, neben "public", "private" und "external". Sie definiert, wie und wo eine Funktion oder Variable aufgerufen werden kann:

- **Zweck**: Die "internal"-Sichtbarkeit ermöglicht es, auf Funktionen und Variablen nur innerhalb des aktuellen Vertrags und durch abgeleitete Verträge zuzugreifen. Dies schützt sensible Daten und Logik vor unberechtigtem Zugriff.
  
- **Verwendung**: Um eine Funktion oder Variable als "internal" zu deklarieren, verwenden Sie das Schlüsselwort `internal` vor der Funktions- oder Variablendeklaration. Wenn keine Sichtbarkeit angegeben wird, ist die Standard-Sichtbarkeit "internal".

- **Details**: 
  - **Funktionen**: Eine als "internal" deklarierte Funktion kann von anderen Funktionen im gleichen Vertrag oder von Funktionen in abgeleiteten Verträgen aufgerufen werden.
  - **Variablen**: Eine "internal"-Variable kann ebenfalls innerhalb des Vertrags und in abgeleiteten Verträgen verwendet werden.
  - **Erbschaft**: Abgeleitete Verträge (Verträge, die von einem anderen Vertrag erben) können auf "internal"-Elemente des Basisvertrags zugreifen, was eine flexible und erweiterbare Architektur ermöglicht.

## Beispiele
Hier sind einige grundlegende Beispiele zur Verwendung von "internal":

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract BasisContract {
    uint internal zahl;

    function setZahl(uint _zahl) internal {
        zahl = _zahl;
    }
}

contract AbleitenderVertrag is BasisContract {
    function updateZahl(uint _zahl) public {
        setZahl(_zahl); // Zugriff auf die interne Funktion
    }

    function getZahl() public view returns (uint) {
        return zahl; // Zugriff auf die interne Variable
    }
}
```

## Erklärung
Ein häufiges Missverständnis ist, dass "internal"-Elemente von außerhalb des Vertrags oder von nicht abgeleiteten Verträgen aus zugänglich sind. Das ist nicht der Fall; "internal" schützt vor externem Zugriff. Weitere Punkte, die zu beachten sind:

- **Sicherheit**: Die Verwendung von "internal" kann die Sicherheit Ihres Smart Contracts erhöhen, da unerwünschte Interaktionen von externen Verträgen ausgeschlossen werden.
- **Standard-Sichtbarkeit**: Denken Sie daran, dass bei fehlender Angabe der Sichtbarkeit die Funktionen und Variablen standardmäßig als "internal" behandelt werden, was potenziell zu unbeabsichtigtem Zugriff führen kann, wenn dies nicht beabsichtigt ist.

## Ein-Satz-Zusammenfassung
Das Schlüsselwort "internal" in Solidity definiert den Zugriff auf Funktionen und Variablen innerhalb eines Vertrags und in abgeleiteten Verträgen und schützt somit vor externem Zugriff.