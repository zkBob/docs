---
description: An atomic operation on the blockchain
---

# Transaction Overview

The main purpose of any transaction is to perform some kind of the funds movement on the blockchain. So each transaction has several inputs and outputs. [Account](../account-and-notes/accounts.md) and [notes](../account-and-notes/notes.md) can be used as inputs and outputs.

The current implementation assumes that the each transaction has a single input and output account and a fixed amount of input \(3\) and output \(127\) notes.

The input and output accounts designate a transaction initiator. The account changes \(including balance, energy and spent offset\) are reflected in the output account.

{% hint style="info" %}
The input account should be omitted for the first transaction from this account
{% endhint %}

The input notes are spending funds. There is only the note owner could it use as a transaction input.  The account spent offset should be changed after note using. The output notes are addressed to the funds receiver.



