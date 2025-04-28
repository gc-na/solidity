<!--
Meta Description: # require in Solidity: Bedingte Anweisungen für Smart Contracts ## Synopsis In Solidity ist `require` eine essentielle Funktion, die verwendet wird, u...
Meta Keywords: die, require, der, von, solidity
-->

# require in Solidity: Bedingte Anweisungen für Smart Contracts

## Synopsis
In Solidity ist `require` eine essentielle Funktion, die verwendet wird, um Bedingungen zu überprüfen und sicherzustellen, dass bestimmte Voraussetzungen erfüllt sind, bevor der Smart Contract fortfährt. Sie spielt eine entscheidende Rolle bei der Validierung von Eingaben und der Gewährleistung der Sicherheit von Transaktionen.

## Documentation
### Zweck
Die `require`-Anweisung wird verwendet, um Bedingungen in Smart Contracts zu stellen. Sie dient dazu, sicherzustellen, dass bestimmte Bedingungen erfüllt sind, bevor der Code weiter ausgeführt wird. Wenn die Bedingung nicht erfüllt ist, wird der gesamte Vorgang abgebrochen, und alle Änderungen werden zurückgesetzt.

### Verwendung
Die allgemeine Syntax von `require` lautet:

```solidity
require(Bedingung, "Fehlermeldung");
```

- **Bedingung**: Ein boolescher Ausdruck, der überprüft wird. Wenn dieser Ausdruck `false` ergibt, wird die Ausführung gestoppt.
- **Fehlermeldung**: Eine optionale Fehlermeldung, die zurückgegeben wird, wenn die Bedingung fehlschlägt. Dies hilft, das Problem zu identifizieren.

### Details
`require` ist eine der drei Funktionen zur Fehlerbehandlung in Solidity, zusammen mit `revert` und `assert`. Der Hauptunterschied besteht darin, dass `require` für die Validierung von Eingaben und Bedingungen verwendet wird, während `assert` für die Überprüfung von Invarianten gedacht ist. `require` kann auch verwendet werden, um sicherzustellen, dass externe Aufrufe erfolgreich sind.

## Examples
Hier sind einige grundlegende Beispiele für die Verwendung von `require` in Solidity:

### Beispiel 1: Überprüfung des Kontostands
```solidity
function withdraw(uint amount) public {
    require(amount <= balance[msg.sender], "Nicht genügend Guthaben");
    balance[msg.sender] -= amount;
    msg.sender.transfer(amount);
}
```

### Beispiel 2: Überprüfung der Eingabewerte
```solidity
function setAge(uint _age) public {
    require(_age > 0 && _age < 120, "Ungültiges Alter");
    age = _age;
}
```

### Beispiel 3: Überprüfung des Vertragsbesitzers
```solidity
function onlyOwner() public view {
    require(msg.sender == owner, "Nur der Besitzer kann das tun");
}
```

## Explanation
Ein häufiges Problem beim Einsatz von `require` ist das Fehlen einer klaren Fehlermeldung. Eine präzise Fehlermeldung kann Entwicklern und Benutzern helfen, das Problem schnell zu identifizieren. Zudem sollten die Bedingungen, die in `require` verwendet werden, so formuliert sein, dass sie nicht zu komplex sind, um Missverständnisse zu vermeiden.

Ein weiterer wichtiger Punkt ist die Gasgebühr: Wenn eine `require`-Bedingung fehlschlägt, wird das gesamte Transaktionsgas zurückerstattet, jedoch nicht die Gebühren, die bereits für die Durchführung der Transaktion angefallen sind. Dies kann in der Planung von Transaktionen berücksichtigt werden.

## One Line Summary
Die `require`-Anweisung in Solidity ermöglicht die Überprüfung von Bedingungen und sorgt für die Sicherheit und Stabilität von Smart Contracts.