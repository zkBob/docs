# Basic Concepts

### zkBob Account

A zkBob account is linked to a user by way of a private key. The private key is used to identify the account balance, to generate proofs to transfer tokens, and to withdraw tokens from the pool.&#x20;

zkBob accounts are created either from the private key of an existing wallet or from a stand-alone seed phrase. Users can choose how they would like to create an account though the UI following a step-by-step process.

Accounts never appear unencrypted in a public field and can only be decyrpted by the account owner.

### zkBob Address

A zkBob account doesn't contain a fixed address for receiving funds. Rather, the user generates a private zkBob address. Ideally, a new address is generated for each incoming transaction.&#x20;

It is not possible to link different private addresses to one another or to the primary account. Only the account owner can confirm ownership of a private address.

Each created address is encoded in base58 format. For example `5fkW3dXTvA8Kizt1EbuRyjWofuqR4Ud1YTjGgY1r8nGosDeSaUreq6bwfF61jWL`

### **Deposits**

Deposits can be made by sending a direct transaction (from a zkBob Account) into the zkBob contract on the Gnosis Chain, which adds the funds into the zkBob pool. This is accomplished through the UI.

### **Transfers**

Transfers use specialized zkBob relayers to send private transactions. A user can transfer funds to another zkBob account by sending zk-proofs anonymously to one of relayers. The relayer publishes the transaction to the zkBob contract on the Gnosis Chain.

### Withdrawals

Similar to deposits, a user can send a direct transaction to the zkBob contract in the Gnosis Chain to withdraw tokens from the pool. The transaction contains a zero-knowledge proof of tokens ownership generated using the private key associated with the corresponding zkBob account.

### **sxDai**

sxDai is shielded xDai, a secure token used for transfers within the zero-knowledge pool.  xDai is automatically converted to sxDai when completing a deposit, and sxDai is converted back to xDai on withdrawal.
