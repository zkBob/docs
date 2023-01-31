---
description: Double-spending protection
---

# Nullifiers

The nullifier is a unique value calculated on the transaction _input_ account. It is included in the public transaction portion. The nullifier depends on the input account, the intermediate key $$\eta$$ and account position in the Merke tree ($$path$$):

$$Nullifier(Acc^\text{in}) = Hash_{nullifier}(Hash_{account}(Acc^\text{in}), I)$$

where $$I$$is intermediate nullifier hash calculated as:

$$I = Hash_{inh}(Hash_{account}(Acc^{in}), \eta, path)$$

$$Hash_{nullifier}$$, $$Hash_{inh}$$ and $$Hash_{account}$$ is a[ $$Poseidon$$ hash functions](../untitled/the-poseidon-hash.md)

There is an archive on the contract side which holds nullifiers. In the case of account double-spending the nullifiers for the same accounts will equal one another. In this case the contract will reject a second transaction with the repeated nullifier value.

A nullifier preimage could be safely disclosed without opening any sensitive data, like an intermediate key $$\eta$$ used for encryption and decryption. For example the nullifier disclosure could be useful in compliance reports to proof accounts chain linkage.
