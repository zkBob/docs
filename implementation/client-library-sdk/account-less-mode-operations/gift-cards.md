---
description: Encoding and decoding URLs for gift cards
---

# Gift Cards

[#getting-gift-card-actual-balance](../full-mode-operations/gift-cards-maintenance.md#getting-gift-card-actual-balance "mention"): When distributing a gift-card several parameters are provided to the user including the spending key, birth index, balance, pool address and so on. The easiest way to achieve this is to encode these parameters into the URL. The following methods are intended for creating and parsing a gift card.

{% hint style="info" %}
Use gift card codes with care. Anyone who knows the code has full access to the gift card funds.
{% endhint %}

## <mark style="background-color:green;">Encoding Gift-Card Parameters</mark>

To create gift-card URL code invoke the following method:

```typescript
async codeForGiftCard(giftCard: GiftCardProperties): Promise<string>
```

### Parameters

`giftCard` - a [GiftCardProperties](../common-types.md#gift-card-properties) object which contains all needed parameters to encode

### Returns

`Promise` returns Base58-encoded string which can be injected into the redeeming URL

### Example

```typescript
const gk: GiftCardProperties = {
    sk: new Uint8Array(
        [ 40, 169, 173, 13, 42, 145, 224, 222, 213, 124, 226, 142, 126, 241, 6, 1,
          42, 133, 48, 12, 96, 66, 213, 158, 112, 225, 75, 198, 172, 82, 148, 3 ]
    ),
    birthIndex: 533888,
    poolAlias: 'BOB-sepolia',
    balance: 10000000000n
};
const code = await zkClient.codeForGiftCard(gk);
const baseURL = 'https://staging--zkbob.netlify.app';
console.log(`Redeem gift-card with: ${baseURL}/?gift-code=${code}`);
// output: Redeem gift-card with: 
// https://staging--zkbob.netlify.app/?gift-code=QvHXyAF2ykRCSTCwiLJbGGJVjJX7M8Xp5vfNNLaiEvwV8BQfYBeR6ivtY7svMpPyCsL6huTHpB
```

## <mark style="background-color:green;">Decoding a Gift-Card Code</mark>

Use the following method to retrieve a gift-card from the code or URL containing the code:

```typescript
async giftCardFromCode(code: string): Promise<GiftCardProperties>
```

<details>

<summary>Related Methods</summary>

* [giftCardBalance(giftCard: GiftCardProperties)](../full-mode-operations/gift-cards-maintenance.md#getting-gift-card-actual-balance)
* [redeemGiftCard(giftCard:GiftCardProperties, preferredProvingMode?: ProverMode)](../full-mode-operations/gift-cards-maintenance.md#gift-card-redemption)

</details>

### Parameters

`code` - a gift-card code or URL contained code within the `gift-code` query parameter.

### Returns

`Promise` returns the [GiftCardProperties](../common-types.md#gift-card-properties) of a decoded card. Errors may return `InternalError`.

### Example

```typescript
const url = 'https://staging--zkbob.netlify.app/?gift-code=QvHXyAF2ykRCSTCwiLJbGGJVjJX7M8Xp5vfNNLaiEvwV8BQfYBeR6ivtY7svMpPyCsL6huTHpB';
try {
    const gk = await zkClient.giftCardFromCode(url);
    console.log(`This card with balance ${gk.balance} intended for ${gk.poolAlias} pool`);
} catch (err) {
    console.log(`An error was occured while parsing the gift-card: ${err.message}`);
}
// output: This card with balance 100000000000 intended for BOB-sepolia pool
```
