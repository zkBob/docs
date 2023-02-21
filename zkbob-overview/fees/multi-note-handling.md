---
description: >-
  Processing of multiple notes for a single outgoing operation can result in
  additional fees
---

# Multi-note handling

{% hint style="info" %}
Multiple transactions are sometimes required when there are many unspent notes in an account.
{% endhint %}

zkBob uses an Unspent Transaction Output (UTXO) model with strict ordering. Incoming zkAccount transfers are ordered and referred to as '[notes](../../implementation/account-and-notes/notes.md)'. About notes:

* Notes are received as incoming transfers within the zkBob pool. They are collected in the receiver's zkAccount and displayed as part of the account's BOB balance.&#x20;
* Notes are collected in a FIFO (first-in-first-out) order.&#x20;
* Collected (unspent) notes are automatically aggregated and added to any outgoing transfer/ withdrawal transaction. A maximum of 3 notes can be included in 1 transaction.&#x20;

When an account has many incoming and outgoing transactions, notes are aggregated regularly (collected and spent) and do not build up.

However, in certain scenarios there may be a large number of unspent notes which are requested for processing in a single operation. In this case, multiple transactions are performed by the application for a single operation, with each transaction requiring a 0.10 BOB fee.&#x20;

## Example: Carl withdraws 20 BOB

Carl starts with a zkBob account funded with 10 BOB. He then receives 10 separate transfers through zkBob of 1 BOB each (ie 10 notes) from his friends. Now, Carl's total account balance displays 20 BOB. He decides to withdraw the entire 20 BOB.&#x20;

In this scenario there are 10 unspent notes that need to be processed to complete the entire operation. They are automatically processed in a series of 4 transactions.

1. **Tx #1**: Aggregates the first 3 notes of 1 BOB each and increases the account balance. The account balance becomes: `10 + 3x1 - 0.1(fee) = 12.9 BOB`
2. **Tx #2:** Aggregates next 3 notes -> acc = `12.9 + 3x1 - 0.1(fee) = 15.8 BOB`
3. **Tx #3**: Aggregates next 3 notes -> acc = `15.8 + 3x1 - 0.1(fee) = 18.7 BOB`
4. **Tx #4**: Aggregates the last note -> acc = `18.7 + 1 - 0.1(fee) = 19.6 BOB` and simultaneously makes an outgoing withdrawal for the full account balance, i.e. `19.6 BOB`

When the operation is complete, Carl receives 19.6 BOB, and 0.4 BOB is spent as fees for the 4 transactions.

## Example: Carl withdraws 15 BOB

If Carl wants to withdraw 15 BOB, the operation only requires 2 txs.&#x20;

1. **Tx #1**: Aggregates first 3 notes ->  `acc = 10 + 3x1 - 0.1(fee) = 12.9 BOB`
2. **Tx #2**: Aggregates next 3 notes -> `acc = 12.9 + 3x1 - 0.1(fee) = 15.8 BOB` and makes a simultaneous withdrawal of 15 BOB  `acc = 15.8 - 15 = 0.8 BOB` . In addition the account contains 4 unspent notes of 1 BOB each.

Carl receives 15 BOB, and 0.2 BOB is used to pay the transaction fees. His new zkAccount balance displays 4.8 BOB. His account consists of 4 unspent notes of 1 BOB each and 0.8 account balance, however this is abstracted for Carl so he only sees the total account balance of 4.8.









