# Helpers

## <mark style="background-color:green;">Getting the Pool Identifier</mark>

Typically each pool has a unique `poolId`. The following method retrieves the currently selected pool ID:

```typescript
async poolId(): Promise<number>
```

{% hint style="info" %}
**Exception:** Polygon BOB and Sepolia BOB pools share the same `poolID` which is 0.
{% endhint %}

### Returns

`Promise` returns `number`: pool identifier

### Example

```typescript
console.log(`Working on the pool with ID: ${await zkClient.poolId()}`);
// output: Working on the pool with ID: 0
```

## <mark style="background-color:green;">Get the Network (Chain) Name</mark>

```typescript
networkName(): string
```

### Returns

Name of the current chain (e.g. `polygon`, `sepolia` etc). The name is retrieved locally from the integrated hard-coded mapping. The default value for unknown chains is `unknown-chain`.

### Example

```typescript
console.log(`Working on ${zkClient.networkName()} chain`);
// output: Working on polygon chain
```

## <mark style="background-color:green;">Get Token Seller Contract</mark>

```typescript
async tokenSellerContract(): Promise<string>
```

### Returns

`Promise` returns the `tokenSeller` contract address.

### Example

```typescript
console.log(`${await zkClient.tokenSellerContract()}`);
// output: 0x1b9d7af7793df23782b43af2566cc614745c32cf 
```
