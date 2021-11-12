---
description: The main data structure
---

# zkBob Merkle Tree

![Full Merkle tree](../../.gitbook/assets/Merkle\_200dpi\_b.png)

Merkle tree in the zkBob solution is used to link and store encrypted transaction data (accounts and notes) with the strict sequence. The accounts and notes are placed in the tree leaves.

The full Merkle tree can be divided into transaction subtrees and commitment subtree (with transaction commitments as leaves).

The commitment subtree ensures correct transaction sequence without transaction data disclosure.

The transaction subtree links underlying data (accounts and notes) within a single operation. The transaction subtree's root called "transaction commitment". The commitments are using as commitment subtree's leaves. Each transaction subtree is building with the corresponding [memo block](../transaction-overview/untitled-1/).

{% hint style="warning" %}
#### Merkle tree height

Please keep in mind that the tree in the picture above is not at its actual height. It's just a simplified representation.

The zkBob solution is using Merkle tree with a total height of 48 (transaction subtree with the height of 7 and commitment subtree with the height of 41).

So due to this height a transaction supports up to 128 leaves (a single account plus 127 notes) and the tree supports up to $$2^{41} \approx 2.2 * 10^{12}$$ transactions
{% endhint %}

According to the scheme above, a new transaction determines a new transaction subtree which will be added to the full Merkle tree. Adding a new transaction will affect Merkle tree root. So Merkle tree root determines a current tree state.

The pool contract holds the current leaves count (the number of transactions multiplied by 128) and the Merkle tree roots for all transactions.

* [x] Merkle Tree graphical scheme
* [x] Tree leaves: account and notes
* [x] A few words about Merkle tree root
* [ ] Merkle Tree proofs
* [ ] Merkle tree updating example

