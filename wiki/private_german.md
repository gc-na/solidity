<!--
Meta Description: # Private: Sichtbarkeit von Variablen in Solidity ## Synopsis In Solidity ist das Schlüsselwort `private` ein Zugriffsmodifikator, der sicherstellt, d...
Meta Keywords: private, funktionen, oder, die, und
-->

# Private: Sichtbarkeit von Variablen in Solidity

## Synopsis
In Solidity ist das Schlüsselwort `private` ein Zugriffsmodifikator, der sicherstellt, dass bestimmte Variablen oder Funktionen nur innerhalb des Vertrags, in dem sie deklariert sind, zugänglich sind. Dies fördert die Kapselung und schützt sensible Daten vor unbefugtem Zugriff.

## Documentation
Das Schlüsselwort `private` wird verwendet, um die Sichtbarkeit von Variablen und Funktionen zu steuern. In Solidity gibt es mehrere Sichtbarkeitsmodifikatoren: `public`, `internal`, `private` und `external`. 

- **Zweck**: Der Hauptzweck von `private` ist die Sicherheit. Durch die Verwendung von `private` können Entwickler sicherstellen, dass bestimmte Funktionen oder Variablen nicht von anderen Verträgen oder externen Benutzern aufgerufen oder verändert werden können.
  
- **Verwendung**: Um eine Variable oder Funktion als `private` zu deklarieren, wird das Schlüsselwort vor der Deklaration platziert. Private Daten sind nur innerhalb des Vertrags sichtbar und nicht in abgeleiteten Verträgen oder außerhalb des Vertrags zugänglich.

- **Details**: Der `private` Modifikator kann sowohl für Zustandsvariablen als auch für Funktionen verwendet werden. Private Funktionen können nur von anderen Funktionen innerhalb desselben Vertrags aufgerufen werden.

## Examples
Hier sind einige grundlegende Beispiele für die Verwendung von `private` in Solidity:

```solidity
pragma solidity ^0.8.0;

contract Beispiel {
    // Private Variable
    uint private geheimeZahl;

    // Konstruktor
    constructor(uint _geheimeZahl) {
        geheimeZahl = _geheimeZahl;
    }

    // Private Funktion
    function _geheimeFunktion() private view returns (uint) {
        return geheimeZahl;
    }

    // Öffentliche Funktion, um geheime Zahl zu erhalten
    function zeigeGeheimeZahl() public view returns (uint) {
        return _geheimeFunktion();
    }
}
```

In diesem Beispiel wird die Variable `geheimeZahl` und die Funktion `_geheimeFunktion` als `private` deklariert, sodass sie nur innerhalb des Vertrags `Beispiel` zugänglich sind.

## Explanation
Ein häufiger Fehler ist, dass Entwickler versuchen, auf private Variablen oder Funktionen von abgeleiteten Verträgen zuzugreifen. Da private Elemente nur innerhalb des Vertrags sichtbar sind, führt dies zu Kompilierungsfehlern. Darüber hinaus sollte beachtet werden, dass private Daten nicht vor der Sichtbarkeit in der Blockchain geschützt sind; sie sind lediglich vor unbefugtem Zugriff durch andere Verträge oder Benutzer geschützt.

Es ist wichtig, die Sichtbarkeit der Variablen und Funktionen sorgfältig zu planen, um die Sicherheit und Integrität des Vertrages zu gewährleisten. In einigen Fällen kann es sinnvoll sein, `internal` zu verwenden, wenn abgeleitete Verträge Zugriff auf bestimmte Funktionen oder Daten benötigen.

## One Line Summary
Das `private` Schlüsselwort in Solidity schützt Variablen und Funktionen vor unbefugtem Zugriff und sorgt für Kapselung innerhalb des Vertrags.