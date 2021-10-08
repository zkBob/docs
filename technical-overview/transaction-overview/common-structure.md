---
description: Public and secret parts
---

# Common Structure

The transaction transferred to the zkBob contract contains the following fields:

* Account nullifier - helps protect from the double-spending
* Transaction commitment - transaction's subtree root hash
* Transfer index
* Energy amount
* Token amount
* Transaction proof
* Merkle tree root after transaction including
* Merkle tree proof
* Transaction type
* Transaction specific fields \(depends on transaction type\)
* Memo block which contain encrypted transaction details \(accounts and notes\)

In general, a transaction sender must prepare all of these fields before submitting to the contract. In case of using relayer it should calculate proofs and send the transaction to the contract.

The sender forms two transaction parts when it's created. There are public and secret parts for the transaction. The public part contains encrypted transaction data and other fields which cannot disclosure sender, receiver, internal transfer amount, etc. The secret transaction's part contains unencrypted data such as input and output accounts and notes, proofs and EDDSA signature.

#### The public transaction components

* The current Merkle tree root \(before transaction processing by the contract\)
* Input account nullifier
* Transaction commitment
* Delta value _**\(will be explained furthermore\)**_
* Memo block

#### The secret transaction components

* A set of unencrypted input\output account and notes for the transaction
* Input account and notes proofs
* Transaction signature $$(S, R)$$
* Account intermediate key $$A$$ to verify signature





