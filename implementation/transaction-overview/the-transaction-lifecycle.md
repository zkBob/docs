---
description: From the user to the contract
---

# The Transaction Lifecycle

Transaction is proceed through the several stages before it being accepted by contact.

![Transaction lifecycle](<../../.gitbook/assets/tx\_flow (1).png>)

First of all the initiator (zkBob client) form the transaction with the desired type. He should to calculate the output account and notes, encrypt and pack them into the memo block. Moreover he should calculate the transaction zkSNARK proof. The client sends a public part of the transaction with the proof to the relayer node.

{% hint style="info" %}
#### The public transaction data to be sent to the relayer:

* Transaction proof. It contains the following input fields:
  * Merkle tree root (at the moment of transaction creating)
  * Transaction nullifier
  * The commitment
  * The delta value (a composition of the transaction index, token delta and energy delta)
* Encrypted memo block
* Transaction type
* A deposit signature (for deposit transactions only)
{% endhint %}

Relayer should calculate Merkle tree proof for the received transaction and compose a transaction to the zkBob Pool contract.

On transaction receiving the pool contract checks proofs with the verifier contracts and approve transaction

{% hint style="info" %}
#### Sending a transaction without Relayer

In case of relayer node is down or compromised, user could form a transaction without relayer. To do that user should build an actual zkBob Merkle tree to calculate the proof

<mark style="color:red;">**to be explained in detail**</mark>
{% endhint %}



