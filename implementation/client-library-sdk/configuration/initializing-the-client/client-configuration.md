---
description: Configure the common parameters
---

# Client Configuration

Your should provide a client configuration when instantiating `ZkBobClient`. This includes pools and chains description according to the following parameters:

```typescript
interface ClientConfig {
  pools: Pools;
  chains: Chains;
  snarkParams: SnarkConfigParams;  // global SNARK parameters (for all pools)
  snarkParamsSet?: Parameters;     // customized SNARK parameters
  supportId?: string;
  forcedMultithreading?: boolean;
}
```

### ClientConfig.pools

**The `ClientConfig.pools`** field contains descriptions of the supported privacy pools and maps the arbitrary pool name (aka pool alias) with the associated pool parameters.&#x20;

{% code fullWidth="false" %}
```typescript
type Pools = { [name: string]: Pool; }

interface Pool {
  chainId: number;
  poolAddress: string;
  tokenAddress: string;
  relayerUrls: string[];
  delegatedProverUrls: string[];
  depositScheme: DepositType;
  coldStorageConfigPath?: string;
  minTxAmount?: bigint;
  feeDecimals?: number;
  isNative?: boolean;
  ddSubgraph?: string;
  parameters?: string;
}
```
{% endcode %}

where

* `chainId` - the chain identifier (`137` for pool on Polygon, `1` for Ethereum Mainnet etc)
* `poolAddress` - 0x-prefixed pool smart-contract address
* `tokenAddress` - 0x-prefixed token smart-contract address served by the current pool
* `relayerUrls` - the list of the relayer URLs to interact with the pool _(please note the most of the pool operations are performed through the relayer)_. The list should be non-empty.

{% hint style="info" %}
Currently the multi-relayer configuration isn't supported. So if you provide several relayer URLs the first one will be used.
{% endhint %}

* `delegatedProverUrls` - the optional list of external entities called `prover` which are designated to perform proof calculations. Helpful for low-performance devices.
* `depositScheme` - a deposit scheme  for depositing tokens. It depends on pool's token. It's an `DepositType` enum value as follows:

```typescript
enum DepositType {
  Approve = 'approve',     // deprecated but still supported deposit scheme
  SaltedPermit = 'permit', // based on EIP-2612 (salt was added to the signing message)
  PermitV2 = 'permit2',    // Uniswap Permit2 scheme (used for WETH)
  AuthUSDC = 'usdc',       // EIP-3009 (for most of USDC deployments)
  AuthPolygonUSDC = 'usdc-polygon',  // EIP-3009 (used by USDC token on Polygon)
}
```

* `coldStorageConfigPath` - optional field which contains URL for the coldstorage config. Coldstorage is pre-downloaded files with pool transactions. It's needed to speed-up the user's state synchronization process.
* `minTxAmount` - the minimum transaction amount in the pool dimension (`500,000,000` is the default if that parameter is omitted).
* `feeDecimals` - the number of digits after the decimal point in the transaction fee (it will always rounded-up). Fees will not round if `feeDecimals` is `undefined`.
* `isNative` - should be true for WETH deployments.
* `ddSubgraph` - name of the subgraph to fetch pending direct deposit transactions.
* `parameters` - SNARK parameters set the alias (string name). The set MUST exist in `ClientConfig.snarkParamsSet` otherwise the global parameters set in `ClientConfig.snarkParams` will used if that parameter is omitted.

### ClientConfig.chains

**`ClientConfig.chains`** field contains chain description which are used in the pools defined in the client config. For the every `Pool.chainId` the chain with the associated ID should be defined here.&#x20;

```typescript
type Chains = { [chainId: string]: Chain; }

interface Chain {
  rpcUrls: string[];
}
```

where `rpcUrls` contain a list of JSON RPC endpoints which can interact with that chain. It's recommended to use several endpoints to decrease the probability of RPC interaction errors.

### ClientConfig.snarkParams

**`ClientConfig.snarkParams`** contains URLs of the zk-SNARK parameters and associated verification keys. It's needed to calculate and verify transactions proofs. The parameters are created before the pool deployment (during the Ceremony) and should be public available for the every pool.

```typescript
interface SnarkConfigParams {
  transferParamsUrl: string;
  transferVkUrl: string;
}
```

{% hint style="warning" %}
`snarkParams` is a common parameters applicable for all defined pools without `parameters` customization field
{% endhint %}

### ClientConfig.snarkParamsSet

**`ClientConfig.snarkParamsSet`** contains customized URLs of the zk-SNARK parameters and associated verification keys. This field implements the multiparameters support feature.

```typescript
type Parameters = {
  [name: string]: SnarkConfigParams;
}
```

### **ClientConfig.supportID**

**`ClientConfig.supportId`** is a unique random string sent to the relayer in every request. It's needed to track the user's activity for support purposes. The most common way to generate it is using the `uuid.v4()` method of the [uuid package](https://www.npmjs.com/package/uuid).&#x20;

{% hint style="info" %}
Please note the `supportId` updates every time the library loads so there is no way to link all user actions on the relayer side. That field is optional but in most cases the relayer requires it and all requests without `supportId` will be rejected.
{% endhint %}

### ClientConfig.forcedMultithreading

**`ClientConfig.forcedMultithreading`** is an optional field needed to override the multithreading mode selection (by default it selects automatically depending on the browser). The mode will select automatically when undefined. For example, to activate singlethread mode set `forcedMultithreading` to `false`.

### Client library multipool configuration example

```ts
const clientConfig: ClientConfig = {
    pools: {
        'USDC-polygon': {
            'chainId': 137,
            'parameters': 'prod',
            'poolAddress': '0x72e6B59D4a90ab232e55D4BB7ed2dD17494D62fB',
            'tokenAddress': '0x2791Bca1f2de4661ED88A30C99A7a9449Aa84174',
            'relayerUrls': ['https://relayer-mvp.zkbob.com'],
            'delegatedProverUrls': ['https://remoteprover-mvp.zkbob.com/'],
            'feeDecimals': 2,
            'depositScheme': 'usdc-polygon',
            'ddSubgraph': 'zkbob-usdc-polygon'
        },
        'BOB-sepolia': {
            'chainId': 11155111,
            'parameters': 'stage',
            'poolAddress': '0x3bd088C19960A8B5d72E4e01847791BD0DD1C9E6',
            'tokenAddress': '0x2C74B18e2f84B78ac67428d0c7a9898515f0c46f',
            'relayerUrls': ['https://relayer.thgkjlr.website/'],
            'delegatedProverUrls': [],
            'feeDecimals': 2,
            'depositScheme': 'permit',
        },

    },
    chains: {
        '137': {
            rpcUrls: ['https://rpc.ankr.com/polygon']
        },
        '11155111': {
            rpcUrls: ['https://rpc.sepolia.org']
        }
    },
    snarkParamsSet: {
        'prod': {
            transferParamsUrl: '/path/to/prod/transfer/params',
            transferVkUrl: '/path/to/prod/transfer/vk'
        },
        'stage': {
            transferParamsUrl: '/path/to/stage/transfer/params',
            transferVkUrl: '/path/to/stage/transfer/vk'
        }
    },
    
    supportId: 'unique_string_generated_with_uuidv4',
    forcedMultithreading: undefined
};
```

### Minimal Configurations for Deployed Solutions

To get started with already deployed privacy pools you can download the minimal config file for the production or development environment.

{% hint style="warning" %}
The following configurations contain only the mandatory fields. To instantiate the ZkBobClient object do not forget to provide other parameters. For example the client can be initialized without `supportId` but most likely the relayer will reject any request without this field.
{% endhint %}

{% file src="../../../../.gitbook/assets/prod-pools (3).json" %}
**Production Pools:** USDC-polygon, BOB-optimism, WETH-optimism
{% endfile %}

{% file src="../../../../.gitbook/assets/dev-pools (3).json" %}
**Development Pools:** BOB-sepolia, BOB2USDC-goerli, WETH-goerli, USDC-goerli, BOB-op-goerli
{% endfile %}
