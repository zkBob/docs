---
description: Relayer lifecycle detailed description
---

# Relayer Operations

The relayer is a mediator between clients and zkBob contracts subsystem. So you should understand its role and operation details. This section describes typical relayer use cases.

### Fetching state

The user must keep and synchronize the current pool state to build proper transactions proofs. The pool state for the client is an ordering set of encrypted transactions ([memo blocks](../transaction-overview/untitled-1/)). The user should try to decrypt each of them to obtain his account and notes. To obtain this data client should use `eth_getLogs` method of the RPC endpoint. In case of a lot of users the RPC endpoints may become overloaded.

The relayer keeps the actual pool transaction set, synchronize it continuously and returns a desired set of transactions to the users. It significantly decreases mainnet nodes overhead.

### Sending transaction

When user wants to send a transaction, he must create its body (memo block), calculate corresponding tx proof and send it to the relayer. In that case he doesn't worry about the Merkle tree root. All he needs is to get actual state (balance and notes). All tree-related work will perform relayer.

**TBD**&#x20;

