---
description: Parameters needed to create a tx
---

# Transaction Constraints

## <mark style="background-color:green;">Getting Pool Limits</mark>

Different privacy pools have different limits for deposit and withdraw operations. Limits can also depend on the user's `0x`-address (address can be whitelisted).

```typescript
async getLimits(address?: string, directRequest: boolean = false): Promise<PoolLimits>
```

### Parameters

* `address`:  An address to be used for evaluating limits. Zero-address is used if undefined.
* `directRequest`: Request limits from the pool contract when `true` (otherwise, request from the relayer node).

### Returns

`Promise` returns [PoolLimits](../common-types.md#pool-limits)

### Example

```typescript
const limits = await zkClient.getLimits('0x0ECD9494F9C1F98C07E5319273C75BEF6232E86D');
console.log(`You can deposit up to ${limits.deposit.total} BOB right now`);
```

## <mark style="background-color:green;">Minimum Transaction Amount</mark>

The transaction amount cannot be less than the return value. This is applicable for each transaction type (for multi-transfer tx each note is must meet this minimum value).

```typescript
async minTxAmount(): Promise<bigint>
```

### Returns

`Promise` returns minimum transaction amount in the pool dimension.

### Example

```typescript
const minTx = await zkClient.minTxAmount();
if (requestedAmount < minTx) {
    console.log(`Requested too small amount to transact!`);
}
```

## <mark style="background-color:green;">Maximum Supported Token Swap During Withdraw</mark>

Privacy pools have the optional ability to swap an amount of tokens to native coins during a withdraw transaction (typically to seed a wallet with native tokens for operations). The following method returns the maximum number of tokens that can be swapped to native coins.

```typescript
async maxSupportedTokenSwap(): Promise<bigint>
```

{% hint style="info" %}
The swap is unavailable if `maxSupportedTokenSwap` returns 0
{% endhint %}

### Returns

`Promise` returns maximum number of tokens available to swap to native coins (in the pool dimension).

### Example

```typescript
const maxSwap = await zkClient.maxSupportedTokenSwap();
if (maxSwap > 0n) {
    console.log(`Congrats! You can swap tokens to the native coins!`);
}
```
