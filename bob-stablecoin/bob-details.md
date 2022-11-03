---
description: zkBob stablecoin with privacy options
---

# BOB Details

:heavy\_check\_mark: BOB is a multi-chain & multi-collateral stable token (stablecoin) enhanced with optional privacy features.

:heavy\_check\_mark: BOB can be acquired by swapping from other tokens using [Uniswap v3](get-bob-on-uniswap-v3.md) or [Metamask](swap-bob-with-metamask-swap.md) on Ethereum, Optimism and Polygon. BOB can also be transferred between users in a shielded form using the zkBOB application.

:heavy\_check\_mark:  BOB is optimized for zkBob. Once deposited, BOB can be sent privately between participants in the zkpool. Transfers are done completely within the application - there is no need to use or connect MetaMask, WalletConnect, or any other web3 wallet to conduct private transfers and you only need BOB, there is no additional fee token.

:heavy\_check\_mark: BOB inventory is currently available on Polygon, Optimism, and Ethereum. Additional chains may be added in the future to support multi-chain deposits and withdrawals.

:heavy\_check\_mark: BOB will be used to explore new mechanics for privacy, governance, and value capture for stablecoin users, such as redistribution of lost funds, compounding yield refunds, and other features.&#x20;

<details>

<summary>How do I get BOB tokens?</summary>

BOB is currently available on Polygon, Optimism and Ethereum. BOB can be acquired in several ways outside of the zkBob application.

* Sent between users to any 0x address on Polygon, Optimism or Ethereum.
* Swap tokens for BOB using Metamask.&#x20;
  * [Instructions](swap-bob-with-metamask-swap.md)
* Swap using Uniswap v3 or 1inch exchange.
  * [Instructions for new users](get-bob-on-uniswap-v3.md)
  * [Get BOB ](https://zkbob.page.link/getBOB)on 1inch exchange.

</details>

<details>

<summary>How do BOB tokens remain stable?</summary>

BOB token inventory is pre-minted and paired with an existing stable token (multi-collateral, for example USDC and BUSD) on Uniswap V3. Uniswap v3 features the ability to set a range for the exchange rate and provide concentrated liquidity for the pair, resulting in very limited slippage to the stablecoin peg. [Learn More](https://docs.uniswap.org/protocol/concepts/V3-overview/concentrated-liquidity).

Called an inventory LP position, this mechanism maintains BOB stability while providing the option for users to purchase BOB inventory.

To enter the circulating supply, BOB must be purchased from the inventory. Users can then create their own LP positions from this purchased BOB, resulting in additional non-inventory LP positions (BOB/WETH, BOB/GNO etc) within the ecosystem.&#x20;

</details>

<details>

<summary>How can I view BOB basic stats (tvl, volume etc)?</summary>

The easiest way to see stats by chain is through the Uniswap interface.

* [BOB on Polygon](https://app.uniswap.org/#/tokens/polygon/0xb0b195aefa3650a6908f15cdac7d92f8a5791b0b)
* [BOB on Optimism](https://app.uniswap.org/#/tokens/optimism/0xb0b195aefa3650a6908f15cdac7d92f8a5791b0b)
* [BOB on Ethereum](https://app.uniswap.org/#/tokens/ethereum/0xb0b195aefa3650a6908f15cdac7d92f8a5791b0b)

Overviews can also be found on [CoinGecko](https://www.coingecko.com/en/coins/bob) or [CoinMarketCap](https://coinmarketcap.com/currencies/bob/).

</details>

<details>

<summary>What are the BOB token contract details and implementation address?</summary>

**BOB contracts on Polygon:**

* BOB Token: [0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B](https://polygonscan.com/address/0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B)&#x20;
* BOB Token Implementation: [0x98DB3A72BeF2145A8F8d8B94F81317341Af2b08C](https://polygonscan.com/address/0x98DB3A72BeF2145A8F8d8B94F81317341Af2b08C)

**BOB on Ethereum (same addresses):**&#x20;

* BOB Token: [0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B ](https://etherscan.io/address/0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B)
* BOB Token Implementation: [0x98DB3A72BeF2145A8F8d8B94F81317341Af2b08C](https://etherscan.io/address/0x98DB3A72BeF2145A8F8d8B94F81317341Af2b08C)

**BOB on Optimism (same addresses):**

* BOB Token: [0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B](https://optimistic.etherscan.io/address/0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B)
* BOB Token Implementation: [0x98DB3A72BeF2145A8F8d8B94F81317341Af2b08C](https://optimistic.etherscan.io/address/0x98db3a72bef2145a8f8d8b94f81317341af2b08c)

**BOB token attributes:**

* ERC20-based fungible tokens
* Upgradeable & Mintable (note upgradeability account and minting account must never be the same account)
* Meta-transaction support
* EIP677 support for `transferAndCall` functionality
* Address block list capability (similar to USDC)
* Recovery function(s) for lost/mis-sent tokens

__

</details>

<details>

<summary>How is BOB inventory regulated?</summary>

BOB inventory is increased via a multisig BOB Safe with a distributed reserve board. Inventory increases are described and [catalogued here](bob-inventory.md).

</details>

<details>

<summary>How can I earn additional BOB tokens through the protocol?</summary>

This is not yet possible, but is planned for activation in a future version. An auction mechanism is in development where users can bid on BOB rewards earned from LP positions, compounding, and lost tokens.\
\
_Details coming soon._

</details>
