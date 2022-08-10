---
description: Optimistic on the outside with a creamy zk center!
---

# Bob Stable Rollup

## 🧁 Stable Rollup Transactions

Bob is an optimistic rollup on Ethereum featuring a native, zk-based transactional application as a core primitive. This combination creates a scalable and secure L2 solution enhanced by privacy options.

A stable token (BOB) is optimized for the protocol and used for gas fees and transactions.&#x20;

Bob is designed for stability, security, and speed as L2s and rollups become the dominant scaling solution for Ethereum.&#x20;

## **Bob and Alice** 🐇&#x20;

_A use case for the zkBob transactional app._

Alice is a well-known comic book collector. She does a lot of business on the blockchain, but prefers to keep the details of her purchases, sales, customers and clients private. Luckily, she finds Bob rollup and zkBob!

🐇 Alice uses 100 USDC to purchase 100 Bob tokens on Uniswap v3 on Ethereum.&#x20;

🐇 She moves the Bob to the Bob Rollup (via a bridge or state channel) and  creates a zkBob account using the private key from an existing Ethereum Externally Owned Account (EOA). She could also create directly from a seed phrase, but chooses to create using MetaMask 🦊.

🐇 Once the account is connected, Alice deposits her 100 Bob into the zkBob pool. Here it is converted into shielded Bob (shBob).

🐇 Alice wants to buy an original Marvel comic from Carl.  She messages him privately and he sends her a private address he has generated in the zkBob app. Alice transfers 50 shBob to Carl. He mails the comics.

🐇 She is also owed some funds from Dave for a Ghost Rider. She sends him a generated address and receives 120 shBob. These transfers are catalogued in the UI and linked to her zkBob address, but not directly to her EOA.

🐇 Alice is ready to withdraw, but waits a few days to make sure the anonymity set has time to grow sufficiently. She orders a withdrawal to a newly generated EOA.&#x20;

🐇 Alice now has a new account with 170 Bob. She converts them back to 170 USDC on Uniswap. There is no way to determine the origin of the funds, and Alice, Carl and Dave are able to preserve their anonymity and grow their comic collections safely and securely, thanks to zkBob!

## Development & Deployment

Bob rollup is an is an application developed by the [Blockscout](https://blockscout.com/) research group with assistance from [ZeroPool ](https://zeropool.network/)for the zkBob application. A production instance is planned for deployment in a decentralized manner via a [Trusted Setup Ceremony](deploying-zkbob/zkbob-solution-deployment/trusted-setup-ceremony.md).&#x20;

