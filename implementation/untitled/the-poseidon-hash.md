---
description: Used for the different purposes
---

# The Poseidon Hash

The Poseidon is a hash function designed for zero-knowledge proof systems like zkSNARKs. It operates over the $$GF(p)$$ prime field. The main advantage of the Poseidon hash is a circuits building simplification.

The Poseidon contains a series of rounds each based on input permutations (add constants, exponentiation and mixing). S-box routine is just an exponentiation number in the $$GF(p)$$ field (the power of 5).

The round constants and S-box operations count depend on the parameter set. The Poseidon parameters are tuple $$(t, f, p, c, m)$$, where

* $$t$$ is  a number of S-box routines in the one round. It also specifies an input dimension: hash function supports up to $$t$$ input numbers
* $$f$$ is a full rounds count ($$t$$ S-box routines)
* $$p$$ is a partial rounds count (single S-box routine)
* $$c$$ is a round constants array ($$(f+p) \times t$$ dimension)
* $$m$$ is a square array used for mixing function ($$t \times t$$ dimension)

The Poseidon routine produces a resulting hash (over prime field) after $$(f+p)$$ rounds.

As mentioned previously there are different parameter sets used for hashes in the Merkle tree. These hash types are explained in the table below. The parameter set is presented in the reduced form (just a tuple$$(t, f, p)$$):&#x20;

| Label                                   | Parameters | Hash purpose                                              | Inputs                                                                                                                                                                                                                                                                                                  |
| --------------------------------------- | ---------- | --------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| $$Hash$$​                               | 2, 8, 56   | Key derivation ($$\eta$$ and $$P_d$$)                     | Transaction verifier key$$A$$ or diversifier $$d$$                                                                                                                                                                                                                                                      |
| $$Hash_{merkle}$$/ $$Hash_{nullifier}$$ | 3, 8, 56   | <p>Merkle tree's node;<br>Nullifier</p>                   | <p>two child nodes or leafs;<br>Account hash and intermediate nullifier hash (<a href="../transaction-overview/the-nullifiers.md">details</a>)</p>                                                                                                                                                      |
| $$Hash_{eddsa}$$/$$Hash_{inh}$$         | 4, 8, 56   | EDDSA sign and verify;  Intermediate nullifier hash (inh) | <p><span class="math">R.x, A.x, H</span>​ (<a href="../transaction-overview/signing-a-transaction.md#signing">details</a>)<br><span class="math">Hash(acc)</span>, <span class="math">\eta</span>, <span class="math">path</span> (<a href="../transaction-overview/the-nullifiers.md">details</a>)</p> |
| $$Hash_{note}$$                         | 5, 8, 56   | Note hash                                                 | $$d, P_d, b, t$$ ([details](../account-and-notes/notes.md))                                                                                                                                                                                                                                             |
| $$Hash_{account}$$/$$Hash_{sponge}$$    | 6, 8, 57   | <p>Account hash;</p><p>Transaction hash</p>               | <p><span class="math">d, P_d, i, b</span> (<a href="../account-and-notes/accounts.md">details</a>)​;</p><p>account and notes hashes with transaction commitment (<a href="../transaction-overview/signing-a-transaction.md#transaction-hashing">details</a>)</p>                                        |

{% hint style="info" %}
**Poseidon specification**

This page provides just a simple description of the Poseidon hash function. For additional details please refer to the [original publication](https://eprint.iacr.org/2019/458.pdf). It contains exhaustive materials, security investigations, implementation details, proof system applications and so on.
{% endhint %}
