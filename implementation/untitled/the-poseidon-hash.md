---
description: Used for the different purposes
---

# The Poseidon Hash

The Poseidon is a hash function designed for zero-knowledge proof systems like zkSNARKs. It operates over the $$GF(p)$$ prime field. The main advantage of the Poseidon hash is simplification in circuits building.

The Poseidon contains a series of rounds each based on input permutations (add constants, exponentiation and mixing). An S-box routine is just an exponentiation number in the $$GF(p)$$ field (the power of 5).

The round constants and S-box operations count depend on the parameter set. The Poseidon parameters are a tuple $$(t, f, p, c, m)$$, where

* $$t$$ is a number of S-box routines in one round. It also specifies an input dimension: hash function supports up to $$t$$ input numbers.
* $$f$$ is a full rounds count ($$t$$ S-box routines)
* $$p$$ is a partial rounds count (single S-box routine)
* $$c$$ is a round constants array ($$(f+p) \times t$$ dimension)
* $$m$$ is a square array used for a mixing function ($$t \times t$$ dimension)

The Poseidon routine produces a resulting hash (over prime field) after $$(f+p)$$ rounds.

As mentioned previously there are different parameter sets used for hashes in the Merkle tree. These hash types are explained in the table below. The parameter set is presented in the reduced form (just a tuple$$(t, f, p)$$):&#x20;

<table><thead><tr><th width="174">Label</th><th width="150">Parameters</th><th width="255.7142857142857">Hash purpose</th><th>Inputs</th></tr></thead><tbody><tr><td><span class="math">Hash</span>​</td><td>2, 8, 56</td><td>Key derivation (<span class="math">\eta</span> and <span class="math">P_d</span>)</td><td>Transaction verifier key<span class="math">A</span> or diversifier <span class="math">d</span></td></tr><tr><td><span class="math">Hash_{merkle}</span>/ <span class="math">Hash_{nullifier}</span></td><td>3, 8, 56</td><td>Merkle tree's node;<br>Nullifier</td><td>two child nodes or leafs;<br>Account hash and intermediate nullifier hash (<a href="../transaction-overview/the-nullifiers.md">details</a>)</td></tr><tr><td><span class="math">Hash_{eddsa}</span>/<span class="math">Hash_{inh}</span></td><td>4, 8, 56</td><td>EDDSA sign and verify;  Intermediate nullifier hash (inh)</td><td><span class="math">R.x, A.x, H</span>​ (<a href="../transaction-overview/signing-a-transaction.md#signing">details</a>)<br><span class="math">Hash(acc)</span>, <span class="math">\eta</span>, <span class="math">path</span> (<a href="../transaction-overview/the-nullifiers.md">details</a>)</td></tr><tr><td><span class="math">Hash_{note}</span></td><td>5, 8, 56</td><td>Note hash</td><td><span class="math">d, P_d, b, t</span> (<a href="../account-and-notes/notes.md">details</a>)</td></tr><tr><td><span class="math">Hash_{account}</span>/<span class="math">Hash_{sponge}</span></td><td>6, 8, 57</td><td><p>Account hash;</p><p>Transaction hash</p></td><td><p><span class="math">d, P_d, i, b</span> (<a href="../account-and-notes/accounts.md">details</a>)​;</p><p>account and notes hashes with transaction commitment (<a href="../transaction-overview/signing-a-transaction.md#transaction-hashing">details</a>)</p></td></tr></tbody></table>

{% hint style="info" %}
**Poseidon specification**

This page provides just a simple description of the Poseidon hash function. For additional details please refer to the [original publication](https://eprint.iacr.org/2019/458.pdf). It contains exhaustive materials, security investigations, implementation details, proof system applications and so on.
{% endhint %}
