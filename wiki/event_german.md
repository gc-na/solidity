<!--
Meta Description: # Events in Solidity: Grundlagen und Anwendung ## Synopsis In Solidity sind Events eine wichtige Funktion, die es Smart Contracts ermöglicht, Informat...
Meta Keywords: solidity, events, die, werden, smart
-->

# Events in Solidity: Grundlagen und Anwendung

## Synopsis
In Solidity sind Events eine wichtige Funktion, die es Smart Contracts ermöglicht, Informationen an externe Abonnenten, wie z.B. DApps oder Frontend-Anwendungen, zu senden. Sie bieten eine effiziente Möglichkeit, Änderungen im Zustand eines Smart Contracts zu protokollieren und zu überwachen.

## Dokumentation
Events in Solidity sind spezielle Protokolle, die es Smart Contracts ermöglichen, Daten im Ethereum-Netzwerk zu speichern und zu übermitteln. Sie sind besonders nützlich, um die Benutzeroberfläche einer DApp zu aktualisieren oder um Transaktionen nachverfolgen zu können.

### Zweck
Events dienen dazu, wichtige Informationen zu speichern, die von externen Anwendungen oder Benutzern abgerufen werden können. Wenn ein Event im Smart Contract ausgelöst wird, wird es in der Blockchain protokolliert und kann von Frontend-Anwendungen abgerufen werden.

### Verwendung
Um ein Event in Solidity zu verwenden, muss es zuerst deklariert werden. Anschließend kann es in Funktionen innerhalb des Contracts ausgelöst werden. Die allgemeine Syntax lautet:

```solidity
event EventName(Type parameter1, Type parameter2, ...);
```

Ein Event wird dann mit dem Schlüsselwort `emit` ausgelöst:

```solidity
emit EventName(value1, value2, ...);
```

### Details
- Events sind kostengünstig in Bezug auf Gas, da sie im Log-Bereich der Blockchain gespeichert werden, der nicht mit den regulären Daten des Smart Contracts interagiert.
- Sie können bis zu 3.000 Bytes an Daten pro Event speichern.
- Es können auch Indizes für Parameter verwendet werden, um die Suche nach bestimmten Ereignissen zu erleichtern.

## Beispiele
Hier sind einige grundlegende Beispiele zur Verwendung von Events in einem Solidity Smart Contract:

### Beispiel 1: Einfaches Event
```solidity
pragma solidity ^0.8.0;

contract SimpleStorage {
    event ValueChanged(uint256 newValue);

    uint256 public storedData;

    function set(uint256 x) public {
        storedData = x;
        emit ValueChanged(x);
    }
}
```

### Beispiel 2: Event mit mehreren Parametern
```solidity
pragma solidity ^0.8.0;

contract Bank {
    event Deposit(address indexed user, uint256 amount);

    function deposit() public payable {
        emit Deposit(msg.sender, msg.value);
    }
}
```

## Erklärung
Ein häufiges Problem beim Arbeiten mit Events in Solidity ist das Missverständnis über die Sichtbarkeit und den Zugriff auf die Ereignisdaten. Events sind nicht direkt im Smart Contract zugänglich, sondern müssen über die Blockchain abgerufen werden. Zudem sollte beachtet werden, dass Events nicht für die Logik des Smart Contracts verwendet werden sollten, da sie nicht den Zustand des Contracts ändern können.

Ein weiteres typisches Problem ist die Verwendung von zu vielen indizierten Parametern. Es können maximal 3 Parameter indiziert werden, was bei der Planung von Events berücksichtigt werden muss.

## Einzeilensummary
Events in Solidity ermöglichen es Smart Contracts, wichtige Informationen effizient an externe Anwendungen zu kommunizieren und zu protokollieren.