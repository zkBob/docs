# Basic Concepts

{% hint style="info" %}
Below are descriptions of basic concepts underlying zkBob functionality. For more thorough details, see the [technical implementation ](broken-reference) section.
{% endhint %}

### BOB

BOB is the name of the multi-chain, multi-collateral stablecoin optimized for the zkBob protocol. It provides optional privacy features for users when paired with the zkBob application. BOB can be swapped for the equivalent amount of other stablecoins (minus standard swap fees) or other available tokens on Ethereum, Polygon, Optimism, Arbitrum and BSC. [More details here](broken-reference).

### zkBob

zkBob is a zk-based privacy application built for stablecoin transfers. It accepts BOB stablecoins for deposit, and once deposited in the zkBob app, BOB can be transferred anonymously between participants. BOB can then be withdrawn from the application to an EOA (externally owned address) preserving anonymity of the transfer amounts and participants.

### Zero-Knowledge Proofs (zkSNARKs)

zkBob uses zkSNARKS zero-knowledge proofs to verify an action has been completed (deposit, transfer, withdrawal) without providing any other identifying details about that action. zkSNARKs confirm that the chain state has changed without divulging information about amounts, initiators, or receivers of transactions. [Learn more about zero-knowledge proofs.](https://vitalik.ca/general/2021/01/26/snarks.html)

### zkBob Account

A zkBob account is linked to a user via a private key. The private key is used to identify the account balance, generate proofs to transfer tokens, and withdraw tokens from the pool.&#x20;

zkBob accounts are created either from the private key of an existing MetaMask/WalletConnect wallet or from a stand-alone secret phrase. Users can decide how they would like to create an account following a step-by-step process.

Accounts never appear unencrypted in a public field and can only be decrypted by the account owner.

### zkBob Address

A zkBob account doesn't contain a fixed address for receiving funds. Rather, the user generates a private zkBob address using the application. Through the UI, a new address is generated for each incoming transaction.&#x20;

It is not possible to link different private addresses to one another or to the primary account. Only the account owner can confirm ownership of a private address.

Each created address is encoded in base58 format. For example `5fkW3dXTvA8Kizt1EbuRyjWofuqR4Ud1YTjGgY1r8nGosDeSaUreq6bwfF61jWL`

### **Deposits**

Deposits can be made by sending Bob tokens (from a regular 0x-based account) to the zkBob Pool contract. Depositors complete 2 steps to get started.&#x20;

1. Approve the contract to access funds.
2. Create and send the deposit.&#x20;

Transactions are routed via a relayer to the pool contract then deposited into a zkAccount.

### **Transfers**

Transfers also use relayers to send private transactions. A user can transfer funds to another zkBob account by sending a zk-proof anonymously to a relayer. The relayer then publishes the transaction to the zkBob contract.

### Withdrawals

Similar to deposits, a user can send a transaction to the zkBob contract to withdraw tokens from the pool. The transaction contains a zero-knowledge proof of token ownership generated using the private key associated with the corresponding zkBob account.

### Relayer

The relayer acts as an intermediary between the user and the smart contracts. Transactions are sent to the relayer which collects transactions, calculates Merkle tree proofs, orders them in a queue, then sends this information to the contract. The relayer cannot see transaction amounts and preserves anonymity by abstracting gas fees for operations. Relayer interaction occurs via a [REST API](../../implementation/relayer-node/rest-api.md).

### Base Layer Neutrality

zkBob stands on the pillars of privacy, anti-censorship, and decentralization and seeks to prevent misuse of the protocol through built-in compliance measures.&#x20;

By enacting these measures, the protocol is designed to function on a neutral base layer. This means that participants on the base layer (validators, sequencers, relayers etc) can operate normally without taking additional measures (like censoring sanctioned addresses) to properly write and order on-chain transactions. [Learn more about base layer neutrality here](https://www.paradigm.xyz/2022/09/base-layer-neutrality).



