---
description: In the multi-pool configurations
---

# Switching Between Pools

{% hint style="info" %}
The following functions are available in both account-less and full modes
{% endhint %}

## <mark style="background-color:green;">Getting the Current Pool</mark>

The `ZkBobClient` object always operate on the concrete pool. There are no cases when the pool is undefined. All pools are named by aliases as specified in the [client configuration](initializing-the-client/client-configuration.md). To obtain the name of the current pool use the following method:

```typescript
currentPool(): string
```

### Returns

String alias of the currently activated pool (as defined in the initial config).

## <mark style="background-color:green;">Getting Available Pools</mark>

You also can get the list of pools specified in the client configuration.

```typescript
availabePools(): string[]
```

### Returns

Array of the all supported pool aliases (as defined in initial config).

## <mark style="background-color:green;">Switching to Another Pool</mark>

If you initialized the `ZkBobClient` object with a multipool configuration you can simply switch between pools using the following routine:

```typescript
async switchToPool(poolAlias: string, birthindex?: number): Promise<void>
```

### Parameters

* `poolAlias`: pool's name as defined in the client configuration.
* `birthindex`: optional parameter only applicable in full mode (when account is attached). It equals the index within the Merkle tree when the account was created. There must be no entries belonging to the account below this index. Always use `undefined` if you don't know the exact index.

{% hint style="danger" %}
**Double check that birthindex is correct**. If you switch to another pool with attached account and incorrect `birthindex`, the input transfers sent to the account before that index can be lost without the ability to recover.
{% endhint %}

### Returns

No value is returned but you must wait until the switch is completed before the next library interaction.

### Example

```typescript
const curPool = zkClient.currentPool();
const allPools = zkClient.availabePools();
const newPool = allPools.find(p => p != curPool);

console.log(`Working on ${curPool} pool`);
console.log(`Available pools: ${allPools.join(',')}`);

if (newPool) {
   console.log(`Switching to ${newPool} pool...`);
   await zkClient.switchToPool(newPool);
   console.log(`Welcome to ${zkClient.currentPool()} pool!`);
}
```
