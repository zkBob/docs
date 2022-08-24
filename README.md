---
description: A stablecoin-based protocol designed for simplicity, privacy and utility.
---

# Meet Bob

Bob protocol is an easy-to-use protocol designed to give regular crypto users new stablecoin-based utility. Users swap USDC 1-to-1 for BOB tokens to get started. BOB can then be used in conjunction with the zkBob app to conduct small, discreet transactions between protocol users.

zkBob is a zk-based application which introduces a shielded transaction pool.  zkBob enables secure, limited-value, private stablecoin transfers between users. [Deposit limits](bob-overview/deposit-limits.md) and [compliance features](bob-overview/compliance.md) provide a safe transactional environment for everyday users.

zkBob is a free application to use. Transaction fees (USDC to BOB swap fees and zkBob transactions) are subsidized at project launch, and future iterations will incorporate compounding, lost token recovery, and other mechanisms to create an evergreen platform.

Bob protocol will initially be deployed on Polygon to take advantage of existing infrastructure (Uniswap v3, Aave, and native USDC) and to support their commitment to zk-based solutions. [Learn More](bob-overview/bob-on-polygon.md).

## **Bob and Alice** 🐇&#x20;

_A use case for the zkBob transactional app._

Alice is a well-known comic book collector. She does a lot of business on the blockchain, but prefers to keep the details of her purchases, sales, customers and clients private. Luckily, she finds Bob!

🐇 Alice uses 100 USDC to purchase 100 Bob tokens on Uniswap v3 on Polygon.&#x20;

🐇 She creates a zkBob account using the private key from an existing Ethereum Externally Owned Account (EOA). She could also create directly from a seed phrase, but chooses to create using MetaMask 🦊.

🐇 Once the account is connected, Alice deposits her 100 Bob into the zkBob pool. Here it is converted into shielded Bob (shBob).

🐇 Alice wants to buy an original Marvel comic from Carl.  She messages him privately and he sends her a private address he has generated in the zkBob app. Alice transfers 50 shBob to Carl. He mails the comics.

🐇 She is also owed some funds from Dave for a Ghost Rider. She sends him a generated address and receives 120 shBob. These transfers are catalogued in the UI and linked to her zkBob address, but not directly to her EOA.

🐇 Alice is ready to withdraw, but waits a few days to allow the anonymity set to grow. After a few days she orders a withdrawal to a newly generated EOA.&#x20;

🐇 Alice now has a new account with 170 BOB. She converts them back to 170 USDC on Uniswap. There is no way to determine the origin of the funds, and Alice, Carl and Dave are able to preserve their anonymity and grow their comic collections safely and securely, thanks to zkBob!

## Development & Deployment

Bob rollup is an is an application originally developed by the xDai research group with assistance from [ZeroPool ](https://zeropool.network/)for the zkBob application. A production instance is planned for deployment in a decentralized manner via a [Trusted Setup Ceremony](deployment/trusted-setup-ceremony.md).&#x20;

