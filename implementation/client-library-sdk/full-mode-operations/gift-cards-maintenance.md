---
description: Getting balance and redemption
---

# Gift Cards Maintenance

## <mark style="background-color:green;">Getting Gift Card Actual Balance</mark>

To retrieve a gift-card balance use the following method

```typescript
async giftCardBalance(giftCard: GiftCardProperties): Promise<bigint>
```

<details>

<summary>See Also</summary>

* [giftCardFromCode(code: string)](../account-less-mode-operations/gift-cards.md#decoding-gift-card-code)

</details>

### Parameters

`giftCard` - [gift card object](../common-types.md#gift-card-properties) which contained all information needed to operate

{% hint style="info" %}
You can get gift card object from the source URL by invoking method [gitfCardFromCode](../account-less-mode-operations/gift-cards.md#decoding-gift-card-code)
{% endhint %}

### Returns

`Promise` returns gift card balance in pool dimension

### Example

```typescript
const code = 'QvHXyAF2ykRCSTCwiLJbGGJVjJX7M8Xp5vfNNLaiEvwV8BQfYBeR6ivtY7svMpPyCsL6huTHpB';
try {
    const gk = await zkClient.giftCardFromCode(code);
    const balance = await zkClient.giftCardBalance(gk);
    console.log(`Actual gift card balance ${balance} BOB`)
} catch (err) {
    console.log(`An error was occured while parsing the gift-card: ${err.message}`);
}
// output: Actual gift card balance 100000000000 BOB
```

## <mark style="background-color:green;">Gift Card Redemption</mark>

You can send money from the gift-card to the your account with the following method

```typescript
async redeemGiftCard(
    giftCard: GiftCardProperties,
    preferredProvingMode?: ProverMode
): Promise<string>
```

<details>

<summary>See Also</summary>

* [giftCardFromCode(code: string)](../account-less-mode-operations/gift-cards.md#decoding-gift-card-code)

</details>

### Parameters

`giftCard` - [gift card object](../common-types.md#gift-card-properties) which contained all information needed to operate

{% hint style="info" %}
You can get gift card object from the source URL by invoking method [gitfCardFromCode](../account-less-mode-operations/gift-cards.md#decoding-gift-card-code)
{% endhint %}

`preferredProvingMode` - you can optionally set other [ProverMode](../common-types.md#prover-mode) for redemption process. E.g. you can use delegated prover to redemption process speed up (if configured) while your account using local prover only

### Returns

`Promise` returns job ID associated with redemption transaction

### Example

```typescript
const code = 'QvHXyAF2ykRCSTCwiLJbGGJVjJX7M8Xp5vfNNLaiEvwV8BQfYBeR6ivtY7svMpPyCsL6huTHpB';
try {
    const gk = await zkClient.giftCardFromCode(code);
    const jobId = await zkClient.giftCardBalance(gk);
    console.log(`The gift card was redeemed (job #${jobId})`)
} catch (err) {
    console.log(`An error was occured while redeeming the gift-card: ${err.message}`);
}
// output: The gift card was redeemed (job #843)
```
