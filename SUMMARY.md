# Table of contents

## 🦹 Bob Overview

* [Bob Stable Rollup](README.md)
* [Basic Concepts](bob-overview/basic-concepts.md)
* [BOB Stable Token](bob-overview/bob-stable-token.md)
* [Deposit Limits](bob-overview/deposit-limits.md)
* [Compliance](bob-overview/compliance.md)
* [Roadmap](bob-overview/roadmap.md)
* [FAQ](bob-overview/faq.md)

## 🦸♂ Applications

* [zkBob Transaction App](applications/zkbob-app/README.md)
  * [Account Creation](applications/zkbob-app/account-creation/README.md)
    * [Metamask / Web3 Wallet Warning](applications/zkbob-app/account-creation/metamask-web3-wallet-warning.md)
  * [Deposits](applications/zkbob-app/deposits.md)
  * [Transfers](applications/zkbob-app/transfers.md)
  * [Withdrawals](applications/zkbob-app/withdrawals.md)
  * [XP Accumulation](applications/zkbob-app/xp-accumulation.md)
  * [Generate a Secure Address](applications/zkbob-app/generate-a-secure-address.md)
  * [Anonymity Set Awareness](applications/zkbob-app/anonymity-set-awareness.md)

## 👩⚕ Technical Implementation <a href="#implementation" id="implementation"></a>

* [Bob Rollup Overview](implementation/bob-rollup-overview.md)
* [zkBob Application Overview](implementation/high-level-overview/README.md)
  * [Smart Contracts](implementation/high-level-overview/contracts-and-circuits/README.md)
    * [The Pool Contract](implementation/high-level-overview/contracts-and-circuits/the-pool-contract/README.md)
      * [Transaction Calldata](implementation/high-level-overview/contracts-and-circuits/the-pool-contract/transaction-calldata.md)
    * [Token Contract](implementation/high-level-overview/contracts-and-circuits/token-contract.md)
    * [Verifier contracts](implementation/high-level-overview/contracts-and-circuits/verifier-contracts.md)
    * [Operator Manager Contract](implementation/high-level-overview/contracts-and-circuits/operator-manager-contract/README.md)
      * [Mutable Operator Manager](implementation/high-level-overview/contracts-and-circuits/operator-manager-contract/mutable-operator-manager.md)
      * [Round-Robin Operator Manager](implementation/high-level-overview/contracts-and-circuits/operator-manager-contract/round-robin-operator-manager.md)
    * [Voucher Token Contract](implementation/high-level-overview/contracts-and-circuits/voucher-token-contract.md)
  * [Transaction Overview](implementation/high-level-overview/transaction-overview/README.md)
    * [Common Structure](implementation/high-level-overview/transaction-overview/common-structure.md)
    * [Memo Block](implementation/high-level-overview/transaction-overview/untitled-1/README.md)
      * [Memo Block Encryption](implementation/high-level-overview/transaction-overview/untitled-1/memo-block-encryption.md)
    * [Transaction Types](implementation/high-level-overview/transaction-overview/transaction-types.md)
    * [The Nullifiers](implementation/high-level-overview/transaction-overview/the-nullifiers.md)
    * [Signing a Transaction](implementation/high-level-overview/transaction-overview/signing-a-transaction.md)
    * [The Transaction Lifecycle](implementation/high-level-overview/transaction-overview/the-transaction-lifecycle.md)
  * [Accounts and Notes](implementation/high-level-overview/account-and-notes/README.md)
    * [Accounts](implementation/high-level-overview/account-and-notes/accounts.md)
    * [Notes](implementation/high-level-overview/account-and-notes/notes.md)
  * [Relayer Node](implementation/high-level-overview/relayer-node/README.md)
    * [Relayer Operations](implementation/high-level-overview/relayer-node/relayer-operations.md)
    * [Optimistic State](implementation/high-level-overview/relayer-node/optimistic-state.md)
    * [REST API](implementation/high-level-overview/relayer-node/rest-api.md)
  * [zkBob Keys](implementation/high-level-overview/zkbob-keys/README.md)
    * [Address derivation](implementation/high-level-overview/zkbob-keys/address-derivation.md)
    * [Ephemeral keys](implementation/high-level-overview/zkbob-keys/ephemeral-keys.md)
  * [zkSNARKs & Circuits](implementation/high-level-overview/zksnarks-and-circuits/README.md)
    * [Transaction verifier circuit](implementation/high-level-overview/zksnarks-and-circuits/transaction-verifier-circuit.md)
    * [Tree verifier circuit](implementation/high-level-overview/zksnarks-and-circuits/tree-verifier-circuit.md)
  * [zkBob Merkle Tree](implementation/high-level-overview/untitled/README.md)
    * [Merkle Tree Updating](implementation/high-level-overview/untitled/merkle-tree-updating.md)
    * [The Poseidon Hash](implementation/high-level-overview/untitled/the-poseidon-hash.md)
  * [Elliptic Curve Cryptography](implementation/high-level-overview/elliptic-curve-cryptography.md)

## 👩🏫 Deployment

* [zkBob Application Deployment](deployment/zkbob-solution-deployment/README.md)
  * [Trusted Setup Ceremony](deployment/zkbob-solution-deployment/trusted-setup-ceremony.md)
  * [Creating the Verifier Contracts](deployment/zkbob-solution-deployment/creating-the-verifier-contracts.md)
  * [Contracts Deployment](deployment/zkbob-solution-deployment/contracts-deployment.md)
  * [Relayers Subsystem](deployment/zkbob-solution-deployment/relayers-subsystem.md)

## 👷♂ In Development

* [Multi-chain Custom Rollup Deployment](in-development/multi-chain-custom-rollup-deployment.md)
* [zkBob OmniBridge Interaction](in-development/zkbob-omnibridge-interaction/README.md)
  * [Private Deposits via OmniBridge (v2)](in-development/zkbob-omnibridge-interaction/private-deposits-via-omnibridge.md)
* [XP (Experience Points)](in-development/xp/README.md)
  * [XP-based Auctions](in-development/xp/xp-based-auctions.md)

## 🧑💻 Jobs

* [Zero-Knowledge Researcher & Protocol Developer](jobs/zero-knowledge-researcher-and-protocol-developer.md)
