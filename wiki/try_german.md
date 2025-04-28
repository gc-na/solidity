<!--
Meta Description: # try in Solidity: Fehlerbehandlung und Ausnahmebehandlung ## Synopsis Der `try`-Befehl in Solidity ermöglicht eine effektive Fehlerbehandlung bei der...
Meta Keywords: try, der, catch, solidity, fehler
-->

# try in Solidity: Fehlerbehandlung und Ausnahmebehandlung

## Synopsis
Der `try`-Befehl in Solidity ermöglicht eine effektive Fehlerbehandlung bei der Interaktion mit externen Verträgen und bietet eine Möglichkeit, Ausnahmen zu fangen und zu behandeln.

## Dokumentation
In Solidity ist der `try`-Befehl Teil der Fehlerbehandlungsmechanismen, die es Entwicklern ermöglichen, sicher mit externen Funktionen zu interagieren. Dieser Befehl wird hauptsächlich in Verbindung mit dem `catch`-Mechanismus verwendet, um spezifische Fehler zu erfassen und darauf zu reagieren.

### Zweck
Der `try`-Befehl dient dazu, den Aufruf einer externen Funktion innerhalb eines `try-catch`-Blocks sicher auszuführen. Wenn der Aufruf fehlschlägt, kann der Fehler abgefangen und behandelt werden, ohne dass die gesamte Transaktion abgebrochen wird.

### Verwendung
Die grundlegende Struktur eines `try-catch`-Blocks sieht folgendermaßen aus:

```solidity
try <Contract>.method() returns (<Type> result) {
    // Erfolgreicher Rückgabewert
} catch Error(string memory reason) {
    // Behandlung eines benannten Fehlers
} catch (bytes memory lowLevelData) {
    // Behandlung eines Low-Level-Fehlers
}
```

In diesem Beispiel wird ein externes Vertragsmethodenaufruf versucht. Bei einem Fehler kann entweder ein benannter Fehler oder ein Low-Level-Fehler abgefangen werden.

### Details
- **Benannte Fehler**: Diese werden durch `require`, `revert` oder `assert` innerhalb des aufgerufenen Vertrags ausgelöst.
- **Low-Level-Fehler**: Diese treten auf, wenn ein Aufruf an ein nicht existierendes Ziel oder durch einen anderen unerwarteten Zustand erfolgt.
- Der `try`-Block kann nur für externe Funktionsaufrufe verwendet werden.

## Beispiele
Hier sind einige einfache Beispiele für die Verwendung von `try` in Solidity.

### Beispiel 1: Erfolgreicher Aufruf
```solidity
contract Caller {
    function callExternal(address externalContract) public {
        try ExternalContract(externalContract).externalMethod() returns (uint256 result) {
            // Erfolgreiche Ausführung
        } catch {
            // Behandlung eines allgemeinen Fehlers
        }
    }
}
```

### Beispiel 2: Benannter Fehler abfangen
```solidity
contract Caller {
    function callExternal(address externalContract) public {
        try ExternalContract(externalContract).externalMethod() returns (uint256 result) {
            // Erfolgreiche Ausführung
        } catch Error(string memory reason) {
            // Behandlung eines benannten Fehlers: reason enthält die Fehlermeldung
        }
    }
}
```

### Beispiel 3: Low-Level-Fehler abfangen
```solidity
contract Caller {
    function callExternal(address externalContract) public {
        try ExternalContract(externalContract).externalMethod() returns (uint256 result) {
            // Erfolgreiche Ausführung
        } catch (bytes memory lowLevelData) {
            // Behandlung eines Low-Level-Fehlers
        }
    }
}
```

## Erklärung
Ein häufiger Stolperstein bei der Verwendung von `try` ist das Missverständnis seiner Funktionsweise. Entwickler sollten beachten, dass der `try`-Block nur für externe Funktionsaufrufe gilt. Interne Aufrufe innerhalb des gleichen Vertrags können nicht mit `try-catch` behandelt werden. Zudem ist es wichtig, die Rückgabewerte der externen Methoden gut zu definieren, um sicherzustellen, dass die Fehlerbehandlung korrekt funktioniert.

## Ein Satz Zusammenfassung
Der `try`-Befehl in Solidity ermöglicht eine sichere Fehlerbehandlung bei externen Vertragsaufrufen durch den Einsatz von `try-catch`-Blöcken.