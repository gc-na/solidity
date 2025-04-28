<!--
Meta Description: # Rückgabewert in Solidity: Verwendung und Beispiele ## Synopsis In Solidity ist das `return`-Schlüsselwort entscheidend für die Rückgabe von Werten a...
Meta Keywords: solidity, return, die, von, der
-->

# Rückgabewert in Solidity: Verwendung und Beispiele

## Synopsis
In Solidity ist das `return`-Schlüsselwort entscheidend für die Rückgabe von Werten aus Funktionen. Es ermöglicht Entwicklern, Ergebnisse zu liefern und den Programmfluss zu steuern.

## Dokumentation
Das `return`-Schlüsselwort wird in Solidity verwendet, um Werte aus Funktionen zurückzugeben. Es ist ein grundlegendes Element der Programmierung, das es Entwicklern ermöglicht, die Ergebnisse von Berechnungen oder Logiken an den Aufrufer zurückzugeben.

### Zweck
Der Hauptzweck von `return` besteht darin, einen Wert oder mehrere Werte aus einer Funktion zurückzugeben, die dann in der aufrufenden Funktion oder im Code verwendet werden können.

### Verwendung
In Solidity wird das `return`-Schlüsselwort wie folgt verwendet:

1. **Deklaration von Rückgabetypen**: Bevor eine Funktion Werte zurückgeben kann, muss ihr Rückgabetyp in der Funktionssignatur angegeben werden.
2. **Rückgabe von Werten**: Innerhalb des Funktionskörpers wird `return` verwendet, um die gewünschten Werte zurückzugeben.

### Details
- Der Rückgabetyp kann ein einfacher Datentyp (wie uint, int, bool) oder ein komplexer Datentyp (wie Structs oder Arrays) sein.
- Eine Funktion kann mehrere Werte zurückgeben, die in Form eines Tupels zurückgegeben werden.
- Wenn keine Rückgabe erforderlich ist, kann die Funktion als `void` betrachtet werden, und das `return`-Schlüsselwort kann weggelassen werden.

## Beispiele
Hier sind einige grundlegende Beispiele für die Verwendung von `return` in Solidity:

### Einfacher Rückgabewert
```solidity
pragma solidity ^0.8.0;

contract Beispiel {
    function addiere(uint a, uint b) public pure returns (uint) {
        return a + b;
    }
}
```

### Mehrere Rückgabewerte
```solidity
pragma solidity ^0.8.0;

contract Beispiel {
    function teile(uint a, uint b) public pure returns (uint quotient, uint rest) {
        require(b > 0, "Division durch Null nicht erlaubt");
        quotient = a / b;
        rest = a % b;
        return (quotient, rest);
    }
}
```

## Erklärung
Einige häufige Fallstricke und Tipps zur Verwendung von `return` in Solidity:

- **Rückgabewert-Typen**: Stellen Sie sicher, dass der Rückgabewert den in der Funktionssignatur definierten Typen entspricht.
- **Mehrere Rückgaben**: Wenn mehrere Werte zurückgegeben werden, müssen diese in der Funktionssignatur als Tupel deklariert werden.
- **Gasverbrauch**: Berücksichtigen Sie den Gasverbrauch, da das Zurückgeben großer Datenmengen teuer sein kann.

## Ein-Satz-Zusammenfassung
Das `return`-Schlüsselwort in Solidity ist entscheidend für die Rückgabe von Werten aus Funktionen und ermöglicht eine effektive Steuerung des Programmflusses.