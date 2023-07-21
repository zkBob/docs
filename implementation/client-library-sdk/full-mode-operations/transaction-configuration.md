---
description: Getting transaction parts and maximum amount to transfer/withdraw
---

# Transaction Configuration

## <mark style="background-color:green;">Getting Transaction Parts</mark>

The user's request to send or withdraw money may produce several transactions to the privacy pool in the common case. It depends on both a local account/notes configuration and transfer destinations amount as well. The following method is used to evaluate transactions needed to process request

```typescript
async getTransactionParts(
    txType: TxType,
    transfers: TransferRequest[],
    relayerFee?: RelayerFee,
    withdrawSwap: bigint = 0n,
    updateState: boolean = true,
    allowPartial: boolean = false,
): Promise<Array<TransferConfig>>
```

### Parameters

`txType` is transaction type (a member of [TxType](../common-types.md#transaction-type) enum)

{% hint style="info" %}
This method supports just a `TxType.Transfer` and `TxType.Withdraw` transaction types only (deposits are always performed within single transaction). The internal error will thrown for other tx types
{% endhint %}

`transfers` - a set of transfer requests (use single request with requested amount for withdrawal as well)

{% hint style="info" %}
The request's `destination` field is ignored in this method
{% endhint %}

`relayerFee` - a raw [relayer fee object](../common-types.md#relayer-raw-fee) which will be used to estimate total transaction fee (will requested under the hood when undefined)

`withdrawSwap` is an optional amount of tokens which should swap in withdraw transaction. It may influence the typical withdraw transaction cost due to extra fee component (ignored for other transaction types)

`updateState` - update the state before parts evaluating

`allowPartial` - try to build result even in case of insufficient balance

### Returns

`Promise` returns array of [TransferConfig](../common-types.md#transfer-config)s which describe all transactions needed to process input request, or a void array if request cannot be processed (e.g. in case of insufficient funds)

### Example

```typescript
const parts = await zkClient.getTransactionParts(
    TxType.Withdraw,
    [{
        destination: '0x49C92c016d2c7A245aAF5351BD932D9D61536eC0',
        amountGwei: 5000000000n // withdraw 5 BOB
    }],
    undefined,    // fetch relayer fee under the hood
    1000000000,    // swap 1 BOB
);
console.log(`This operation requires ${parts.length} transaction(s)`);
// output: This operation requires 4 transaction(s)
```

## <mark style="background-color:green;">Getting Maximum Available Outgoing Transaction</mark>

Calculating maximum available amount for transfers and withdrawals. This estimation doesn't take into account pool contract limits

```typescript
async calcMaxAvailableTransfer(
    txType: TxType,
    relayerFee?: RelayerFee,
    withdrawSwap: bigint = 0n,
    updateState: boolean = true
): Promise<bigint>
```

<details>

<summary>See Also</summary>

* [minTxAmount()](../account-less-mode-operations/transaction-constraints.md#minimum-transaction-amount)

</details>

### Parameters

`txType` is transaction type (a member of [TxType](../common-types.md#transaction-type) enum)

{% hint style="info" %}
This method supports just a `TxType.Transfer` and `TxType.Withdraw` transaction types only (you can deposit any amount in the limit boundaries). The internal error will thrown for other tx types
{% endhint %}

`relayerFee` - a raw [relayer fee object](../common-types.md#relayer-raw-fee) which will be used to estimate total transaction fee (will requested under the hood when undefined)

`withdrawSwap` is an optional amount of tokens which should swap in withdraw transaction. It may influence the typical withdraw transaction cost due to extra fee component (ignored for other transaction types)

`updateState` - update the state before parts evaluating

### Returns

`Promise` returns token amount in the pool dimension

### Example

```typescript
const maxAmount = await zkClient.calcMaxAvailableTransfer(TxType.Transfer);
console.log(`You can transfer up to ${maxAmount} BOB`);
// output: You can transfer up to 234.56 BOB
```
