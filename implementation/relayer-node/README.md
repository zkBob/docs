---
description: An intermediary between zkBob clients and contract
---

# Relayer Node

The relayer is a client interface to zkBob solution. The main purpose of the relayer is to process input transaction, calculate Merkle tree proofs and send them to the contract.

{% hint style="success" %}
One of relayer's advantage is increasing anonymity due to abstracted gas payments. When you directly interact with the zkBob contract your actions can be disclosed implicitly because you should pay some gas within the native blockchain.
{% endhint %}

* The relayer consists of a Merkle tree instance and transaction storages.
* The Merkle tree based on a key-value database. It supports adding new leaves, root updating and zkSNARK proofs building.
* Transaction storage is used to to save encrypted accounts and notes. The relayer can provide fast reply to the client during the state synchronization.
* Clients interact with the relayer via the [REST API](rest-api.md).
* [Relayer github repo](https://github.com/zkBob/zeropool-relayer).

{% hint style="warning" %}
#### Relayer scalability

zkBob  is developed to support multiple relayers configuration. But the current implementation assumes a single relayer in the network. We will implement a multiple relayer scheme in the near future.
{% endhint %}
