<!--
Meta Description: # Calldata in Solidity: Verständnis und Anwendung ## Synopsis Calldata ist ein spezieller Datentyp in Solidity, der für die Übergabe von Daten an Funk...
Meta Keywords: calldata, der, die, solidity, ist
-->

# Calldata in Solidity: Verständnis und Anwendung

## Synopsis
Calldata ist ein spezieller Datentyp in Solidity, der für die Übergabe von Daten an Funktionen verwendet wird, insbesondere bei externen Funktionsaufrufen. Er ist unveränderlich und optimiert den Gasverbrauch bei der Interaktion mit Smart Contracts.

## Dokumentation
Calldata ist ein wichtiger Bestandteil der Solidity-Sprache, der es Entwicklern ermöglicht, Daten effizient an Funktionen zu übergeben. Im Gegensatz zu anderen Datentypen wie `memory` oder `storage`, die variabel sind und bearbeitet werden können, ist `calldata` nur lesbar. Dies macht ihn ideal für externe Funktionsaufrufe, bei denen große Mengen an Daten übergeben werden müssen, ohne zusätzlichen Speicherplatz auf der Blockchain zu beanspruchen.

### Zweck
Der Hauptzweck von `calldata` ist die Optimierung der Gasnutzung und die Gewährleistung der Effizienz bei der Datenübergabe. Da `calldata` nur lesbar ist, gibt es keine Möglichkeit, die Daten innerhalb der Funktion zu verändern, was zu einer höheren Sicherheit und Klarheit führt.

### Verwendung
Calldata wird häufig in externen Funktionen verwendet, die mit anderen Smart Contracts oder Wallets interagieren. Es kann in Funktionsparametern deklariert werden, um sicherzustellen, dass die übergebenen Daten effizient verarbeitet werden.

Beispiel:
```solidity
pragma solidity ^0.8.0;

contract Beispiel {
    function addiere(uint256[] calldata zahlen) external pure returns (uint256) {
        uint256 summe = 0;
        for (uint256 i = 0; i < zahlen.length; i++) {
            summe += zahlen[i];
        }
        return summe;
    }
}
```

## Beispiele
### Beispiel 1: Verwendung von Calldata für Arrays
In diesem Beispiel wird ein Array von Zahlen über `calldata` an die Funktion `addiere` übergeben.

```solidity
pragma solidity ^0.8.0;

contract Summierer {
    function summiere(uint256[] calldata zahlen) external pure returns (uint256) {
        uint256 gesamt = 0;
        for (uint256 i = 0; i < zahlen.length; i++) {
            gesamt += zahlen[i];
        }
        return gesamt;
    }
}
```

### Beispiel 2: Übergabe von Strings
Calldata kann auch für die Übergabe von Strings verwendet werden. Beachten Sie, dass Strings in Solidity als `bytes` behandelt werden können.

```solidity
pragma solidity ^0.8.0;

contract StringHandler {
    function empfangeString(string calldata text) external pure returns (string memory) {
        return text;
    }
}
```

## Erklärung
### Häufige Fallstricke
1. **Unveränderlichkeit**: Da `calldata` unveränderlich ist, können Sie die übergebenen Daten nicht in der Funktion ändern. Dies kann zu unerwarteten Ergebnissen führen, wenn Entwickler versuchen, Änderungen an den Daten vorzunehmen.
2. **Speicherlimit**: Bei der Verwendung von `calldata` müssen Sie sicherstellen, dass die Datenmenge innerhalb der Gasgrenzen bleibt, insbesondere bei großen Arrays.
3. **Kompatibilität**: Denken Sie daran, dass `calldata` nur für externe Funktionen geeignet ist. Bei internen Funktionen sollte `memory` oder `storage` verwendet werden.

## Ein-Satz-Zusammenfassung
Calldata ist ein unveränderlicher Datentyp in Solidity, der die effiziente und sichere Übergabe von Daten an externe Funktionen ermöglicht und dabei Gas spart.