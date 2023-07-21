---
description: Instantiating the client object
---

# Initializing the client

Before interacting with the privacy pool you must instantiate the `ZkBobClient` object. Use the static factory method to create a `ZkBobClient` instance. Using a constructor is not supported.

```typescript
static async create(
    config: ClientConfig,
    activePoolAlias: string
): Promise<ZkBobClient>
```

### Parameters

`config` - the [client configuration](client-configuration.md) which defines available pools, associated chains and other parameters.

`activePoolAlias` - the name of the pool which should be activated during instance creation. The names of the pools (aka aliases) are defined in the client configuration. The client should always have an active pool.

### Returns

An instance of the client in a `Promise`

### Example

The client configuration `clientConfig` defined in [this example](client-configuration.md#the-client-library-multipool-configuration-example).

```typescript
console.log('Creating ZkBob client...');
const zkClient = await ZkBobClient.create(clientConfig, 'BOB-sepolia');
console.log('You can dive into a privacy pool right now!');
```
