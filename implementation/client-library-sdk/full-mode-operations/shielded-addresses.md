---
description: Used to transfer funds inside a privacy pool
---

# Shielded Addresses

## <mark style="background-color:green;">Generate Shielded Address (pool specific)</mark>

A regular shielded address for the currently selected privacy pool (aka pool-specific address).

```typescript
async generateAddress(): Promise<string>
```

{% hint style="info" %}
The shielded address has a human-readable prefix to indicate which privacy pool it belongs to. Do not remove this: the address without the prefix considered invalid.
{% endhint %}

### Returns

`Promise` returns the shielded address for the current pool.

### Example

```typescript
console.log(`${await zkClient.generateAddress()}`);
// output: zkbob_sepolia:MrjNRn4ja5ctEW5PVFkZDe6XG97ZNCCHtgchKGzUgbrQDYUf26PikByp61oDVD9
```

## <mark style="background-color:green;">Generate Universal Shielded Address</mark>

A universal shielded address for use with any privacy pool (aka generic address).

```typescript
async generateUniversalAddress(): Promise<string>
```

### Returns

`Promise` returns the shielded address for any pool

### Example

```typescript
console.log(`${await zkClient.generateAddress()}`);
// output: zkbob:6aSJjrJ7F6kcoEzvKwiYwFSWeGsPJ4rLyGiGVD6e1TYdRZdGffTcyKvmM4wHFse
```

## <mark style="background-color:green;">Generate Shielded Address for Another Account</mark>

You can also generate a pool-specific address for another user account. To generate, you must provide the account spending key.

```typescript
async generateAddressForSeed(seed: Uint8Array): Promise<string>
```

### Parameters

`seed` - spending key for the account generated address belongs to

{% hint style="info" %}
It's the same parameter as provided in the [`AccountConfig.sk`](../configuration/attaching-a-user-account/account-configuration.md) during the account attaching&#x20;
{% endhint %}

### Returns

`Promise` returns the shielded address for the current pool belonging to the provided spending key

### Example

```typescript
const mnemonic = 'magic trophy foil direct marriage glad bench wash doctor risk end cheap';
const sk = deriveSpendingKeyZkBob(mnemonic);
console.log(`${await zkClient.generateAddressForSeed(sk)}`);
// output: zkbob_sepolia:SZgsuNkez8MMZJ4tvVyNCUajQNu26agnZvqJmkxdNpcTmshdfSzA2sUW1fsPVPU
```

## <mark style="background-color:green;">Shielded Address Verification</mark>

```typescript
async verifyShieldedAddress(address: string): Promise<boolean>
```

### Parameters

`address` - pool-specific or generic shielded address

{% hint style="info" %}
Addresses without prefixes are deprecated, the only exception is the **USDC pool on Polygon where they are allowed**. Otherwise, prefix-less addresses will be marked as invalid.
{% endhint %}

### Returns

`Promise` returns `true` if address checksum is correct and can be used on the current privacy pool

### Example

```typescript
const address = 'zkbob:4NeCQJijr9GQKBUBkp61bdQiqB15sf42fvy3CKGeXjUqJR3GBrQKSRrkboJounM';
const isValid = await zkClient.verifyShieldedAddress(address)
console.log(`The checking address is ${!isValid ? 'IN' : ''}VALID`);
// output: The checking address is VALID
```

## <mark style="background-color:green;">Check if a Shielded Address Belongs to an Account</mark>

```typescript
async isMyAddress(address: string): Promise<boolean>
```

### Parameters

`address` - pool-specific or generic shielded address

{% hint style="info" %}
Addresses without prefixes are deprecated, the only exception is the **USDC pool on Polygon where they are allowed**. Otherwise, prefix-less addresses will be marked as invalid.
{% endhint %}

### Returns

`Promise` returns `true` if address checksum is correct, it can be used on the current privacy pool and it belongs to the current user account

### Example

```typescript
const address = 'zkbob_sepolia:SZgsuNkez8MMZJ4tvVyNCUajQNu26agnZvqJmkxdNpcTmshdfSzA2sUW1fsPVPU';
const isOwn = await zkClient.isMyAddress(address)
console.log(`The address is ${!isOwn ? 'not ' : ''}belongs to our account`);
// output: The address is belongs to our account
```

## <mark style="background-color:green;">Get Components of a Shielded Address</mark>

```typescript
async addressInfo(address: string): Promise<IAddressComponents>
```

### Parameters

`address` - pool-specific or generic shielded address

### Returns

`Promise` returns [`IAddressComponents`](../common-types.md#shielded-address-components) for the provided address

### Example

```typescript
const address = 'zkbob_sepolia:SZgsuNkez8MMZJ4tvVyNCUajQNu26agnZvqJmkxdNpcTmshdfSzA2sUW1fsPVPU';
const components = await zkClient.addressInfo(address)
console.log(`d = ${components.d}, P_d = ${components.p_d}`);
// output: d = 221091213303296764154858, P_d = 104205498421613002257722403946176839412231742105831354351312357543598985595
```
