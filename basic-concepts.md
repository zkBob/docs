# Basic Concepts

Below are descriptions of basic concepts underlying zkBob functionality. For more thorough details, see the technical overview section.

The zkBob protocol facilitates private transactions. Users can deposit arbitrary amounts into a zero-knowledge pool, privately transfer tokens within that pool, and withdraw arbitrary amounts from the pool. A shielded token is used within the pool to anonymize transfers, and relayers are used to process transactions and abstract gas costs between users and the pool smart contract.&#x20;

### Zero-Knowledge Proofs

zkBob uses zero-knowledge proofs to verify an action has been completed (deposit, transfer, withdrawal) without providing any other identifying details about that action. Zkproofs confirm that the chain state has changed without divulging information about amounts, initiators or receivers of transactions. [Learn more about zero-knowledge proofs](https://en.wikipedia.org/wiki/Zero-knowledge\_proof).

### zkBob Account

A zkBob account is linked to a user via a private key. The private key is used to identify the account balance, generate proofs to transfer tokens, and withdraw tokens from the pool.&#x20;

zkBob accounts are created either from the private key of an existing wallet or from a stand-alone seed phrase. Users can decide how they would like to create an account following a step-by-step process.

Accounts never appear unencrypted in a public field and can only be decyrpted by the account owner.

### zkBob Address

A zkBob account doesn't contain a fixed address for receiving funds. Rather, the user generates a private zkBob address using the application. Ideally, a new address is generated for each incoming transaction.&#x20;

It is not possible to link different private addresses to one another or to the primary account. Only the account owner can confirm ownership of a private address.

Each created address is encoded in base58 format. For example `5fkW3dXTvA8Kizt1EbuRyjWofuqR4Ud1YTjGgY1r8nGosDeSaUreq6bwfF61jWL`

### **Deposits**

Deposits can be made by sending a transaction (from a zkBob Account) to the zkBob pool contract on the Gnosis Chain. Depositors first approve the contract to access the funds, then create and send the deposit. Transactions are routed via a relayer to the pool contract, and can be initiated through the UI.

### **Transfers**

Transfers also use relayers to send private transactions. A user can transfer funds to another zkBob account by sending zk-proofs anonymously to one of relayers. The relayer publishes the transaction to the zkBob contract on the Gnosis Chain.

### Withdrawals

Similar to deposits, a user can send a transaction to the zkBob contract in the Gnosis Chain to withdraw tokens from the pool. The transaction contains a zero-knowledge proof of tokens ownership generated using the private key associated with the corresponding zkBob account.

### **sxDai**

sxDai is shielded xDai, a secure token used for transfers within the zero-knowledge pool.  xDai is automatically converted to sxDai when completing a deposit, and sxDai is converted back to xDai on withdrawal.

### Relayer

The relayer acts as an intermediary between the user and the smart contracts. Transactions are sent to the relayer which processes the input transactions, calculates Merkle tree proofs, then sends this information to the contract. The relayer preserves anonymity by abstracting gas fees for operations, and provides encrypted transaction storage. Relayer interaction occurs via a [REST API](technical-overview/relayer-node/rest-api.md).
