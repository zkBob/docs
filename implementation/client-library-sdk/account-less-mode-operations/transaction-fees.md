---
description: Requesting and estimation
---

# Transaction Fees

Each transaction should include a fee. This is a payment to the relayer for maintaining a request,  preparing, and sending a transaction to the pool contract. The fee is returned by the relayer and may vary for different reasons. Moreover different transactions require different fee amounts based on the calldata length. This is why the transaction fee must be calculated every time before sending a transaction in general.

The fee is always returned in the token denominated units (pool dimension). The relayer fee estimate follows the [_RelayerFee_](../common-types.md#relayer-raw-fee) _structure._

In general the transaction fee estimated on the client side follows this formula ( _`relayerFee`_ is the commission returned by relayer):

$$
fee(tx, relayerFee) = relayerFee.fee + relayerFee.oneByteFee * tx.calldata.length
$$

For withdrawal transactions with token swaps the equation is as follows:

$$
fee_{withdraw}^{swap}(tx, relayerFee) = fee(tx, relayerFee) 
 + relayerFee.nativeConvertFee
$$

It is not possible to define the absolute fee value when creating a transaction, but you may provide a [relayer raw fee ](../common-types.md#relayer-raw-fee)object. The final fee is calculated under the hood as described above. If the raw fee field is omitted, the raw fee will be automatically requested from the relayer.

## <mark style="background-color:green;">Getting Relayer Raw Fee</mark>

Request the fee estimation from the relayer. If a previous request was performed recently (<30 secs) the cached value will be returned.

```typescript
async getRelayerFee(): Promise<RelayerFee>
```

### Returns

`Promise` returns [`RelayerFee`](../common-types.md#relayer-raw-fee): actual raw fee contents.

### Example

```typescript
const relayerFee = await zkClient.getRelayerFee();
console.log(`Raw fee = ${relayerFee.fee} per tx ${relayerFee.oneByteFee} per byte`);
// output: Raw fee = 100000000 per tx 429035 per byte
```

## <mark style="background-color:green;">Estimating Transaction Typical Fee</mark>

Calculate the typical fee amount for the desired transaction type. It may be helpful to display the approximate fee before entering the transaction config.

```typescript
async atomicTxFee(txType: TxType, withdrawSwap: bigint = 0n): Promise<bigint>
```

{% hint style="info" %}
Keep in mind these are _typical_ fee values. In several cases the transaction fee may be different depending on the account or transaction configuration (e.g. multi-transfer transactions). To estimate the actual transaction fee please use the [feeEstimate](../full-mode-operations/fee-estimations.md#estimating-transaction-typical-fee) full mode method.
{% endhint %}

<details>

<summary>Related methods</summary>

* [feeEstimate( transfers, txType, withdrawSwap, updateState)](../full-mode-operations/fee-estimations.md#estimating-transaction-fee)
* [directDepositFee()](../full-mode-operations/direct-deposits.md#getting-direct-deposit-fee)

</details>

### Parameters



* `txType`: transaction type (a member of [TxType](../common-types.md#transaction-type) enum).
* `withdrawSwap`: An optional amount of tokens to swap in the withdrawal transaction. This may influence the typical withdraw transaction cost due to an additional fee component (ignored for other transaction types).

### Returns

`Promise` returns the absolute fee value for a typical transaction with the requested type (in tokens, pool dimension).

### Example

```typescript
const fee = await zkClient.atomicTxFee(TxType.BridgeDeposit);
console.log(`The typical deposit will cost you approx ${fee}`);
// output: The typical withdraw will cost you approx 505867110
```
