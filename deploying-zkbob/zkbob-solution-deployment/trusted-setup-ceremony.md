---
description: Initial mandatory procedure
---

# Trusted Setup Ceremony

Our solution based on zkSNARKs which are using to provide transaction correctness proofs by the participants. Nobody can disclosure transaction details but everyone can verify it. zkSNARK scheme require parameter and verification scheme generation for the each circuit. It has a bottleneck: this process will produce "toxic waste" which should not be disclosed anyone.

The most famous approach to get the public parameters and verification keys for the circuit is to involve people to the Multi-Party Computation (MPC) process. At least single participant in this scheme should be the honest to ensure the safety of the entire process. So that process is well-known as Trusted Setup Ceremony.

**The Ceremony input:** transfer and tree circuit written with bellman library

**The Ceremony output:**

* transfer verifier circuit parameters (tx\_params.bin)
* transfer verifier circuit verification key (tx\_vk.json)
* tree verifier circuit parameters (tree\_params.bin)
* tree verifier circuit verification key (tree\_vk.json)



