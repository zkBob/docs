# Contracts Deployment

Deploy the contract set to initialize zkBob by running the deploy script from the contract repository. Get the verifier contracts from the previous step ([Creating the Verifier Contracts](creating-the-verifier-contracts.md)).

```
git clone https://github.com/zkBob/pool-evm-single-l1
cp ./verifiers/TransferVerifier.sol ./pool-evm-single-l1/contracts/
cp ./verifiers/TreeUpdateVerifier.sol ./pool-evm-single-l1/contracts/
cd pool-evm-single-l1
```

Next, load the required dependencies and compile the contracts.

```
npm install
npx hardhat compile
```

Prepare the `.env` file to set deployment parameters. You must provide a seed phrase for your account to deploy contacts. Deposit funds to your wallet before contracts deployment to pay for the deployment.

```
echo -e MOCK_TREE_VERIFIER=false > .env
echo -e MOCK_TX_VERIFIER=false >> .env
echo -e MNEMONIC=\'insert seed phrase for your native account\' >> .env
```

Deploy all contracts. This example uses the Polygon network.

```
npx hardhat run --network matic scripts/deploy-task.js
```
