---
description: From the user to the contract
---

# The Transaction Lifecycle

A transaction proceeds through several stages before being accepted by the contract.

![Transaction lifecycle](<../../.gitbook/assets/tx\_flow (1).png>)

First the initiator (zkBob client) forms the desired transaction type. Output account and notes are calculated, encrypted, and packed into the memo block. The zkSNARK proof is also calculated. The client sends the public portion of the transaction along with the proof to the relayer node.

{% hint style="info" %}
#### The public transaction data sent to the relayer:

* Transaction proof containing the following input fields:
  * Merkle tree root (at the moment the transaction is created)
  * Transaction nullifier
  * The commitment
  * The delta value (a composition of the transaction index, token delta and energy delta)
* Encrypted memo block
* Transaction type
* Deposit signature (for deposit transactions only)
{% endhint %}

Relayer calculates the Merkle tree proof for the received transaction and composes a transaction sent to the zkBob Pool contract.

On transaction receipt the pool contract checks proofs with the verifier contracts and approves the transaction.

{% hint style="info" %}
#### Sending a transaction without Relayer

If a relayer node is down or compromised, a user can create a transaction without the relayer. To do this the user should build an actual zkBob Merkle tree to calculate the proof.

<mark style="color:red;">**to be explained in detail**</mark>
{% endhint %}



