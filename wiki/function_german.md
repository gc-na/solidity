<!--
Meta Description: # Funktionen in Solidity: Grundlagen und Anwendung ## Synopsis In Solidity sind Funktionen zentrale Bausteine, die es Entwicklern ermöglichen, logisch...
Meta Keywords: und, solidity, die, funktionen, funktion
-->

# Funktionen in Solidity: Grundlagen und Anwendung

## Synopsis
In Solidity sind Funktionen zentrale Bausteine, die es Entwicklern ermöglichen, logische Operationen in Smart Contracts zu definieren und auszuführen. Sie strukturieren den Code, fördern die Wiederverwendbarkeit und ermöglichen die Interaktion mit anderen Teilen des Contracts.

## Dokumentation
Funktionen in Solidity sind deklarierte Abschnitte des Codes, die spezifische Aufgaben erfüllen. Sie können Eingabewerte (Parameter) akzeptieren und Rückgabewerte liefern. Funktionen helfen dabei, den Code modular zu gestalten und erleichtern die Wartung und das Testen.

### Zweck
Der Hauptzweck von Funktionen in Solidity besteht darin, Logik zu kapseln und den Code lesbarer zu machen. Sie ermöglichen es Entwicklern, komplexe Abläufe in kleinere, handhabbare Teile zu zerlegen.

### Verwendung
Eine Funktion wird in Solidity mit dem Schlüsselwort `function` deklariert, gefolgt vom Funktionsnamen, einer optionalen Sichtbarkeit (wie `public`, `private`, `internal`, oder `external`), und einer optionalen Rückgabetypen-Deklaration.

```solidity
function funktionsName(parameterTyp parameterName) public returns (rückgabewertTyp) {
    // Funktionskörper
}
```

### Details
- **Sichtbarkeit**: Bestimmt, wer die Funktion aufrufen kann. `public` ermöglicht den Zugriff von außen, `private` nur innerhalb der Klasse, und `internal` erlaubt den Zugriff innerhalb des Contracts und abgeleiteten Contracts.
- **Sichtbare Funktionen**: Die Funktionen können in `pure`, `view` oder `payable` klassifiziert werden. `pure` bedeutet, dass die Funktion keine Blockchain-Daten liest oder ändert, `view` erlaubt das Lesen von Daten, und `payable` lässt Ether-Transaktionen zu.
- **Fallback-Funktion**: Eine spezielle Funktion, die aufgerufen wird, wenn eine Transaktion an einen Contract geschickt wird, ohne eine spezifische Funktion zu benennen.

## Beispiele
Hier sind einige grundlegende Beispiele für die Verwendung von Funktionen in Solidity:

### Beispiel 1: Einfache Funktion
```solidity
pragma solidity ^0.8.0;

contract Beispiel {
    uint256 public zahl;

    function setZahl(uint256 _zahl) public {
        zahl = _zahl;
    }

    function getZahl() public view returns (uint256) {
        return zahl;
    }
}
```

### Beispiel 2: Funktion mit Zahlung
```solidity
pragma solidity ^0.8.0;

contract BezahlterVertrag {
    function empfangen() public payable {
        // Logik für den Empfang von Ether
    }
}
```

## Erklärung
Ein häufiger Fehler beim Arbeiten mit Funktionen in Solidity ist das Missverständnis über Sichtbarkeit. Wenn eine Funktion `private` deklariert ist, kann sie nicht von externen Konten oder sogar von abgeleiteten Contracts aufgerufen werden. Auch das Vergessen, eine Funktion als `payable` zu kennzeichnen, kann dazu führen, dass Ether nicht akzeptiert wird.

Ein weiterer Punkt ist der Umgang mit Rückgabewerten. Entwickler sollten sicherstellen, dass der Rückgabewert den richtigen Typ hat und dass der Funktionskörper alle möglichen Ausführungspfade abdeckt.

## Einzeiler Zusammenfassung
Funktionen in Solidity sind entscheidend für die Strukturierung und Modularität von Smart Contracts, indem sie spezifische Aufgaben definieren und die Wiederverwendbarkeit des Codes fördern.