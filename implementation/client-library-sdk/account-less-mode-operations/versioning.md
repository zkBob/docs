---
description: Library, relayer and prover version information
---

# Versioning

## <mark style="background-color:green;">Get the Library Version</mark>

```typescript
getLibraryVersion(): string
```

### Returns

Version string as defined in the `package.json` file

### Example

```typescript
console.log(`You are using client library v${zkClient.getLibraryVersion()}`);
// output: You are using client library v5.4.0
```

## <mark style="background-color:green;">Get the Relayer Version</mark>

```typescript
async getRelayerVersion(): Promise<ServiceVersion>
```

### Returns

`Promise` returns [`ServiceVersion`](../common-types.md#service-version): current relayer version

### Example

```typescript
const relayerVer = await zkClient.getRelayerVersion();
console.log(`We are communicating with relayer ${relayerVer.ref}`);
// output: We are communicating with relayer v4.3.0
```

## <mark style="background-color:green;">Get the Delegated Prover Version</mark>

```typescript
async getProverVersion(): Promise<ServiceVersion>
```

{% hint style="info" %}
The method will throw an `InternalError` if the delegated prover isn't configured for the current pool during client initialization.
{% endhint %}

### Returns

`Promise` returns [`ServiceVersion`](../common-types.md#service-version): current delegated prover version

### Example

```typescript
try {
    const proverVer = await zkClient.getProverVersion();
    console.log(`Delegated prover ${relayerVer.ref}`);
} catch (err) {
    console.log('Delegated prover is unavailable');
}
// output: Delegated prover v0.1.0
```

