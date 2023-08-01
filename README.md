---
description: A stablecoin-based privacy wallet build for everyday users
---

# zkBob

<figure><img src=".gitbook/assets/readme2.jpg" alt=""><figcaption></figcaption></figure>

## Get Started

> :man: [zkBob App](https://app.zkbob.com/)\
> :man\_mage: [BOB Stablecoin](broken-reference)\
> :man\_swimming: [Info and Instructions](zkbob-app/zkbob-app.md)\
> :person\_running:[Technical Details and Contracts](broken-reference)\
> 🔐 [Security Audit](resources/security-audit.md)

## About

[zkBob](https://app.zkbob.com) is a stablecoin-based privacy application deployed on Polygon and Optimism and designed for everyday users and [common use cases](zkbob-overview/basic-concepts/use-cases/). zkBob uses [zkSNARKS](implementation/zksnarks-and-circuits/) to anonymize senders, receivers, and amounts when transferring stable funds. [Compliance features](zkbob-overview/compliance-and-security/) deter bad actors and illicit usage, giving privacy and safety back to ordinary blockchain users.&#x20;

zkBob was developed for use with the [BOB token](zkbob-overview/bob-stablecoin.md), a multi-chain stable token (stablecoin) enhanced with optional privacy. Once BOB is deposited into the zkBob pool, participants can transfer any amount\* of BOB amongst themselves in a private, secure manner without needing to connect MetaMask, WalletConnect or any web3 wallet.

Now that BOB pools have been used effectively, new pools for ETH and USDC will be rolling out soon.

<figure><img src=".gitbook/assets/home-page-1.png" alt=""><figcaption></figcaption></figure>

When a transfer is initiated, the amount and recipient is never disclosed or published. Transactions are routed through a [relayer](implementation/relayer-node/), abstracting gas fees while providing an efficient transfer environment. Deposits, transfers and withdrawals are all processed on Polygon or Optimism, with standardized gas fees ($0.10 per tx on MATIC, variable on Optimism) paid using BOB tokens. MATIC/ETH is not needed for any of these actions, simplifying usage.

* The [zkBob application](https://app.zkbob.com/) is multichain (**Polygon & Optimism**) to utilize existing infrastructure (Uniswap v3, Aave, and native USDC), prioritize scalability, and support their commitment to zk-based solutions.
* The [BOB stablecoin](zkbob-overview/bob-stablecoin.md) is currently available on Polygon, Optimism, BNB Chain,  Ethereum and Arbitrum with additional chains on the horizon.&#x20;

_\*zkBob introduces_ [_deposit and withdrawal limits_](zkbob-overview/deposit-and-withdrawal-limits.md) _and other_ [_compliance features_](zkbob-overview/compliance-and-security/) _to keep the application and its users safe. Transfers are limited by these pool constraints._&#x20;

## Project Landing Pages

* zkBob application: [https://zkbob.com/](https://zkbob.com/)
* BOB stablecoin: [https://bob.zkbob.com/](https://bob.zkbob.com/)

## Newsletter & Blog

[Sign up for the zkBob Blog](https://blog.zkbob.com/) to receive the latest updates about zkBob.



###

