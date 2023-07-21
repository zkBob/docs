---
description: Low-level routines to interact with the a local Merkle tree
---

# Account State

## <mark style="background-color:green;">Sync the Local State</mark>

To update the account balance local state should be periodically synced with the relayer. Most routines (which are state dependent) have an associated parameter for updating state, but you may want to force update the account state (e.g. using a timer) to reduce sync delays and get balance updates in time.

```typescript
async updateState(): Promise<boolean>
```

### Returns

`Promise` returns boolean indicating whether your local state has pending outgoing transactions

{% hint style="info" %}
You cannot send a new transaction while there is an outgoing one from your account queued by the relayer but not yet mined.
{% endhint %}

### Example

```typescript
await zkClient.updateState()
console.log('Your local state has been updated');
// output: Your local state has been updated
```

## <mark style="background-color:green;">Check Transaction Sending Ability</mark>

You cannot send a new transaction while there is an outgoing one from your account queued by the relayer but not yet mined. Use the following function to check whether you can send a new transaction.

```typescript
async isReadyToTransact(): Promise<boolean>
```

{% hint style="info" %}
The routine is currently identical to `updateState()` but other conditions can be introduced here in the future&#x20;
{% endhint %}

{% hint style="info" %}
Invoking this function causes a local state update
{% endhint %}

### Returns

`Promise` returns boolean indicating whether you can send a new transaction

### Example

```typescript
const res = await zkClient.isReadyToTransact();
console.log(`You can${res ? '' : 'not'} send a new transaction right now`);
// output: You can send a new transaction right now
```

## <mark style="background-color:green;">Wait for Transaction Sending Ability</mark>

When the `isReadyToTransact()` method returns false you can wait for the appropriate conditions to send a new transaction using the following method:

```typescript
async waitReadyToTransact(): Promise<boolean>
```

{% hint style="info" %}
The routine attempts to update the local state periodically within a limited time interval (about 5 minutes). When all of attempts are exhausted the method returns `false.`
{% endhint %}

### Returns

`Promise` returns boolean indicating whether you can send a new transaction

### Example

```typescript
if (await zkClient.waitReadyToTransact()) {
    console.log('Let\'s send a transaction!');
} else {
    console.log('Sorry, I cannot wait anymore');
}
// output: Let's send a transaction!
```

## <mark style="background-color:green;">Get the Local State</mark>

Get the local Merkle tree index and root at the desired index

```typescript
async getLocalState(index?: bigint): Promise<TreeState>
```

<details>

<summary>Related Methods</summary>

* [getPoolState(index?: bigint)](../account-less-mode-operations/getting-the-state.md#getting-pool-contract-state)
* [getRelayerState()](../account-less-mode-operations/getting-the-state.md#getting-relayer-state)
* [getRelayerOptimisticState()](../account-less-mode-operations/getting-the-state.md#getting-relayer-optimistic-state)

</details>

### Parameters

`index` - the index for which the root should be retrieved (use the latest index if undefined, should be multiple of 128)&#x20;

### Returns

`Promise` returns [TreeState](../common-types.md#tree-state)

### Example

```typescript
const localState = await zkClient.getLocalState();
console.log(`The local state: ${localState.root} @ ${localState.index}`);
// output: The local state:
// 20259123668790783065614334268308370728058669663334716067122266810210516357394 @ 533760
```

## <mark style="background-color:green;">Clean the Local State</mark>

Remove all local Merkle tree nodes. After the state is cleared a full sync must be performed for the state to be ready.

```typescript
public async cleanState(): Promise<void>
```

### Example

```typescript
await zkClient.cleanState();
```

## <mark style="background-color:green;">Rollback the Local State</mark>

Use the following method in to remove all state data after the desired index

```typescript
async rollbackState(index: bigint): Promise<bigint>
```

### Parameters

`index` - the index after which the state should be cleared (should be multiple of 128)

### Returns

`Promise` returns new local Merkle tree index

{% hint style="info" %}
In some cases the new Merkle tree index may not match the desired rollback index (e.g. in the case of a partial tree)
{% endhint %}

### Example

```typescript
const newIndex = await zkClient.rollbackState(528000n);
console.log(`State rollbacked to index ${newIndex}`);
// output: State rollbacked to index 528000
```
