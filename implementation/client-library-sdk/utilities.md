---
description: Auxiliary routines
---

# Utilities

The following functions do not belong to the `ZkBobClient` object and should be imported before using:

## <mark style="background-color:green;">Deriving Spending Key from the Mnemonic</mark>

```typescript
function deriveSpendingKeyZkBob(mnemonic: string): Uint8Array
```

### Parameters

`mnemonic` - 12-words [BIP39](https://github.com/bitcoin/bips/blob/master/bip-0039.mediawiki) valid mnemonic phrase (English dictionary)

### Returns

The spending key bytes array (32 bytes)

### Example

```typescript
const mnemonic = 'magic trophy foil direct marriage glad bench wash doctor risk end cheap';
const sk = deriveSpendingKeyZkBob(mnemonic);
const hexSk = [...sk].map(x => x.toString(16).padStart(2, '0')).join('')
console.log(`Your top secret key: 0x${hexSk}`);
// output:
// Your top secret key: 0xc792b86b61d8fe174c0a1fd44a23aa8db64d18f4d94f9e35b049b4c9af4b8401
```
