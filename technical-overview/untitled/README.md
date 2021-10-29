---
description: The main data structure
---

# zkBob Merkle Tree

![Full Merkle tree](../../.gitbook/assets/Merkle\_200dpi\_b.png)

Merkle tree in the zkBob solution is used to link and store encrypted transaction data (accounts and notes) with the strict sequence. The accounts and notes are placed in the tree leaves.

The full Merkle tree can be divided into transaction subtrees and commitment subtree (with transaction commitments as leaves).

The commitment subtree ensures correct transaction sequence without transaction data disclosure. The transaction subtree links underlying data (accounts and notes) within&#x20;

{% hint style="warning" %}
#### Merkle tree height

Please keep in mind that the tree in the picture above is not at its actual height. It's just a simplified representation.

The zkBob solution use Merkle tree with a total height of 48 (transaction subtree with the height of 7 and commitment subtree with the height of 41).

So due to this height a transaction supports up to 128 leaves (a single account plus 127 notes) and the tree supports up to $$2^{41} \approx 2.2 * 10^{12}$$ transactions
{% endhint %}



* [x] Merkle Tree graphical scheme
* [x] Tree leaves: account and notes
* [ ] A few words about Merkle tree root
* [ ] Merkle Tree proofs
* [ ] Merkle tree updating example

