---
description: The main system components
---

# High-level Overview

zkBob is the Layer 2 solution based on the zero-knowledge rollup. The main purpose of the solution is to make transactions anonymous. Nobody can reveal transaction details (such as sender, receiver, amount, etc) when you transfer funds to another user inside zkBob. The users are operate shielded tokens inside the Pool.

{% hint style="warning" %}
**Anonymity Set Warning**

Despite the fact that internal transaction details are hidden you can be compromised when entering in or leaving the solution in case of small anonymity set.

Imagine you want to send money to Alice through the zkBob. You decided to create a new account and deposit exact the necessary amount of tokens. Alice also creates account and provide her private address. You transfer funds to Alice and she makes a withdrawal transaction for all received tokens. In case of you and Alice are the only active users of the zkBob solution, any neutral observer can suggest your funds movement with high probability.

There are no time limits for the funds withdrawal. But we strongly recommend to stay inside the solution some extra time (the more the better) to increase the anonymity set. Such approach can be useful to avoid the cases described above. Moreover you will be rewarded for the staying inside the solution with extra [energy](energy.md)
{% endhint %}

zkBob solution is composed with the following components:

* ****[**The Pool**](contracts-and-circuits/the-pool-contract/) - the main contract which holds zero-knowledge rollup state. It's the core solution component. All transactions are sent here
* ****[**Relayer**](relayer-node/) - an intermediate actor between users and the Pool. Relayer receives user transactions, calculates zkSNARKs and sends transactions to the Pool in the serial manner. Users can send transactions to the Pool directly, but in this case the collision probability is increased (so user transaction can be reverted due to incorrect rollup state)
* ****[**Operator Manager**](contracts-and-circuits/operator-manager-contract/) - is the contract which manages access to the Pool. It helps to set the single relayer active for the some period of time or provide unlimited access to the Pool
* The application - is the solution front-end. It's the user interaction point. All transaction are initiated here. The application synchronises user account with the rollup, and helps to create transactions
* The bridge - is under development currently. The bridges can deposit the user's funds from the other networks (e.g. Ethereum) to the Pool directly

