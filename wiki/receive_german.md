<!--
Meta Description: # receive: Die Empfangsfunktion in Solidity ## Synopsis In Solidity ist die `receive`-Funktion eine spezielle Funktion, die es Smart Contracts ermögli...
Meta Keywords: die, funktion, receive, ether, wird
-->

# receive: Die Empfangsfunktion in Solidity

## Synopsis
In Solidity ist die `receive`-Funktion eine spezielle Funktion, die es Smart Contracts ermöglicht, Ether zu empfangen, ohne dass dabei Daten gesendet werden. Sie ist ein zentraler Bestandteil des Ethereum-Ökosystems und wird häufig in Smart Contracts verwendet, um den Empfang von Zahlungen zu automatisieren.

## Dokumentation
Die `receive`-Funktion ist eine von zwei Funktionen, die in Solidity zur Handhabung von eingehenden Ether-Transfers verwendet werden. Die zweite Funktion ist die `fallback`-Funktion. Die `receive`-Funktion wird aufgerufen, wenn ein Ether-Transfer an den Smart Contract ohne begleitende Daten erfolgt.

### Zweck
Die Hauptfunktion der `receive`-Funktion besteht darin, Ether von externen Konten zu empfangen. Sie bietet eine einfache Möglichkeit, Gelder zu akzeptieren und gleichzeitig die Logik des Smart Contracts zu steuern.

### Verwendung
Die `receive`-Funktion wird wie folgt definiert:
```solidity
receive() external payable {
    // Logik zum Empfang von Ether
}
```
- **`external`**: Die Funktion kann nur von außerhalb des Contracts aufgerufen werden.
- **`payable`**: Diese Kennzeichnung erlaubt es dem Contract, Ether zu empfangen.

### Details
- Die `receive`-Funktion kann nur einmal pro Contract existieren.
- Wenn eine Funktion mit Daten an den Contract gesendet wird, wird die `fallback`-Funktion aufgerufen, nicht die `receive`-Funktion.
- Wenn der Contract keine `receive`- oder `fallback`-Funktion implementiert, wird der Empfang von Ether fehlschlagen.

## Beispiele
### Einfaches Beispiel
Hier ist ein einfaches Beispiel, das zeigt, wie die `receive`-Funktion verwendet wird:
```solidity
pragma solidity ^0.8.0;

contract EtherReceiver {
    event Received(address sender, uint amount);

    receive() external payable {
        emit Received(msg.sender, msg.value);
    }
}
```
In diesem Beispiel wird jedes Mal, wenn der Contract Ether empfängt, ein Ereignis `Received` ausgelöst, das den Absender und den Betrag protokolliert.

### Beispiel mit Fallback-Funktion
Ein Contract kann sowohl die `receive`- als auch die `fallback`-Funktion definieren:
```solidity
pragma solidity ^0.8.0;

contract EtherReceiver {
    event Received(address sender, uint amount);
    event FallbackCalled(address sender, uint amount);

    receive() external payable {
        emit Received(msg.sender, msg.value);
    }

    fallback() external payable {
        emit FallbackCalled(msg.sender, msg.value);
    }
}
```
In diesem Beispiel wird die `fallback`-Funktion aufgerufen, wenn Ether mit Daten gesendet wird.

## Erklärung
### Häufige Fallstricke
- **Fehlende `payable` Kennzeichnung:** Wenn die `receive`-Funktion nicht als `payable` deklariert ist, wird kein Ether empfangen.
- **Unzureichende Gasgrenze:** Wenn das Senden von Ether an den Contract aufgrund von Gasproblemen fehlschlägt, wird die Transaktion revertiert.
- **Verwendung der falschen Funktion:** Bei der Übertragung von Ether mit Daten wird die `receive`-Funktion nicht aufgerufen; stattdessen ist die `fallback`-Funktion relevant.

### Zusätzliche Hinweise
- Die `receive`-Funktion kann nicht über einen `view` oder `pure` Modifikator verfügen.
- Es ist ratsam, Sicherheitsmaßnahmen zu implementieren, um sicherzustellen, dass der Contract nicht angreifbar ist.

## Ein Satz Zusammenfassung
Die `receive`-Funktion in Solidity ermöglicht es Smart Contracts, Ether ohne begleitende Daten zu empfangen und ist ein wichtiger Bestandteil des Ethereum-Ökosystems.