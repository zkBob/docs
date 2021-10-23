---
description: An intermediate between zkBob clients and contract
---

# Relayer Node

The relayer is a client interface to zkBob solution. The main purpose of the relayer is to process input transaction, calculate Merkle tree proofs and bring them to the contract.

{% hint style="success" %}
One of relayer's advantage is anonymity increasing due to gas payments. When you directly interact with the zkBob contract your actions can be disclosed implicitly because you should pay some gas within the native blockchain.
{% endhint %}

The relayer consist of Merkle tree instance and transaction storages.

Merkle tree based on a key-value database. It supports adding new leaves, root updating and zkSNARK proofs building.

Transaction storage is used to to save encrypted accounts and notes. That's why the relayer can provide fast reply to the client during the state synchronising.

Clients interact with the relayer according with REST API

{% hint style="warning" %}
#### Relayers scalability

zkBob solution is developed to support multiply relayers configuration. But the current implementation assumes single relayer in the network. We will implement multiple relayer scheme in the near future
{% endhint %}
