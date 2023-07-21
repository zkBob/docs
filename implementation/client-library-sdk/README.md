---
description: Client library v5.2.0 development guide
---

# Client Library SDK

The `zkbob-client-js` library SDK is used to interact with the zkBob ecosystem from the client side. The SDK supports different privacy pool deployments and can be used to create custom clients.

## Get Started

The latest stable version of the library is published on [npmjs.com](https://www.npmjs.com/package/zkbob-client-js) with the `latest` tag. To use the library install it with your preferred packet manager like `npm`:

```sh
npm i zkbob-client-js
```

or `yarn`:

```bash
yarn add zkbob-client-js
```

...or manually include it in the `package.json` file as follows:

```json
"dependencies": {
    .........
    "zkbob-client-js": "5.2.0"
    .........
}
```

All interactions with the solution are performed within the instance of the `ZkBobClient` object which should be initialized with the desired [pool configuration](configuration/initializing-the-client/client-configuration.md). There are two available modes for the `ZkBobClient` instance:

* **Account-less mode**. The library can interact with most of the system components (such as relayers, contracts and so on) to retrieve publicly available data (transaction fee, limits, Merkle tree indexes and other data needed to render the UI), but cannot perform any actions belonging to the concrete user account (e.g. getting user's balance, making deposits\transfers\withdrawals and so on). The library starts on this state when `ZkBobClient` is [instantiated](configuration/initializing-the-client/).
* **Full mode**. To switch to full mode you must provide user credentials (spending key) to the library. Do this by [attaching](configuration/attaching-a-user-account/#login) a prepared user's [account configuration](configuration/attaching-a-user-account/account-configuration.md). [Logout](configuration/attaching-a-user-account/#logout) of the account any time

## Next Steps

1. Start with the [configuration](configuration/ "mention") section to understand which data you need start designing your own client.&#x20;
   * Associated examples are available for the [client](configuration/initializing-the-client/client-configuration.md#the-client-library-multipool-configuration-example) and [account](configuration/attaching-a-user-account/account-configuration.md#account-configuration-example) configurations.
   * Actual production and development configurations are available for [download here](configuration/initializing-the-client/client-configuration.md#minimal-configurations-for-the-deployed-solutions).
2. [Initialize](configuration/initializing-the-client/) a `ZkBobClient` instance and check that the account-less mode works properly. For example you can [request the relayer fee](account-less-mode-operations/transaction-fees.md#getting-relayer-raw-fee) or [fetch privacy pool limits](account-less-mode-operations/transaction-constraints.md#getting-pool-limits). All available functions for this mode are described in the [account-less-mode-operations](account-less-mode-operations/ "mention") section.
3. Create you own [account](configuration/attaching-a-user-account/account-configuration.md) and [attach](configuration/attaching-a-user-account/#login) it to the `ZkBobClient` instance. Remember only one account can be attached at a time.
4. [Synchronize](full-mode-operations/account-state.md#syncing-the-local-state) the local state with the relayer and privacy pool state. This operation can take some time depending on pool size (overall number of transactions in the pool).
5. Retrieve account related data (e.g. [fetch shielded balance](full-mode-operations/balances-and-history.md#getting-the-account-balance) or [generate a zk-address](full-mode-operations/shielded-addresses.md#generating-shielded-address)). All routines associated with the account are located in the [full-mode-operations](full-mode-operations/ "mention") section

## Examples

You can always refer to the existing client implementations to get a better understanding and find answers to your questions:

* [A brief how-to example](https://github.com/zkBob/zkbob-client-js/blob/main/README.md) located in the client repository's README file.
* [zkbob-console](https://github.com/zkBob/zkbob-console) - a simple text Web-client based on jQuery Terminal. It's always synced with the last library version.
* [react-template](https://github.com/zkBob/react-template) - a React App template project with integrated `zkbob-client-js` library.
* **Waiting for your cool implementation to include it here...!**

## FAQ

#### **What can I build using ZkBob client SDK?**

You can build a custom client for the platform of your choice or add extended functionality like a custodial wallet service or mobile wallet. It should also be noted that the SDK relies heavily on underlying low-level Rust code compiled to WASM, so for example mobile support in React Native would impose additional challenges.&#x20;

#### How do I use ZkBob SDK in my React app?

The SDK can be imported as a regular JS library, but it requires some customization of the webpack configuration, which can be challenging if you use `create-react-app`. This is why we have created a ready-to-go [ react-template](https://github.com/zkBob/react-template) that utilizes react-app-rewired tool to override some configurations and make it all work.\
Alternatively you can use Next.js or Vite to bootstrap your React app that allows you to access the webpack configuration.

#### Where do I get Snark parameters for client initialization?

In order for a client to create a valid transaction proof, parameters and a verification key are required (for a quick sanity check before sending a transaction). These parameters are generated using a trusted setup ceremony for production usage, while the development environment uses some random values.&#x20;

All the testing and development environments on testnets use the following parameters:&#x20;

```javascript
snarkParams: {
      transferParamsUrl: 'https://r2-staging.zkbob.com/transfer_params_20022023.bin',
      transferVkUrl: 'https://r2-staging.zkbob.com/transfer_verification_key_20022023.json'
    }
```

All of the production environments use these parameters:

```javascript
snarkParams: {
      transferParamsUrl: 'https://r2.zkbob.com/transfer_params_22022023.bin',
      transferVkUrl: 'https://r2.zkbob.com/transfer_verification_key_22022023.json'
    }
```

{% hint style="warning" %}
The CDN is configured so that only requests from localhost and zkbob domains are processed, so you would have to download params files and include them in the bundle. You can see how to do that in the [#examples](./#examples "mention")
{% endhint %}

#### How do I login to an existing account using the SDK?

Currently the API between the front end and the SDK allows you to pass the account credentials in the form of a spending key that is derived from the mnemonic seed phrase. You can export your seed phrase and pass it to the function `deriveSpendingKeyZkBob` to get a secret key:&#x20;

```typescript
const sk = deriveSpendingKeyZkBob("general team spot pass shoulder domain axis crazy since kind athlete buzz")
```

Then pass the resulting spending key to the `accountConfig` object to login.

```typescript
    const client = await ZkBobClient.create(config, 'BOB-sepolia');
    const accountConfig: AccountConfig = {
      sk,
      pool: 'BOB-sepolia',
      birthindex: -1,
      proverMode: ProverMode.Local,
    };
    await client.login(accountConfig);
```

If you'd rather derive a spending key from your Web3 wallet (such as MetaMask) signature then you need to get the menmonic first:

```typescript
const mnemonic = ethers.utils.entropyToMnemonic(hexToBuf("9f86d081884c7d659a2feaa0c55ad015a3bf4f1b2b0b822cd15d6c15b0f00a08"))
```

{% hint style="info" %}
See the full code for client instantiation and login in [#examples](./#examples "mention")
{% endhint %}

#### How do I generate an address for receiving funds?

In the current version of the protocol, only the user can generate a new address for receiving funds inside the pool (zkAddress). Generating a zkAddress requires a secret encryption key which can only be provided by the user. Address generation itself is very easy, simply call the corresponding method of the client object.

```typescript
const zkAddress = await zkClient?.generateAddress()
```

