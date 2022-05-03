---
description: Initial mandatory procedure
---

# Trusted Setup Ceremony

zkBob uses zkSNARKs to provide transaction correctness proofs for participants. No one can ascertain transaction details but anyone can verify proof that a transaction occurred. To start, the zkSNARK scheme requires parameter and verification scheme generation for each circuit. However, this process produces "toxic waste" which should not be disclosed to anyone.

The most popular approach to get the public parameters and verification keys for the circuit is to involve a group of people in the Multi-Party Computation (MPC) process. At least a single participant in this scheme should be honest to ensure the safety of the entire process. This process is known as a Trusted Setup Ceremony.

**The Ceremony input:**&#x20;

* Transfer and tree circuit written with the bellman library.

**The Ceremony output:**

* Transfer verifier circuit parameters (tx\_params.bin)
* Transfer verifier circuit verification key (tx\_vk.json)
* Tree verifier circuit parameters (tree\_params.bin)
* Tree verifier circuit verification key (tree\_vk.json)



