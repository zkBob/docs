---
description: Calculating exact fee values for the different transactions
---

# Fee Estimations

## <mark style="background-color:green;">Estimate Transaction Fee</mark>

Calculate the relayer fee amount for the provided transaction configuration. A transaction request may produce several transactions, with the following method you have an ability to display fee details

```typescript
async feeEstimate(
    transfersGwei: bigint[],
    txType: TxType,
    withdrawSwap: bigint = 0n,
    updateState: boolean = true
): Promise<FeeAmount>
```

<details>

<summary>Related Methods</summary>

* [atomicTxFee(txType, withdrawSwap)](../account-less-mode-operations/transaction-fees.md#estimating-transaction-typical-fee)

</details>

### Parameters



* `transfersGwei` - a set of transfer amounts (ignored for all transactions except with `txType == TxType.Transfer`)
* `txType` is transaction type (a member of [TxType](../common-types.md#transaction-type) enum)
* `withdrawSwap` is an optional amount of tokens to swap in the withdraw transaction. This may influence the typical withdraw transaction cost due to the extra fee component (ignored for other transaction types).
* `updateState` - update the state before fee estimation if `true` (fee may depends on account and notes configuration)

### Returns

`Promise` returns [FeeAmount](../common-types.md#fee-amount-required-for-request) object with fee estimation

### Example

```typescript
const res = await zkClient.feeEstimate([100000000000, 12000000000], TxType.Transfer);
console.log(`The transfer will take ${res.txCnt} tx(s) and requires ${res.total} fee`);
// output: The transfer will take 1 tx(s) and requires 263573104 fee
```
