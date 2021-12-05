![[Klasa account.png]]

Dla każdej z tych operacji mam regułę obliczania wartości podatku.Zwykle tworzy się wtedy instrukcję ```if/else```
![[if_else.png]]

Pierwszym krokiem jest utworzenie klasy `enum`. W przykładzie tym utworzyłem klasę wyliczeniową TransactionType z metodą abstrakcyjną o nazwie doTransactionOperation
![[Klasa TransactionType.png]]


W kolejnym kroku musimy zaimplementować metodę doTransactionOperation
![[Klasa TransactionType Impl.png]]
![[Pasted image 2011204144409.png]]

Start programu
![[Użycie operacji BUY.png]]
![[Użycie operacji SELL.png]]
![[Użycie operacji DEPOSIT.png]]
![[Użycie operacji WITHDRAWAL.png]]

## Źródło
[Henri Tremblay Github](https://github.com/henri-tremblay/refactoring) Refactoring project — [TransactionType class](https://github.com/henri-tremblay/refactoring/blob/henri/app/src/main/java/pro/tremblay/core/TransactionType.java)