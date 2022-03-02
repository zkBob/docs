---
description: Deposit, transfer, withdrawal
---

# Transaction Types

The current protocol implementation supports three transaction types: deposit, transfer and withdrawal. Each type has a numeric code included in the transaction calldata.

{% tabs %}
{% tab title="Deposit" %}
![The deposit flow](../../.gitbook/assets/deposit.png)

A deposit transaction helps to bring some external funds to the user account. It's supposed that the user who initiate the deposit transaction had made a token approval to the zkBob contract.

The deposit transaction has no input and output notes. The deposit amount should be added to the output account balance to consider incoming funds.

The deposit transaction will be additionally checked on the contract side. The approved tokens should be successfully transferred to the contract address to proceed transaction and update Merkle tree. Therefore user must include a deposit signature field to the transaction. This field contains account nullifier signed by the client's private key from the native chain. The contract will extract client public address via `ecrecover` Solidity function.

#### Transaction specific:

* Tx type = 0
* has no output notes
* `token_amount` field contains deposit magnitude (a positive value)
* `energy_amount` field equals 0
* The output account balance is increased to the deposit amount
* `depositSignature` field exist
{% endtab %}

{% tab title="Transfer" %}
![The internal transfer flow](../../.gitbook/assets/transfer.png)

This transaction move some funds to one or more internal (zkBob) receivers. The transfer transaction does not change the receiver's account immediately. Instead one or more payment notes are generated and sent inside the transaction's memo block.

Formally the transfer transaction emits an output account and output notes to push them in the Merkle tree

#### Transaction specific:

* Tx type = 1
* the output notes are acceptable in the memo block
* `token_amount` field equals 0
* `energy_amount` field equals 0
* the output account balance is decreased to the transfer magnitude
{% endtab %}

{% tab title="Withdrawal" %}
![The withdrawal flow](../../.gitbook/assets/withdrawal.png)

A withdrawal transaction move funds from zkBob account to the external destination point.                                       Destination address is specified in the `memo.receiver` field (a chain-specific address)

Each withdrawal transaction must zeroize account energy value. This value is converted into a voucher token which will be minted to the destination address. So `energy_amount` should be less or equal zero.

Withdrawal amount is specified in the `token_amount` field. This amount will be transferred to the destination address on transaction proceed.

{% hint style="warning" %}
#### Required further clarification

Withdrawal transaction supports the native coin redirecting mechanism. When relayer send a native coin to the contract within the withdrawal transaction (`memo.native_amount` should be equal coins amount), the contract should send native coins to the destination address
{% endhint %}



#### Transaction specific:

* Tx type = 2
* has no output notes
* `token_amount` contains token withdrawal magnitude (less or equal zero)
* `energy_amount` contains voucher token mint amount (less or equal zero)
*   memo block contains extra fields: `memo.native_amount` and `memo.receiver`

    * `memo.native_amount` contains native coins magnitude to withdraw
    * `memo.receiver` contains receiver for all of output payments


{% endtab %}
{% endtabs %}
