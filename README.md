---
description: zkBob private transfers
---

# Private Transactions

## 🔐 Private Transactions

zkBob is an advanced blockchain privacy solution for safeguarding P2P financial transfers. With zkBob, it is easy to:

1. [Setup](using-zkbob/zkbob-app/account-creation/) a zkAccount using a seed phrase or existing web3 wallet.
2. [Deposit ](using-zkbob/zkbob-app/deposits.md)arbitrary token amounts of a stablecoin into the application.
3. [Transfer](using-zkbob/zkbob-app/transfers.md) deposits to other participants using zkSnarks technology (proof of transaction without disclosing details of the sender, recipient, and value).
4. [Withdraw](using-zkbob/zkbob-app/withdrawals.md) arbitrary token amounts securely and privately.

To ensure privacy, zkBob leverages a unique stablecoin called Bob and an associated zero-knowledge pool to anonymize transactions. Deposits of any amount of Bob can be made to the pool. Funds in the pool are converted to shielded Bob tokens, which can then be transferred to other participants within the pool and/or withdrawn from the pool.

Transactions are processed through a relayer that constructs zkproofs and submits anonymous transactions to the pool contract.

Zero knowledge proofs ensure that transfers and withdrawals are decoupled from deposits, resulting in private transfers between parties.

## **zkBob and Alice** 🐇

Alice is a well-known comic book collector. She does a lot of business on the blockchain, but prefers to keep the details of her purchases, sales, customers and clients private. Luckily, she finds zkBob!

🐇 Alice uses 100 USDC to purchase 100 Bob tokens on Uniswap v3.&#x20;

🐇 She creates a zkBob account using the private key from an existing Ethereum Externally Owned Account (EOA). She could also create directly from a seed phrase, but chooses to create using MetaMask 🦊.

🐇 Once the account is connected, Alice deposits her 100 Bob into the pool. It is converted into shielded Bob (shBob).

🐇 Alice wants to buy an original Marvel comic from Carl.  She messages him privately and he sends her a private address he has generated in the zkBob app. Alice transfers 50 shBob to Carl. He mails the comics.

🐇 She is also owed some funds from Dave for a Ghost Rider. She sends him a generated address and receives 120 shBob. These transfers are catalogued in the UI and linked to her zkBob address, but not directly to her EOA.

🐇 Alice is ready to withdraw, but waits a few days to make sure the anonymity set has time to grow sufficiently. She orders a withdrawal to a newly generated EOA.&#x20;

🐇 Alice now has a new account with 170 Bob. She converts them back to 170 USDC on Uniswap. There is no way to determine the origin of the funds, and Alice, Carl and Dave are able to preserve their anonymity and grow their comic collections safely and securely, thanks to zkBob!

## Development & Deployment

zkBob is an application developed by [ZeroPool ](https://zeropool.network/)and [Blockscout](https://blockscout.com/) research groups. A production instance is planned for deployment in a decentralized manner via a [Trusted Setup Ceremony](deploying-zkbob/zkbob-solution-deployment/trusted-setup-ceremony.md) on a TBD chain. A multi-chain deployment is planned for an optimistic rollup in a future iteration.&#x20;

