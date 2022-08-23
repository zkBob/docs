---
description: Experience points - not in active use
---

# XP (Experience Points)

{% hint style="warning" %}
**Non-production feature**

The XP mechanism is still in research and development.
{% endhint %}

Every time you put your money in the zkBob pool you earn additional XP. XP represent your contribution to the anonymity set. The more you invest funds and the longer you hold it inside the pool, the more XP is earned.

Your XP value is updated every time you make a transaction and growth calculated using the following formula:

$$e = Acc_{in}.b (Acc_{out}.i - Acc_{in}.i) + \sum_k Note_k.b (Acc_{out}.i - pos(Note_k))$$

where

* $$Acc_{in}$$ and $$Acc_{out}$$ is the transaction's input and output [accounts](../../implementation/account-and-notes/accounts.md) respectively,
* $$Note_k$$ is the transaction's input [note](../../implementation/account-and-notes/notes.md)
* $$pos(Note_k)$$ is the note's position in the [Merkle tree](../../implementation/untitled/)

When you make a withdrawal transaction, you can get some amount (from zero to overall) of XP. The pool contract will mint [XP ](../../implementation/contracts-and-circuits/voucher-token-contract.md)for the address specified in such a transaction.





