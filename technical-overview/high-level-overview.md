---
description: The main system components
---

# High-level Overview

* zkBob is a Layer 2 solution based on the zero-knowledge rollup.&#x20;
* zkBob makes transactions anonymous.
* Transaction details (sender, receiver, amount, etc) are never revealed when transferring funds between users inside the zkBob application.&#x20;
* Shielded tokens are used inside the application pool.

{% hint style="warning" %}
**Anonymity Set Warning**

Although internal transaction details are hidden, users can be compromised when entering in or leaving the solution **in cases when there is a small anonymity set.**

Imagine you want to send money to Alice through zkBob. You decide to create a new account and deposit the exact necessary amount of tokens.&#x20;

Alice also creates an account and provides her private address. You transfer funds to Alice and she makes a withdrawal transaction for all received tokens.&#x20;

If you and Alice are the only active users of the zkBob solution, any neutral observer can infer your funds movement with a high degree of accuracy.

There are no time limits for funds withdrawal. It is recommended to keep funds inside the solution some extra time (the more the better) to increase the anonymity set. This approach can be useful to avoid the case described above. Moreover you will be rewarded for staying inside the solution with extra [energy](energy-token.md).
{% endhint %}

## Components&#x20;

zkBob solution is composed with the following components:

* ****[**Pool**](contracts-and-circuits/the-pool-contract/)**:** The main contract which holds zero-knowledge rollup state. It's the core solution component. All transactions are sent here
* ****[**Relayer**](relayer-node/)**:** An intermediate actor between users and the Pool. The Relayer receives user transactions, calculates zkSNARKs and sends transactions to the Pool in a serial manner. While users can send transactions directly to the Pool, the collision probability increases (and user transactions can be reverted due to incorrect rollup state), so it makes sense to send to the Relayyer.
* ****[**Operator Manager**](contracts-and-circuits/operator-manager-contract/)**:** The contract which manages access to the Pool. It helps to set the single relayer active for the some period of time or provide unlimited access to the Pool
* **Application**: The solution front-end and user interaction point. All transaction are initiated here. The application synchronises a user account with the rollup, and helps to create transactions.
* **Bridge**: Currently under development. Bridges can deposit the user's funds from the other networks (e.g. Ethereum) to the Pool directly.

