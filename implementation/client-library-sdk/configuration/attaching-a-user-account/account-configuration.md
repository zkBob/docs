---
description: Configure the customer's wallet
---

# Account Configuration

During client onboarding you should first request unique account credentials (mnemonic phrase, Metamask signature etc), then you can login the user. Fill the following configuration before starting:

```typescript
interface AccountConfig {
  sk: Uint8Array;
  pool: string;
  birthindex?: number;
  proverMode: ProverMode;
}
```

### **AccountConfig.sk**

**`AccountConfig.sk`** is a spending key - the top secret account credentials. Anyone who know it can get full control over the client's funds.

{% hint style="info" %}
To produce a valid spending key from the mnemonic phrase use the [`deriveSpendingKeyZkbob`](../../utilities.md#deriving-spending-key-from-the-mnemonic) helper routine.
{% endhint %}

### **AccountConfig.pool**

**`AccountConfig.pool`** is a pool alias which should be activated on login. For example you can initialize the client to support multiple pool configurations (sepolia/goerli) and want to activate goerli pool after client login. The pool can be switched later without logout.

### **AccountConfig.birthindex**

**`AccountConfig.birthindex`** is an account "birthday" within the Merkle tree. No transactions associated with the account should exist lower than that index. If you create a _NEW_ account you can pass `-1` here to create account with the birthindex which equals the current one. Always use `undefined` if you do not known the index exactly to avoid loss of any assets.

{% hint style="danger" %}
Please use this field with care because if the client account has been initialized with the incorrect `birthindex` the input transfers sent to the account before that index could be lost.
{% endhint %}

### **AccountConfig.proverMode**

**`AccountConfig.proverMode`** defines the prover behavior. The following modes are supported:

* `ProverMode.Local` - using local prover. It's the most secure way (because you won't share transaction details with 3rd-parties). But it could be slow on weak devices
* `ProverMode.Delegated` - send proving request to the designated external server (the server URL must be defined in associated `Pool.delegatedProverUrls` field). In case of any errors during external proving (e.g. in case of prover unavailable) the transaction will rejected. Please keep in mind the remote prover will have access to the transaction details
* `ProverMode.DelegatedWithFallback` - try to use external prover; in case of any error the local proving will be used

### Account  Configuration Example

```typescript
const accountConfig: AccountConfig = {
  sk: Uint8Array.from([199,146,184,107,97,216,254,23,76,10,31,212,74,35,170,141,
                       182,77,24,244,217,79,158,53,176,73,180,201,175,75,132,1]),
  pool: 'BOB-sepolia',
  birthindex: 0,
  proverMode: ProverMode.Local,
};
```
