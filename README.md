---
description: zkBob private transfers
---

# Private Transactions

## 🔐 Private Transactions

zkBob is an advanced blockchain privacy solution for safeguarding P2P financial transfers. With zkBob, it is easy to:

1. [Setup](zkbob-getting-started/zkbob-app/account-creation/) a zk account using a seed phrase or existing web3 wallet.
2. [Deposit ](zkbob-getting-started/zkbob-app/deposits.md)arbitrary token amounts into the application.
3. [Transfer](zkbob-getting-started/zkbob-app/transfers.md) deposits to other participants using zkSnarks technology (proof of transaction without disclosing details of the sender, recipient, and value).
4. [Withdraw](zkbob-getting-started/zkbob-app/withdrawals.md) arbitrary token amounts securely and privately.

To ensure privacy, zkBob leverages a zero-knowledge pool to anonymize transactions. Deposits of any amount can be made to the pool. Funds in the pool are converted to shielded tokens, which can then be transferred to other participants within the pool and/or withdrawn from the pool.

Transactions are processed through a relayer that constructs zkproofs and submits anonymous transactions to the pool contract.

Zero knowledge proofs ensure that transfers and withdrawals are decoupled from deposits, resulting in completely private transfers between parties.

## **zkBob and Alice** 🐇

Alice is a well-known comic book collector. She does a lot of business on the blockchain, but prefers to keep the details of her purchases, sales, customers and clients private. Luckily, she finds zkBob!

🐇 Alice creates a zkBob account using the private key from an existing Ethereum Externally Owned Account (EOA). She could also create directly from a seed phrase, but chooses to create using MetaMask 🦊.

🐇 Once the account is connected, Alice makes a deposit of 100 xDai into the pool. It is converted into shielded xDai (sxDai).

🐇 Alice wants to buy an original Marvel comic from Carl.  She messages him privately and he sends her a private address he has generated in the zkBob app. Alice transfers 50 sxDai to Carl. He mails the comics.

🐇 She is also owed some funds from Dave for a Ghost Rider. She sends him a generated address and receives 120 zxDai. These transfers are catalogued in the UI and linked to her zkBob address, but not directly to her EOA.

🐇 Alice is ready to withdraw, but waits a few days to make sure the anonymity set has time to grow sufficiently. She orders a withdrawal to a newly generated EOA on the Gnosis Chain.&#x20;

🐇 Alice now has an new account with 170 xDai. There is way to determine the origin of the funds, and Alice, Carl and Dave are able to preserve their anonymity and grow their comic collections safely and securely, thanks to zkBob!

_\<diagram here>_

## Development & Deployment

zkBob is an application developed by [ZeroPool ](https://zeropool.network)and the [Gnosis Chain](https://www.gnosischain.com) (GC) research groups. A production instance is planned for deployment via a [Trusted Setup Ceremony](deploying-zkbob/zkbob-solution-deployment/trusted-setup-ceremony.md) on the Gnosis Chain, and a multi-chain deployment is planned for an optimistic rollup in a future iteration.&#x20;

More details on the distributed deployment process will be available soon.





