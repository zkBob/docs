---
description: zkBob private transfers
---

# zkBob Overview

## 🔐 Private Transactions

zkBob is an advanced blockchain privacy solution for safeguarding P2P financial transfers. With zkBob, it is easy to:

1. Deposit arbitrary token amounts into the application.
2. Transfer deposits to other participants using zkSnarks technology (proof of transaction without disclosing details of the sender, recipient, and value).
3. Withdraw arbitrary token amounts securely and privately.

To ensure privacy, zkBob leverages a zero-knowledge pool to anonymize transactions. Deposits of any amount can be made to the pool. Funds in the pool are converted to shielded tokens, which can then be transferred to other participants within the pool and/or withdrawn from the pool.

Transactions are processed through a relayer that constructs zkproofs and submits anonymous transactions to the pool contract.

Zero knowledge proofs ensure that transfers and withdrawals are decoupled from deposits, resulting in completely private transfers between parties.

## **How zkBob works for Alice** 🐇

🐇 Alice creates a zkBob account using the private key from an existing Ethereum EOA. She could also create directly from a seed phrase, but chooses to create using MetaMask.

🐇 Once the account is connected, Alice makes a deposit of 100 xDai into the pool. It is converted into zxDai.

🐇 Alice wants to transfer some zxDai to her friend Carl.  He sends her a private address he has generated within the zkBob app. Alice transfers 50 zxDai to Carl.

🐇 She is also owed some funds from Dave, so sends him a generated address and receives 120 zxDai. These transfers are catalogued in the UI and linked to her zkBob address.

🐇 Alice is ready to withdraw, but waits a few days to make sure the anonymity set has time to grow sufficiently. She orders a withdrawal and sends to a newly generated Ethereum address on the Gnosis Chain.&#x20;

🐇 Alice now has an account with 170 xDai. There is way to determine the origin of the funds, and Alice, Carl and Dave are able to preserve their anonymity!

_\<diagram here>_

## Development & Deployment

zkBob is developed by [ZeroPool ](https://zeropool.network)and the [Gnosis Chain](https://www.gnosischain.com) (GC) research teams. A production instance is planned for deployment via a [Trusted Setup Ceremony](technical-overview/zkbob-solution-deployment/trusted-setup-ceremony.md) on the Gnosis Chain, and a multi-chain deployment planned for deployment to an optimistic rollup.&#x20;

More details on the distributed deployment process will be available soon.





