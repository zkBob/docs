---
description: Using ephemeral 0x-accounts served on the library side
---

# Ephemeral Deposits

The ephemeral deposit scheme was designed to give the ability to deposit to a zk-account from the smart contracts (e.g. bridges). The idea is to temporary give control over the deposited funds to some EOA, which can then make a regular permittable deposit.

Such an EOA is an ad-hoc generated account derived from the zk-account spending key. So the library controls ephemeral private keys and has full access over the funds on the ephemeral addresses

Since deposits to a single zkBob account can be made from different smart contract wallets, reusing the same ephemeral EOA address is not a good idea, as it can be used to link together independent deposits. A better option is to use a newly generated EOA address for each new deposit.

{% hint style="warning" %}
Using ephemeral deposit scheme is an early developed feature. At now the [direct deposits](direct-deposits.md) are more suitable to process external deposits
{% endhint %}

## <mark style="background-color:green;">Sending Ephemeral Deposits</mark>

To use an ephemeral deposit you should send funds to the ephemeral address first. The address must have a sufficient balance to process the deposit and cover the relayer fee.

```typescript
async depositEphemeral(
    amountGwei: bigint,
    ephemeralIndex: number,
    relayerFee?: RelayerFee,
): Promise<string>
```

### Parameters

`amountGwei` - token amount to deposit into an account (in pool dimension).

`ephemeralIndex` - an index of the ephemeral address.&#x20;

`relayerFee` - a raw [relayer fee object](../common-types.md#relayer-raw-fee) which will be used to estimate the total transaction fee (will requested under the hood when undefined).

### Returns

`Promise` returns `jobId` returned by relayer which can be use to monitor the transaction.

### Example

```typescript
const myAddress = await zkClient.directDeposit(90000000000n, 0);
console.log(`Ephemeral deposit sent to the relayer (job ID = ${jobId})`)
// output: Ephemeral deposit sent to the relayer (job ID = 4736)
```

## <mark style="background-color:green;">Getting the First Non-Used Ephemeral Address Index</mark>

Scanning over the ephemeral addresses pool to find the first address which was not in use. The address is considering to be non-used if token balance, native balance, native and permit nonces are zero.

```typescript
async getNonusedEphemeralIndex(): Promise<number>
```

### Returns

`Promise` returns index of the first non-used ephemeral address.

### Example

```typescript
const idx = await getNonusedEphemeralIndex();
console.log(`Found nonused ephemeral address at index ${idx}`);
// output: Found nonused ephemeral address at index 3
```

## <mark style="background-color:green;">Getting Ephemeral Address at Index</mark>

The library generates ephemeral addresses with [BIP32](https://github.com/bitcoin/bips/blob/master/bip-0032.mediawiki) (hierarchical deterministic wallets). So the every address has an index (the last HD path component).

```typescript
async getEphemeralAddress(index: number): Promise<EphemeralAddress>
```

### Parameters

`index` - an index of requested ephemeral address.&#x20;

### Returns

`Promise` returns [EphemeralAddress](../common-types.md#ephemeral-address) object.

### Example

```typescript
const ephAddr = await getEphemeralAddress(0);
console.log(`First ephemeral address: ${ephAddr.address}`);
// output: First ephemeral address: 0x8ff66a5491a15ac67c596d1e9a6290e56dd4d156
```

## <mark style="background-color:green;">Getting All Used Ephemeral Addresses</mark>

Request details of all ephemeral addresses which were already used.

```typescript
async getUsedEphemeralAddresses(): Promise<EphemeralAddress[]>
```

### Returns

`Promise` returns array of [EphemeralAddress](../common-types.md#ephemeral-address) objects.

### Example

```typescript
const used = await getUsedEphemeralAddresses();
console.log(`$Used addresses: {used.map((a) => a.address).join(`,\n`)}`);
// output: Used addresses: 0x8ff66a5491a15ac67c596d1e9a6290e56dd4d156,
//         0x8434e839e0fa967fb7b9f624c381d533bcbce05d,
//         0xa78b9d09b307a972cae3be39f9182b7065fb15f4
```

## <mark style="background-color:green;">Retrieving Number of Token Transfers To the Address</mark>

```typescript
async getEphemeralAddressInTxCount(index: number): Promise<number>
```

### Parameters

`index` - an index of the ephemeral address.

### Returns

`Promise` returns number of incoming token transfers to the ephemeral address with the requested index.

### Example

```typescript
const cnt = await getEphemeralAddressInTxCount(0);
console.log(`Incoming token transfers: ${cnt}`);
// output: Incoming token transfers: 1
```

## <mark style="background-color:green;">Retrieving Number of Token Transfers From the Address</mark>

```typescript
async getEphemeralAddressInTxCount(index: number): Promise<number>
```

### Parameters

`index` - an index of the ephemeral address&#x20;

### Returns

`Promise` returns number of outgoing token transfers to the ephemeral address with the requested index.

### Example

```typescript
const cnt = await getEphemeralAddressInTxCount(0);
console.log(`Outgoing token transfers: ${cnt}`);
// output: Outgoing token transfers: 1
```

## <mark style="background-color:green;">Getting the Ephemeral Address Private Key</mark>

{% hint style="danger" %}
Use this method only for emergency reasons. Everyone who has the private key has full control over the funds on that ephemeral address.
{% endhint %}

```typescript
getEphemeralAddressPrivateKey(index: number): string
```

### Parameters

`index` - an index of the ephemeral address&#x20;

### Returns

A string with the private key in the hex representation

### Example

```typescript
const privKey = getEphemeralAddressPrivateKey(1);
console.log(`Private key: ${privKey}`);
// output: Private key: 2c7c5924e695bd0aad2145641f92fe3d95faf13d236dba7978c138fb6045ba3c
```
