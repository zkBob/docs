# Inventory Management

To facilitate inventory, BOB liquidity is deployed on DEXs including Uniswap v3 & Kyberswap and paired with a stable asset such as USDC or BUSD. &#x20;

Inventory positions are tuned to a very narrow range and maintained through the [AMM concentrated liquidity algorithm](https://docs.uniswap.org/concepts/protocol/concentrated-liquidity). This keeps BOB stable, and is known as an **inventory LP position**.

BOB can be purchased from inventory at \~1:1 for USD stable assets. Any BOB in circulation has been purchased through an inventory LP position, meaning it is backed 100% by stable user collateral at the time of purchase.

{% hint style="info" %}
Inventory and collateralized supply are [tracked here](https://dune.com/maxaleks/bob-stable-token).
{% endhint %}

Users may choose to create their own **non-inventory LP positions** using purchased BOB + another tokens of their choice (for example BOB/WETH, BOB/WMATIC, BOB/OP, BOB/USDT etc).&#x20;

Additional decentralization measures including broader community-driven governance and timelocks are in development to maintain and balance optimal BOB inventory based on usage and demand.

Inventory increases and decreases are detailed on the [Inventory Actions](inventory-actions.md) page.

###
