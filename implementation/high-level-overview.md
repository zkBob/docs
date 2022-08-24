---
description: Main system components
---

# zkBob Application Overview

## Components&#x20;

The zkBob application is comprised of the following components:

* ****[**Pool**](contracts-and-circuits/the-pool-contract/)**:** The main contract which holds the zero-knowledge rollup state. It's the core solution component. All transactions are sent here.
* ****[**Relayer**](relayer-node/)**:** An intermediate actor between users and the Pool. The Relayer receives user transactions, calculates zkSNARKs, and sends transactions to the Pool in a serial manner. While users can send transactions directly to the Pool, the collision probability increases (and user transactions can be reverted due to incorrect rollup state), so it makes sense to send to the Relayer.
* ****[**Operator Manager**](contracts-and-circuits/operator-manager-contract/)**:** The contract which manages access to the Pool. It can be used to activate a single relayer for a defined period of time or provide unlimited access to the Pool.
* ****[**Application**](../zkbob-app/zkbob-app.md): The solution front-end and UI. All transactions are initiated here. The application synchronises a user account with the rollup, and helps to create transactions.
* **Bridge**: Currently in research and development. Bridges can deposit the user's funds from the other networks (e.g. Ethereum) to the Pool directly.

