---
description: What about $BOB
---

# BOB stablecoin FAQ

## How do I get BOB?

BOB is currently available on Polygon, Optimism and Ethereum. BOB can be acquired in several ways outside of the zkBob application.

* Sent between users to any 0x address on Polygon, Optimism or Ethereum.
* Swap tokens for BOB using Metamask.&#x20;
  * [Instructions](swap-bob-with-metamask-swap.md)
* Swap using Uniswap v3 or 1inch exchange.
  * [Instructions for new users](get-bob-on-uniswap-v3.md)
  * [Get BOB ](https://zkbob.page.link/getBOB)on 1inch exchange.

## How does BOB remain stable?

BOB token inventory is pre-minted and paired with an existing stable token (multi-collateral, for example USDC and BUSD) on decentralized exchanges featuring concentrated liquidity mechanisms (Uniswap v3, Kyberswap). The ability to set a narrow exchange rate range and provide concentrated liquidity for the pair results in very limited slippage to the stablecoin peg. [Learn More](https://docs.uniswap.org/protocol/concepts/V3-overview/concentrated-liquidity).

Called an **inventory LP position**, this mechanism maintains BOB stability while providing the option for users to purchase BOB inventory.

To enter the circulating supply, BOB must be purchased from the inventory. Users can then create their own LP positions from this purchased BOB, resulting in additional **non-inventory LP positions** (BOB/WETH, BOB/GNO etc) within the ecosystem.&#x20;

## How can I view BOB basic stats (tvl, volume etc)?

The easiest way to see stats by chain is through the Uniswap interface. Overviews can also be found on [CoinGecko](https://www.coingecko.com/en/coins/bob) or [CoinMarketCap](https://coinmarketcap.com/currencies/bob/).

* [BOB on Polygon](https://app.uniswap.org/#/tokens/polygon/0xb0b195aefa3650a6908f15cdac7d92f8a5791b0b)
* [BOB on Optimism](https://app.uniswap.org/#/tokens/optimism/0xb0b195aefa3650a6908f15cdac7d92f8a5791b0b)
* [BOB on Ethereum](https://app.uniswap.org/#/tokens/ethereum/0xb0b195aefa3650a6908f15cdac7d92f8a5791b0b)

For an overview of deposits, transfer volume and withdrawals within zkBob, see the dune analytics dashboard at [https://dune.com/maxaleks/zkbob](https://dune.com/maxaleks/zkbob)

## What are the BOB contract details?

**BOB contracts on Polygon:**

* BOB Token: [0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B](https://polygonscan.com/address/0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B)&#x20;
* BOB Token Implementation: [0x98DB3A72BeF2145A8F8d8B94F81317341Af2b08C](https://polygonscan.com/address/0x98DB3A72BeF2145A8F8d8B94F81317341Af2b08C)

**BOB on Ethereum (same addresses):**&#x20;

* BOB Token: [0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B ](https://etherscan.io/address/0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B)
* BOB Token Implementation: [0x98DB3A72BeF2145A8F8d8B94F81317341Af2b08C](https://etherscan.io/address/0x98DB3A72BeF2145A8F8d8B94F81317341Af2b08C)

**BOB on Optimism (same addresses):**

* BOB Token: [0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B](https://optimistic.etherscan.io/address/0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B)
* BOB Token Implementation: [0x98DB3A72BeF2145A8F8d8B94F81317341Af2b08C](https://optimistic.etherscan.io/address/0x98db3a72bef2145a8f8d8b94f81317341af2b08c)

**BOB on BSC:**

* BOB Token: [0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B](https://bscscan.com/token/0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B)
* BOB Token Implementation: [0xe0e184e850d24113ad512583b77621e35740befc](https://bscscan.com/address/0xe0e184e850d24113ad512583b77621e35740befc)&#x20;

**BOB attributes:**

* ERC20-based fungible tokens
* Upgradeable & Mintable (note upgradeability account and minting account must never be the same account)
* Meta-transaction support
* EIP677 support for `transferAndCall` functionality
* Address block list capability (similar to USDC)
* Recovery function(s) for lost/mis-sent tokens

## How is BOB inventory regulated?

BOB inventory is increased in LP positions via a multisig BOB Safe with a distributed reserve board. Inventory details are described and [catalogued here](bob-inventory.md).

## Can I earn additional BOB through zkBob or in other ways?

Not yet, but future functionality is planned to distribute funds earned from BOB activity. An auction mechanism is in development where users can bid on BOB rewards earned from LP positions, compounding, and lost tokens.\
\
_Details coming soon._

