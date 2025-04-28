<!--
Meta Description: # Virtuelle Funktionen in Solidity: Verwendung und Bedeutung ## Synopsis In Solidity ist das Schlüsselwort `virtual` entscheidend für die Erstellung a...
Meta Keywords: virtual, die, funktion, solidity, abgeleiteten
-->

# Virtuelle Funktionen in Solidity: Verwendung und Bedeutung

## Synopsis
In Solidity ist das Schlüsselwort `virtual` entscheidend für die Erstellung anpassbarer Funktionen in vererbten Verträgen. Es ermöglicht die Definition von Funktionen, die in abgeleiteten Verträgen überschrieben werden können.

## Dokumentation
Das `virtual`-Schlüsselwort wird in Solidity verwendet, um Funktionen zu kennzeichnen, die überschrieben werden können. Dies ist ein zentraler Bestandteil der objektorientierten Programmierung und ermöglicht Entwicklern, flexible und erweiterbare Smart Contracts zu erstellen.

### Zweck
Der Hauptzweck von `virtual` besteht darin, die Funktionalität einer Funktion in einem Basiskontrakt zu definieren, die in abgeleiteten Verträgen angepasst oder erweitert werden kann. Dies fördert die Wiederverwendbarkeit und Modularität des Codes.

### Verwendung
Um eine Funktion als `virtual` zu kennzeichnen, fügen Sie einfach das Schlüsselwort vor der Funktionsdefinition hinzu. Ein abgeleiteter Vertrag kann dann die Funktion mit dem Schlüsselwort `override` überschreiben.

### Details
- **Kompatibilität**: Das `virtual`-Schlüsselwort ist in Solidity-Versionen >=0.6.0 verfügbar.
- **Erforderlichkeit**: Wenn eine Funktion in einem abgeleiteten Vertrag überschrieben wird, muss die ursprüngliche Funktion im Basiskontrakt als `virtual` deklariert werden.
- **Zugänglichkeit**: `virtual` kann für öffentliche und interne Funktionen verwendet werden.

## Beispiele
Hier sind einige grundlegende Beispiele zur Verwendung von `virtual` in Solidity:

```solidity
pragma solidity ^0.8.0;

contract Base {
    function greet() public virtual returns (string memory) {
        return "Hallo aus dem Basiskontrakt!";
    }
}

contract Derived is Base {
    function greet() public override returns (string memory) {
        return "Hallo aus dem abgeleiteten Vertrag!";
    }
}
```

In diesem Beispiel definiert der `Base`-Vertrag eine Funktion `greet`, die als `virtual` gekennzeichnet ist. Der `Derived`-Vertrag überschreibt diese Funktion mit einer eigenen Implementierung.

## Erklärung
### Häufige Fallstricke
- **Fehlende Deklaration**: Wenn Sie eine Funktion im Basiskontrakt nicht als `virtual` kennzeichnen, kann sie nicht in einem abgeleiteten Vertrag überschrieben werden.
- **Fehlendes Override**: Wenn eine `virtual`-Funktion in einem abgeleiteten Vertrag nicht mit `override` gekennzeichnet wird, wird ein Kompilierungsfehler erzeugt.
- **Versteckte Funktionen**: Wenn eine `virtual`-Funktion in einem abgeleiteten Vertrag überschrieben wird, kann die ursprüngliche Implementierung nicht mehr direkt aufgerufen werden, es sei denn, Sie verwenden den `super`-Schlüssel.

## Ein-Satz-Zusammenfassung
Das `virtual`-Schlüsselwort in Solidity ermöglicht die Definition von anpassbaren Funktionen in Smart Contracts, die in abgeleiteten Verträgen überschrieben werden können.