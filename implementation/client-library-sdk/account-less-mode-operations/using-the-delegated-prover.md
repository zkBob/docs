---
description: To reduce proof time computation time
---

# Using the Delegated Prover

Each transaction to the privacy pool must be proven. The process is a heavy-computation process performed by the transaction sender. The library supports three proving modes:

* `Local` - The most secure case where no sensitive data sent to the 3rd parties. The hard computation is performed during the transaction proving on the user's device. This can take a long time with low performance devices. Moreover the proving parameters must be downloaded before transaction creation (\~70 Mb).
* `Delegated` - An external proving machine is used (aka Delegated Prover). In this case the unencrypted transaction is sent to the delegated prover to perform hard computations outside of the user's device. Using a properly configured heavy-duty dedicated server can significantly decrease proving time. The client shouldn't download proving parameters.&#x20;

{% hint style="danger" %}
A transaction will be rejected if the external prover is unavailable when the`Delegated` proving mode selected.
{% endhint %}

* `DelegatedWithFallback` - Combines the Delegated and Local modes (external prover is used as the primary one).

## <mark style="background-color:green;">Setting Prover Mode</mark>

The following command sets the specified prover mode. **The proving mode is set for the current pool only**. If you switch to a new pool the previously selected mode on the _new_ pool will be used (if it wasn't set yet - the mode from the old pool will selected).

```typescript
async setProverMode(mode: ProverMode): Promise<void>
```

{% hint style="info" %}
`Delegated` and `DelegatedWithFallback` modes can only be set when the current pool configuration contains a correct delegated prover URL which is available. Otherwise you will receive an InternalError.
{% endhint %}

### Parameters

`mode`: proving mode (a member of [ProverMode](../common-types.md#prover-mode) enum)

### Returns

No return value but you must wait until the switch is completed before the next library interaction.

### Example

```typescript
try {
    await zkClient.setProverMode(ProverMode.Delegated);
    console.log('The proving system was switched to Delegated mode successfully');
} catch (err) {
    console.log(`Cannot switch to delegated prover: ${err.message}`);
}
```

## <mark style="background-color:green;">Get Current Prover Mode</mark>

The following routine gets the current prover mode:

```typescript
getProverMode(): ProverMode
```

### Returns

[ProverMode](../common-types.md#prover-mode) enum member.

### Example

```typescript
if (zkClient.getProverMode() == ProverMode.Local) {
    console.log('Using local prover');
}
```
