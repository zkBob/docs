---
description: EVM-based
---

# Smart Contracts

The zkBob solution based on several related smart contracts. The main purpose of the contract subsystem is to store current [Merkle tree](../untitled/) state inside the base blockchain. Each zkBob transaction changes the Merkle tree, so it should be processed by smart contract. The overall contract subsystem presented below

![The zkBob Smart Contracts Subsystem](../../.gitbook/assets/contracts\_240dpi.png)

The Pool contract is the main contract which holds the current Merkle tree state. It process all transactions and holds a current Merkle tree root.

The Token contract is a coin protected by current zkBob solution. This token is deposited in the Pool contact and withdraw from it.

The Pool contract uses verifiers contracts to check transaction correctness.

The operator contract helps the Pool contract to determine whether transactions can be accepted from a concrete sender at the moment. It's using in the multi-relayer configuration to serialize transaction sequence from the different nodes and minimize transaction collisions count.

The Voucher token is minted by the Pool to rewards users for their contribution in the anonymity set. It's token equivalent of the [energy](../../in-development/energy-token.md).

**TODO:**

* [x] Contracts overview
* [ ] Pool contract
* [ ] Tree and Tx verifiers
* [ ] Direct withdrawal requests
* [ ] Offset table (used on contract side)

