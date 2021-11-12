---
description: Poseidon hash function
---

# Merkle tree hashing

The Merkle tree's leaves and nodes contains hashes. Each node is calculated as hash of two children nodes. A leaf depends on leafs type (account and note leafs). A single hash function called Poseidon with the different parameters set is used to calculate hash for the every Merkle tree's element.

The Poseidon is a hash function designed for zero-knowledge proof systems like zkSNARKs. It operates over the $$GF(p)$$ prime field. The main advantage of the Poseidon hash is circuits building simplification.

The Poseidon contains a series of rounds each based on inputs  permutations (add constants, exponentiation and mixing). S-box routine is a simple number exponentiation in the $$GF(p)$$ field (the power of 5).

The round constants and S-box operations count depends on the parameters set. The Poseidon parameters is a tuple $$(t, f, p, c, m)$$, where

* $$t$$ is  a number of S-box routines in the one round. It also specifies an input dimension: hash function will support up to $$t$$ input numbers
* $$f$$ is a full rounds count ($$t$$ S-box routines)
* $$p$$ is a partial rounds count (single S-box routine)
* $$c$$ is round constants array ($$(f+p) \times t$$ dimension)
* $$m$$ is a square array used for mixing function ($$t \times t$$ dimension)

The Poseidon routine produces a resulting hash (over prime field) after $$(f+p)$$ rounds

As mentioned above, the are different parameter sets used for hashes in the Merkle tree. This hash types are explained in the table below

| Hash purpose | Parameters set: t, f, p | Inputs                                                          |
| ------------ | ----------------------- | --------------------------------------------------------------- |
| Account leaf | 6, 8, 57                | $$\eta, i, b,t$$ ([details](../account-and-notes/accounts.md))​ |
| Note leaf    | 5, 8, 56                | $$d, P_d, b, t$$ ([details](../account-and-notes/notes.md))     |
| Tree node    | 3, 8, 56                | two child nodes or leafs                                        |

{% hint style="info" %}
**Poseidon specification**

This page just provide a simple description of the Poseidon hash function. For additional details please refer to the [original publication](https://eprint.iacr.org/2019/458.pdf). It contains exhaustive materials, security investigations, implementation details, proof system applications and so on.
{% endhint %}
