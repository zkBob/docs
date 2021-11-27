---
description: The promotional token for your involvement
---

# The Energy

Every time you put your money in the zkBob pool, you earn additional energy tokens. The energy - is some kind of your contribution in the anonymity set. The more you invested funds and the longer you hold it inside the pool, the more your energy earned.

So the energy is updated every time you made a transaction and it's growth calculated as following:

$$e = Acc_{in}.b (Acc_{out}.i - Acc_{in}.i) + \sum_k Note_k.b (Acc_{out}.i - pos(Note_k))$$

where

* $$Acc_{in}$$ and $$Acc_{out}$$ is the transaction's input and output [accounts](account-and-notes/accounts.md) respectively,
* $$Note_k$$ is the transaction's input [note](account-and-notes/notes.md)
* $$pos(Note_k)$$ is the note's position in the [Merkle tree](untitled/)

When you make a withdrawal transaction, you can get some amount (from zero to overall) of your energy. The pool contract will mint energy tokens for the address specified in such transaction.

{% hint style="danger" %}
**Non-production feature**

The energy token mechanics is still in development. Please note that the energy is accumulated in the your account as described above when you are interacting with the zkBob solution, but you cannot withdraw energy tokens currently.
{% endhint %}





