---
description: A stablecoin-based zkprotocol designed for simplicity, privacy and utility.
---

# zkBob

<figure><img src=".gitbook/assets/readme2.jpg" alt=""><figcaption></figcaption></figure>

zkBob simplifies secure, limited-value, and anonymous stablecoin transfers for everyday users. The application accepts [BOB](broken-reference), a multi-chain stable token (stablecoin) enhanced with optional privacy features. Once BOB is deposited in the zkBob app, pool participants can transfer any amount\* of BOB amongst themselves in a private, secure manner without needing to connect MetaMask, WalletConnect or any web3 wallet.

The shielded zkBob pool uses [zkSNARKs](implementation/zksnarks-and-circuits/) to limit public data exposure. When a transfer is initiated, the amount and recipient is never disclosed or published. Transactions are routed through a relayer, abstracting gas fees while providing an efficient transfer environment.&#x20;

The [BOB stablecoin](bob-stablecoin/bob-details.md) is currently available on Polygon, Optimism, and Ethereum mainnet with additional chains on the horizon. The zkBob application is deployed on Polygon to utilize existing infrastructure (Uniswap v3, Aave, and native USDC), prioritize scalability, and support their commitment to zk-based solutions.

_\*zkBob introduces_ [_deposit and withdrawal limits_](zkbob-overview/deposit-and-withdrawal-limits.md) _to deter bad actors and illegal usage of the application. Transfers are limited by these pool constraints._&#x20;

### Get Started!

> :man: [zkBob App](https://app.zkbob.com/)\
> :man\_mage: [Learn about the BOB Stablecoin](broken-reference)\
> :man\_swimming: [Info and UI Instructions](zkbob-app/zkbob-app.md)\
> :woman\_shrugging: [FAQs](zkbob-overview/faq.md)\
> :person\_running:[Technical Details and Contracts](broken-reference)

