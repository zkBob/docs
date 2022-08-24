# Table of contents

## 🦹 Bob Overview

* [Meet Bob](README.md)
* [Basic Concepts](bob-overview/basic-concepts.md)
* [BOB Stable Token](bob-overview/bob-stable-token.md)
* [Bob on Polygon](bob-overview/bob-on-polygon.md)
* [Deposit & Withdrawal Limits](bob-overview/deposit-and-withdrawal-limits.md)
* [Security](bob-overview/security.md)
* [Compliance](bob-overview/compliance.md)
* [FAQ](bob-overview/faq.md)

## 🦸♂ zkBob Application <a href="#zkbob-app" id="zkbob-app"></a>

* [UI Overview](zkbob-app/zkbob-app.md)
* [Account Creation](zkbob-app/account-creation/README.md)
  * [Metamask / Web3 Wallet Warning](zkbob-app/account-creation/metamask-web3-wallet-warning.md)
* [Deposits](zkbob-app/deposits.md)
* [Transfers](zkbob-app/transfers.md)
* [Withdrawals](zkbob-app/withdrawals.md)
* [Generate a Secure Address](zkbob-app/generate-a-secure-address.md)
* [Anonymity Set Awareness](zkbob-app/anonymity-set-awareness.md)

## 👩⚕ Technical Implementation <a href="#implementation" id="implementation"></a>

* [zkBob Application Overview](implementation/high-level-overview.md)
* [Smart Contracts](implementation/contracts-and-circuits/README.md)
  * [The Pool Contract](implementation/contracts-and-circuits/the-pool-contract/README.md)
    * [Transaction Calldata](implementation/contracts-and-circuits/the-pool-contract/transaction-calldata.md)
  * [Token Contract](implementation/contracts-and-circuits/token-contract.md)
  * [Verifier contracts](implementation/contracts-and-circuits/verifier-contracts.md)
  * [Operator Manager Contract](implementation/contracts-and-circuits/operator-manager-contract/README.md)
    * [Mutable Operator Manager](implementation/contracts-and-circuits/operator-manager-contract/mutable-operator-manager.md)
    * [Round-Robin Operator Manager](implementation/contracts-and-circuits/operator-manager-contract/round-robin-operator-manager.md)
  * [Voucher Token Contract](implementation/contracts-and-circuits/voucher-token-contract.md)
* [Accounts and Notes](implementation/account-and-notes/README.md)
  * [Accounts](implementation/account-and-notes/accounts.md)
  * [Notes](implementation/account-and-notes/notes.md)
* [Relayer Node](implementation/relayer-node/README.md)
  * [Relayer Operations](implementation/relayer-node/relayer-operations.md)
  * [Optimistic State](implementation/relayer-node/optimistic-state.md)
  * [REST API](implementation/relayer-node/rest-api.md)
* [zkBob Keys](implementation/zkbob-keys/README.md)
  * [Address derivation](implementation/zkbob-keys/address-derivation.md)
  * [Ephemeral keys](implementation/zkbob-keys/ephemeral-keys.md)
* [zkSNARKs & Circuits](implementation/zksnarks-and-circuits/README.md)
  * [Transaction verifier circuit overview](implementation/zksnarks-and-circuits/transaction-verifier-circuit.md)
* [zkBob Merkle Tree](implementation/untitled/README.md)
  * [The Poseidon Hash](implementation/untitled/the-poseidon-hash.md)
* [Elliptic Curve Cryptography](implementation/elliptic-curve-cryptography.md)
* [Transaction Overview](implementation/transaction-overview/README.md)
  * [Common Structure](implementation/transaction-overview/common-structure.md)
  * [Memo Block](implementation/transaction-overview/untitled-1/README.md)
    * [Memo Block Encryption](implementation/transaction-overview/untitled-1/memo-block-encryption.md)
  * [Transaction Types](implementation/transaction-overview/transaction-types.md)
  * [Nullifiers](implementation/transaction-overview/the-nullifiers.md)
  * [Signing a Transaction](implementation/transaction-overview/signing-a-transaction.md)
  * [The Transaction Lifecycle](implementation/transaction-overview/the-transaction-lifecycle.md)

## 👩🏫 Deployment

* [zkBob Deployment Overview](deployment/overview.md)
* [Trusted Setup Ceremony](deployment/trusted-setup-ceremony.md)
* [Creating the Verifier Contracts](deployment/creating-the-verifier-contracts.md)
* [Contracts Deployment](deployment/contracts-deployment.md)
* [Relayers Subsystem](deployment/relayers-subsystem.md)

## 👷♂ Roadmap

* [Multi-chain Custom Rollup Deployment](roadmap/multi-chain-custom-rollup-deployment.md)
* [Compounding](roadmap/compounding.md)
* [XP (Experience Points)](roadmap/xp/README.md)
  * [XP-based Auctions](roadmap/xp/xp-based-auctions.md)

## 🧑💻 Jobs

* [Zero-Knowledge Researcher & Protocol Developer](jobs/zero-knowledge-researcher-and-protocol-developer.md)
