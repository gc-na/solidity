<!--
Meta Description: # Override in Solidity: Eine umfassende Anleitung ## Synopsis Der `override`-Modifier in Solidity ermöglicht es, eine Funktion in einer abgeleiteten K...
Meta Keywords: override, der, solidity, modifier, die
-->

# Override in Solidity: Eine umfassende Anleitung

## Synopsis
Der `override`-Modifier in Solidity ermöglicht es, eine Funktion in einer abgeleiteten Klasse zu überschreiben, die in einer Basisklasse definiert ist. Diese Funktionalität ist entscheidend für die Implementierung polymorpher Verhalten in intelligenten Verträgen.

## Documentation
Der `override`-Modifier wird verwendet, um anzugeben, dass eine Funktion in einem abgeleiteten Vertrag die Implementierung einer Funktion aus einem übergeordneten Vertrag ersetzen soll. Dies ist besonders nützlich, wenn man mit Vererbung arbeitet, um sicherzustellen, dass die korrekte Funktion aufgerufen wird.

### Zweck
- **Polymorphie**: Der `override`-Modifier ermöglicht polymorphe Aufrufe, indem er es abgeleiteten Verträgen erlaubt, die Funktionsimplementierung der Basisklasse zu ändern.
- **Klarheit**: Durch die Verwendung von `override` wird der Code klarer und verständlicher, da es sofort erkennbar ist, dass eine Funktion absichtlich überschrieben wird.

### Verwendung
Um den `override`-Modifier zu verwenden, fügen Sie ihn in der Funktionsdefinition der abgeleiteten Klasse hinzu. Hier ist die Syntax:

```solidity
function functionName() public override returns (returnType) {
    // Implementierung
}
```

### Details
- Der `override`-Modifier kann nur verwendet werden, wenn die Funktion in der Basisklasse als `virtual` deklariert ist.
- Wenn eine Funktion in mehreren Basisklassen definiert ist, muss der `override`-Modifier für jede dieser Basisklassen angegeben werden.

## Examples
Hier sind einige grundlegende Beispiele zur Verwendung des `override`-Modifiers in Solidity:

### Beispiel 1: Einfaches Überschreiben
```solidity
pragma solidity ^0.8.0;

contract Base {
    function greet() public virtual returns (string memory) {
        return "Hallo von der Basis!";
    }
}

contract Derived is Base {
    function greet() public override returns (string memory) {
        return "Hallo von der abgeleiteten Klasse!";
    }
}
```

### Beispiel 2: Mehrfaches Überschreiben
```solidity
pragma solidity ^0.8.0;

contract Base1 {
    function greet() public virtual returns (string memory) {
        return "Hallo von Basis 1!";
    }
}

contract Base2 {
    function greet() public virtual returns (string memory) {
        return "Hallo von Basis 2!";
    }
}

contract Derived is Base1, Base2 {
    function greet() public override(Base1, Base2) returns (string memory) {
        return "Hallo von der abgeleiteten Klasse!";
    }
}
```

## Explanation
### Häufige Fallstricke
- **Fehlendes `virtual` in der Basisklasse**: Wenn Sie versuchen, eine Funktion ohne `virtual` in der Basisklasse zu überschreiben, wird ein Compilerfehler ausgegeben.
- **Falsche Verwendung des `override`-Modifiers**: Es ist wichtig, den `override`-Modifier korrekt zu verwenden, insbesondere bei mehreren Basisklassen, um Verwirrung und Fehler zu vermeiden.

### Zusätzliche Hinweise
- Der `override`-Modifier ist ab Solidity 0.6.0 verpflichtend, um die Codequalität und -klarheit zu erhöhen.
- Nutzen Sie den `override`-Modifier, um sicherzustellen, dass die Intention des Codes klar ist, und um unbeabsichtigte Überschreibungen zu vermeiden.

## One Line Summary
Der `override`-Modifier in Solidity ermöglicht es, Funktionen in abgeleiteten Klassen zu überschreiben und fördert so ein klares und sicheres Vererbungssystem.