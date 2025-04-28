<!--
Meta Description: # Revert in Solidity: Fehlerbehandlung und Transaktionsrückgabe ## Synopsis Der `revert` Befehl in Solidity wird verwendet, um eine Transaktion zurück...
Meta Keywords: die, der, revert, solidity, wird
-->

# Revert in Solidity: Fehlerbehandlung und Transaktionsrückgabe

## Synopsis
Der `revert` Befehl in Solidity wird verwendet, um eine Transaktion zurückzusetzen und alle Änderungen, die während der Ausführung vorgenommen wurden, rückgängig zu machen. Dies ist eine wichtige Funktion für die Fehlerbehandlung in smart contracts.

## Documentation
### Zweck
Der `revert` Befehl dient dazu, eine Transaktion abzubrechen, wenn ein unerwarteter Zustand oder Fehler auftritt. Dies stellt sicher, dass der Zustand des Smart Contracts konsistent bleibt und keine unerwünschten Änderungen vorgenommen werden.

### Verwendung
Der `revert` Befehl kann an beliebiger Stelle im Code verwendet werden, um die Ausführung eines Smart Contracts zu stoppen. Er wird oft in Verbindung mit Bedingungen verwendet, um sicherzustellen, dass nur gültige Transaktionen durchgeführt werden.

```solidity
if (condition == false) {
    revert("Fehler: Bedingung nicht erfüllt.");
}
```

### Details
- Wenn `revert` aufgerufen wird, werden alle Änderungen, die seit dem letzten Speichern des Status (z.B. seit der letzten Transaktion) vorgenommen wurden, zurückgesetzt.
- Der Befehl kann auch eine Fehlermeldung übergeben, die Entwicklern hilft, die Ursache des Fehlers zu identifizieren.
- Die Gasgebühren, die für die Transaktion anfallen, werden nicht zurückerstattet, jedoch wird jede nicht verbrauchte Gasmenge an den Aufrufer zurückgegeben.

## Examples
Hier sind einige einfache Beispiele, die die Verwendung von `revert` in Solidity zeigen:

### Beispiel 1: Grundlegende Verwendung
```solidity
pragma solidity ^0.8.0;

contract Beispiel {
    uint public wert;

    function setWert(uint _wert) public {
        if (_wert > 100) {
            revert("Fehler: Wert darf nicht größer als 100 sein.");
        }
        wert = _wert;
    }
}
```
In diesem Beispiel wird der Wert auf 100 begrenzt. Wenn ein Benutzer versucht, einen höheren Wert zu setzen, wird die Transaktion abgebrochen.

### Beispiel 2: Überprüfung von Berechtigungen
```solidity
pragma solidity ^0.8.0;

contract Berechtigungen {
    address public besitzer;

    constructor() {
        besitzer = msg.sender;
    }

    function nurBesitzer() public view {
        if (msg.sender != besitzer) {
            revert("Fehler: Nur der Besitzer kann diese Funktion aufrufen.");
        }
    }
}
```
Hier wird überprüft, ob der Aufrufer der Funktion der Besitzer des Vertrags ist. Andernfalls wird die Ausführung gestoppt.

## Explanation
Ein häufiges Problem bei der Verwendung von `revert` ist das Missverständnis über die Gasgebühren. Entwickler neigen dazu zu glauben, dass alle Gasgebühren zurückerstattet werden, was nicht der Fall ist. Nur die nicht verbrauchte Gasmenge wird zurückgegeben. Ein weiterer Punkt ist die Verwendung von `revert` in Schleifen oder komplexen Bedingungen, da dies zu unerwarteten Kosten führen kann, wenn viele Transaktionen gleichzeitig abgebrochen werden.

## One Line Summary
Der `revert` Befehl in Solidity ist ein leistungsstarkes Werkzeug zur Fehlerbehandlung, das Transaktionen zurücksetzt und den Zustand des Smart Contracts schützt.