---
description: An intermediary between zkBob clients and contract
---

# Relayer Node

The relayer is a client interface to zkBob solution. The main purpose of the relayer is to process input transaction, calculate Merkle tree proofs and send them to the contract.

The relayer node isn't a mandatory system part. Users are able to create transactions and interact with the Pool contract themselves. But there are some issues they can face with. First of all user should continuously synchronize the pool state to keep the actual Merkle tree. If the Merkle tree on the client side isn't actual he unable to create correct proof needed to include his transaction. Secondly when the Pool is heavy loaded (a lot of users send transactions simultaneously) the time delay between the proof calculation start and transaction delivery to the pool may lead to collision. If somebody successfully sends his transaction in that time interval the Merkle tree root will change so your transaction will be reverted (while gas will spent).

The relayer solves the issues described above by strict transaction ordering. Moreover it takes on the heavy tree proof computations and Pool state synchronisation. You can simply query the current pool state instead of extracting it from the pool's calldata. In general the relayer just provides a quality customer service to facilitate the contract interaction.

{% hint style="info" %}
The relayer cannot compromise your transactions and take the "Attacker in the Middle" role. The most negative thing which the relayer can do is to provide an incorrect state to the user. But it never can steal your money, reveal shielded balances, decrypt transactions receiver\amount or change your transactions due to underlying zero-knowledge protocol nature
{% endhint %}

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
