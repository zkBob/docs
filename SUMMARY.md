# Table of contents

## 🦹 zkBob Overview

* [Private Transactions](README.md)
* [Basic Concepts](zkbob-overview/basic-concepts.md)
* [FAQ](zkbob-overview/faq.md)
* [Roadmap](zkbob-overview/roadmap.md)

## 🦸♂ Using zkBob <a href="#zkbob-getting-started" id="zkbob-getting-started"></a>

* [zkBob App](zkbob-getting-started/zkbob-app/README.md)
  * [Account Creation](zkbob-getting-started/zkbob-app/account-creation/README.md)
    * [Metamask / Web3 Wallet Warning](zkbob-getting-started/zkbob-app/account-creation/metamask-web3-wallet-warning.md)
  * [Deposits](zkbob-getting-started/zkbob-app/deposits.md)
  * [Transfers](zkbob-getting-started/zkbob-app/transfers.md)
  * [Withdrawals](zkbob-getting-started/zkbob-app/withdrawals.md)
  * [Generate a Secure Address](zkbob-getting-started/zkbob-app/generate-a-secure-address.md)
* [Anonymity Set Awareness](zkbob-getting-started/anonymity-set-awareness.md)

## 👩⚕ Technical Implementation <a href="#implementation" id="implementation"></a>

* [High-level Overview](implementation/high-level-overview.md)
* [Smart Contracts](implementation/contracts-and-circuits/README.md)
  * [The Pool Contract](implementation/contracts-and-circuits/the-pool-contract/README.md)
    * [Transaction Calldata](implementation/contracts-and-circuits/the-pool-contract/transaction-calldata.md)
  * [Token Contract](implementation/contracts-and-circuits/token-contract.md)
  * [Verifier contracts](implementation/contracts-and-circuits/verifier-contracts.md)
  * [Operator Manager Contract](implementation/contracts-and-circuits/operator-manager-contract/README.md)
    * [Mutable Operator Manager](implementation/contracts-and-circuits/operator-manager-contract/mutable-operator-manager.md)
    * [Round-Robin Operator Manager](implementation/contracts-and-circuits/operator-manager-contract/round-robin-operator-manager.md)
  * [Voucher Token Contract](implementation/contracts-and-circuits/voucher-token-contract.md)
* [Relayer Node](implementation/relayer-node/README.md)
  * [Relayer Operations](implementation/relayer-node/relayer-operations.md)
  * [REST API](implementation/relayer-node/rest-api.md)
* [Accounts and Notes](implementation/account-and-notes/README.md)
  * [Accounts](implementation/account-and-notes/accounts.md)
  * [Notes](implementation/account-and-notes/notes.md)
* [Transaction Overview](implementation/transaction-overview/README.md)
  * [Common Structure](implementation/transaction-overview/common-structure.md)
  * [Memo Block](implementation/transaction-overview/untitled-1/README.md)
    * [Memo Block Encryption](implementation/transaction-overview/untitled-1/memo-block-encryption.md)
  * [Transaction Types](implementation/transaction-overview/transaction-types.md)
  * [The Nullifiers](implementation/transaction-overview/the-nullifiers.md)
  * [Signing a Transaction](implementation/transaction-overview/signing-a-transaction.md)
  * [The Transaction Lifecycle](implementation/transaction-overview/the-transaction-lifecycle.md)
* [zkBob Merkle Tree](implementation/untitled/README.md)
  * [Merkle Tree Updating](implementation/untitled/merkle-tree-updating.md)
  * [The Poseidon Hash](implementation/untitled/the-poseidon-hash.md)
* [zkBob Keys](implementation/zkbob-keys/README.md)
  * [Address derivation](implementation/zkbob-keys/address-derivation.md)
  * [Ephemeral keys](implementation/zkbob-keys/ephemeral-keys.md)
* [zkSNARKs & Circuits](implementation/zksnarks-and-circuits/README.md)
  * [Transaction verifier circuit](implementation/zksnarks-and-circuits/transaction-verifier-circuit.md)
  * [Tree verifier circuit](implementation/zksnarks-and-circuits/tree-verifier-circuit.md)
* [Elliptic Curve Cryptography](implementation/elliptic-curve-cryptography.md)

## 👩🏫 Deploying zkBob

* [zkBob Solution Deployment](deploying-zkbob/zkbob-solution-deployment/README.md)
  * [Trusted Setup Ceremony](deploying-zkbob/zkbob-solution-deployment/trusted-setup-ceremony.md)
  * [Creating the Verifier Contracts](deploying-zkbob/zkbob-solution-deployment/creating-the-verifier-contracts.md)
  * [Contracts Deployment](deploying-zkbob/zkbob-solution-deployment/contracts-deployment.md)
  * [Relayers Subsystem](deploying-zkbob/zkbob-solution-deployment/relayers-subsystem.md)

## 👷♂ In Development

* [Multi-chain Custom Rollup Deployment](in-development/multi-chain-custom-rollup-deployment.md)
* [zkBob OmniBridge Interaction](in-development/zkbob-omnibridge-interaction/README.md)
  * [Private Deposits via OmniBridge (v2)](in-development/zkbob-omnibridge-interaction/private-deposits-via-omnibridge.md)
* [XP (Experience Points)](in-development/xp/README.md)
  * [XP-based Auctions](in-development/xp/xp-based-auctions.md)

## 🧑💻 Jobs

* [Zero-Knowledge Researcher & Protocol Developer](jobs/zero-knowledge-researcher-and-protocol-developer.md)
