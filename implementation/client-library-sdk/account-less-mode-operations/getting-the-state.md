---
description: 'The state of the Merkle tree: relayer and contract'
---

# Getting the State

The privacy pool's state is a set of the Merkle tree root and its current index ( additional details [here](../../untitled/)). The state is described by the [TreeState interface](../common-types.md#tree-state). In normal operations the client's local state should match both the relayer and the pool contract state. However there is no local state in the accountless mode, but we can monitor relayer and pool states.

The relayer node has two different states: the regular state (which should match the pool contract) and the optimistic one. The optimistic state contain transactions which will be included into the state but are not processed yet. In other words the optimistic state is a most likely future Merkle tree state. The optimistic index should always be greater or equal to the normal state.

The client local state should be up to date with the relayer state. Use the associated full-mode method [getLocalState(index?)](../full-mode-operations/account-state.md#getting-the-local-state) to retrieve.

## <mark style="background-color:green;">Get Pool Contract State</mark>

This is the primary state. All subsystems (relayer, client) must be synced with the pool state.

```typescript
async getPoolState(index?: bigint): Promise<TreeState>
```

### Parameters

`index` - the index of the merkle tree root to retrieve (use the latest index if undefined)&#x20;

### Returns

`Promise` returns [TreeState](../common-types.md#tree-state)

### Example

```typescript
const poolState = await zkClient.getPoolState();
console.log(`The pool contract actual state: ${poolState.root} @ ${poolState.index}`);
// output: The pool contract actual state:
// 20259123668790783065614334268308370728058669663334716067122266810210516357394 @ 533760
```

## <mark style="background-color:green;">Get Relayer State</mark>

This should match the pool state. Only the latest state can be requested, there is no way to specify an index.

```typescript
async getRelayerState(): Promise<TreeState>
```

### Returns

`Promise` returns [TreeState](../common-types.md#tree-state)

### Example

```typescript
const relayerState = await zkClient.getRelayerState();
console.log(`The relayer state: ${relayerState.root} @ ${relayerState.index}`);
// output: The relayer state:
// 20259123668790783065614334268308370728058669663334716067122266810210516357394 @ 533760
```

## <mark style="background-color:green;">Get Relayer Optimistic State</mark>

The forcasted state by the relayer. This can be used to monitor transaction queue length. The index of the optimistic state should be greater or equal the index of the current state.

```typescript
async getRelayerOptimisticState(): Promise<TreeState>
```

### Returns

`Promise` returns [TreeState](../common-types.md#tree-state)

### Example

```typescript
const opState = await zkClient.getRelayerOptimisticState();
console.log(`The relayer optimistic state: ${opState.root} @ ${opState.index}`);
// output: The relayer state:
// 12637519184649269054381762592793608281145118612151270269221975452396577578313 @ 533888
```
