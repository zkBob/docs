---
description: Main system components
---

# zkBob Application Overview

## Components&#x20;

{% hint style="info" %}
[View deployed contracts here](deployed-contracts.md).
{% endhint %}

The zkBob application is comprised of the following components:

* ****[**zkBob Pool**](contracts-and-circuits/the-pool-contract/)**:** The main contract which holds the zero-knowledge state. It's the core solution component. All transactions are sent here.
* [**Bob Token**](contracts-and-circuits/token-contract.md): The BOB token contract, an ERC20-based fungible token with additional features.
* ****[**Relayer**](relayer-node/)**:** An intermediate actor between users and the Pool. The Relayer receives user transactions, calculates zkSNARKs, and sends transactions to the Pool in a serial manner. While users can send transactions directly to the Pool, the collision probability increases (and user transactions can be reverted due to incorrect rollup state), so it makes sense to send to the Relayer.
* ****[**Operator Manager**](contracts-and-circuits/operator-manager-contract/)**:** The contract which manages access to the Pool. It can be used to activate a single relayer for a defined period of time or provide unlimited access to the Pool. It also checks that the fee receiver and relayer are separate entities.
* ****[**Application**](../zkbob-app/zkbob-app.md): The solution front-end and UI. All transactions are initiated here. The application synchronises a user account with the rollup, and helps to create transactions.



