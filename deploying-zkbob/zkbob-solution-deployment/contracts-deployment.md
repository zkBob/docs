# Contracts Deployment

You should to deploy the contract set to become zkBob ready to operate. The easiest way to do that is to run deploy script from the contract repository. You should get the verifier contracts from the previous step

```
git clone https://github.com/zkBob/pool-evm-single-l1
cp ./verifiers/TransferVerifier.sol ./pool-evm-single-l1/contracts/
cp ./verifiers/TreeUpdateVerifier.sol ./pool-evm-single-l1/contracts/
cd pool-evm-single-l1
```

Next you should load required dependencies and compile the contracts

```
npm install
npx hardhat compile
```

Prepare `.env` file to set deployment parameters. You must provide seed phrase for your account to deploy contacts. Please charge your wallet before contracts deployment

```
echo -e MOCK_TREE_VERIFIER=false > .env
echo -e MOCK_TX_VERIFIER=false >> .env
echo -e MNEMONIC=\'insert seed phrase for your native account\' >> .env
```

Deploy all contracts in the xDai network

```
npx hardhat run --network xdai scripts/deploy-task.js
```

{% hint style="danger" %}
**TODO:** need to add xdai network to the hardhat.config.js
{% endhint %}
