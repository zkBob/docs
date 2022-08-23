---
description: To check transaction and tree proofs at the contract level
---

# Creating the Verifier Contracts

The parameters generated with the Ceremony are used to create verifier contracts. Before starting create a new folder and copy verification keys (json files) produced during the Ceremony:

```
mkdir verifiers
cp ./ceremony/tx_vk.json ./verifiers
cp ./ceremony/tree_vk.json ./verifiers
cd verifiers
```

Next, install `libzeropool-setup` utility and use it to generate contracts code:

```
cargo install --git https://github.com/zeropoolnetwork/libzeropool
libzeropool-setup generate-verifier -s TransferVerifier.sol -n TransferVerifier -v tx_vk.json
libzeropool-setup generate-verifier -s TreeUpdateVerifier.sol -n TreeUpdateVerifier -v tree_vk.json
cd ..

```

The resulting files are:

* TransferVerifier.sol
* TreeUpdateVerifier.sol
