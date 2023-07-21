---
description: Between native and pool dimensions
---

# Converting Token Amounts

Each pool contains a `denominator` property which is defined during the pool contract deployment. Token amounts are always converted to the denominated form when interacting with a pool. All operations with tokens are performed in the pool denominated realm (we also call it pool or shielded dimension). The following functions perform conversions between the shielded token and the native one.

{% hint style="info" %}
The native amount is named wei, which is a misnomer. Historically pools only held the BOB token (which has 18 decimals natively). Now the library supports pools with different decimal places and `wei` isn't the correct name. This will be updated in future versions.
{% endhint %}

## <mark style="background-color:green;">Native to Shielded</mark>

Convert native tokens to the pool dimension. The result is always rounded down.

```typescript
async weiToShieldedAmount(amountWei: bigint): Promise<bigint>
```

### Parameters

`amountWei`: token amount in the native dimension (in `wei` for most ERC20 tokens)

### Returns

`Promise` returns `bigint`: amount representation in the current pool dimension (rounded down if needed).

### Example

```typescript
// ...working on BOB-sepolia pool...
const nativeAmount = 123456789123456789123n; // ~123.46 BOB
const shieldedAmount = await zkClient.weiToShieldedAmount(nativeAmount);
console.log(`${nativeAmount} native tokens -> ${shieldedAmount} shielded tokens`);
// output: 123456789123456789123 native tokens -> 123456789123 shielded tokens
```

## <mark style="background-color:green;">Shielded to Native</mark>

Convert pool tokens from the pool dimension to the native dimension.

```typescript
async shieldedAmountToWei(amountShielded: bigint): Promise<bigint>
```

### Parameters

`amountShielded`: token amount in the pool dimension (denominated value).

### Returns

`Promise` returns `bigint`: amount representation in the native token dimension (rounded down if needed).

### Example

```typescript
// ...working on BOB-sepolia pool...
const shieldedAmount = 42n * (10n ** 9n); // 42 BOB
const nativeAmount = await zkClient.shieldedAmountToWei(shieldedAmount);
console.log(`${shieldedAmount} shielded tokens -> ${nativeAmount} native tokens`);
// output: 42000000000 shielded tokens -> 42000000000000000000 native tokens
```
