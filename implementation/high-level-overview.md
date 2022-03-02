---
description: Main system components
---

# High-level Overview

## Components&#x20;

zkBob solution is composed with the following components:

* ****[**Pool**](contracts-and-circuits/the-pool-contract/)**:** The main contract which holds zero-knowledge rollup state. It's the core solution component. All transactions are sent here
* ****[**Relayer**](relayer-node/)**:** An intermediate actor between users and the Pool. The Relayer receives user transactions, calculates zkSNARKs and sends transactions to the Pool in a serial manner. While users can send transactions directly to the Pool, the collision probability increases (and user transactions can be reverted due to incorrect rollup state), so it makes sense to send to the Relayer.
* ****[**Operator Manager**](contracts-and-circuits/operator-manager-contract/)**:** The contract which manages access to the Pool. It helps to set the single relayer active for the some period of time or provide unlimited access to the Pool
* ****[**Application**](../zkbob-getting-started/zkbob-app/): The solution front-end and user interaction point. All transaction are initiated here. The application synchronises a user account with the rollup, and helps to create transactions.
* **Bridge**: Currently under development. Bridges can deposit the user's funds from the other networks (e.g. Ethereum) to the Pool directly.

