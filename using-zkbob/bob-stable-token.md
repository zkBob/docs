# BOB Stable Token

BOB tokens are stable tokens transferable 1-to-1 to USDC. They are designed to function specifically with the zkBob privacy pool. BOB can be swapped for USDC using Uniswap v3 on Gnosis Chain, then [deposited ](zkbob-app/deposits.md)to the zkBob application through the UI.

On deposit, BOB are converted to shBOB, a shielded version of the token which can be transacted privately within the application. On withdrawal, shBOB are converted back to BOB.

<details>

<summary>How do I get BOB tokens?</summary>

With Uniswap v3 on Gnosis Chain (or through direct transfer from another user). Details coming son.

</details>

<details>

<summary>How do BOB tokens remain stable?</summary>

BOB tokens are pre-minted and paired with an existing stable token (USDC) on Uniswap V3. Uniswap v3 features the ability to set a range for the exchange rate and provide concentrated liquidity for the pair, resulting  in limited slippage to the USDC peg.

</details>

<details>

<summary>What are the BOB token contract details and implementation address?</summary>

_More Info Coming Soon_

BOB tokens are deployed with the same contract address across multiple networks.

Basic BOB token attributes:

* ERC20-based fungible tokens
* Upgradeable & Mintable (note upgradeability account and minting account must not be the same account)
* Metatransaction support
* EIP677 support for `transferAndCall` functionality
* Address block list capability (similar to USDC)
* Recovery function(s) for lost/mis-sent tokens





</details>

<details>

<summary>How can I earn additional BOB tokens through the protocol?</summary>

This is not yet possible, but will be activated in the next version. A novel auction will be implemented where users who earn XP can bid on BOB rewards earned from LP positions and compounding.\
\
&#x20;_Auction details coming soon._

</details>
