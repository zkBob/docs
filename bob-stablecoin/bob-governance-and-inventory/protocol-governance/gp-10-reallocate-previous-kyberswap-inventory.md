# GP 10: Reallocate previous Kyberswap inventory

{% hint style="success" %}
Proposal confirmed and executed in the following transactions:

* Ethereum
  * Safe transaction [#13](https://app.safe.global/transactions/tx?safe=eth:0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8\&id=multisig\_0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8\_0xc4b72c6573bbe14bc075acce9cdc4dc0a72e2d6df15d8841139af8a76f8d7679)
  * Ethereum tx: [https://etherscan.io/tx/0xdcf96c97c5340f0023d2cd378b0d1e89b3433cb24817260103a4c7fff84446df](https://etherscan.io/tx/0xdcf96c97c5340f0023d2cd378b0d1e89b3433cb24817260103a4c7fff84446df)
* BNB Smart Chain
  * Safe transaction [#9](https://app.safe.global/transactions/queue?safe=bnb:0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8)
  * BNB tx: [https://bscscan.com/tx/0x337deca24b6bcd018b785edd4e6efe788dd4125ebf110d83495d649a2d9bc0ab](https://bscscan.com/tx/0x337deca24b6bcd018b785edd4e6efe788dd4125ebf110d83495d649a2d9bc0ab)
{% endhint %}

## Proposal Objective

Following [GP 9](gp-9-deactivate-kyberswap-inventory-pairs-emergency-measure.md), an emergency proposal to remove inventory from Kyberswap pairs on Mainnet and BNB chain, adjustments and reallocation of funds are proposed in this GP. The result will be a redistribution to several Uniswap pools and removal of some BOB from inventory. **The overall decrease of total supply after this proposal is -3m BOB (52.5m → 49.5m).**

### Mainnet

1. Move Kyberswap USDT/BOB 0.008% inventory funds into Uniswap V3 USDT/BOB 0.01% inventory (**2,000,000 BOB**).
2. Remove **2,000,000 BOB** from Kyberswap USDC/BOB 0.008% inventory as the Uniswap V3 USDC/BOB inventory already holds a sufficient amount of funds.

### BNB Smart Chain

1. Move Kyberswap USDT/BOB 0.008% inventory funds into Uniswap V3 USDT/BOB 0.01% inventory (**2,000,000 BOB**)
2. Move Kyberswap USDC/BOB 0.008% inventory funds into Uniswap V3 USDC/BOB 0.01% inventory (**2,000,000 BOB**)
3. Remove **1,000,000 BOB** from Kyberswap BUSD/BOB 0.008% inventory, as BUSD is being gradually deprecated.

## Moving Funds

Moving funds between inventory pairs requires several system swap transactions throughout the execution, since the funds are stored and allocated in different proportions (this is a limitation of existing AMM protocols like Uniswap or Kyberswap).&#x20;

To facilitate the swaps in this proposal, customized 1inch limit orders using a separate one-time helper contract are constructed. Following successful proposal execution, 1inch resolvers or other BOB counterparties will asynchronously fill the orders.

## Proposal and Transaction Breakdown

Since the proposal consists of changes on 2 different networks, there are 2 different transactions explained below.

## Ethereum Mainnet

Transaction [#13](https://app.safe.global/transactions/tx?safe=eth:0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8\&id=multisig\_0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8\_0xc4b72c6573bbe14bc075acce9cdc4dc0a72e2d6df15d8841139af8a76f8d7679) in the Safe on Mainnet contains 6 actions:

**Action 1**

Approve **1,999,985 BOB** (18 decimals) for inventory allocation into Uniswap V3 BOB/USDT 0.01% inventory pair through the helper contract counterparty. [`0xCDAD0ad4DD1F614a6502043Ef546e447b25Ffb99`](https://etherscan.io/address/0xCDAD0ad4DD1F614a6502043Ef546e447b25Ffb99)

**Action 2**

Approve **15 USDT** (6 decimals) for inventory allocation into Uniswap V3 BOB/USDT 0.01% inventory pair through the helper contract counterparty [`0xCDAD0ad4DD1F614a6502043Ef546e447b25Ffb99`](https://etherscan.io/address/0xCDAD0ad4DD1F614a6502043Ef546e447b25Ffb99)

**Action 3**

Mint part of the inventory BOB/USDT position through the helper contract counterparty. The action is executed by calling `mint` on the helper contract [`0xCDAD0ad4DD1F614a6502043Ef546e447b25Ffb99`](https://etherscan.io/address/0xCDAD0ad4DD1F614a6502043Ef546e447b25Ffb99)

During simulations, this action results in **1,999,985 BOB + 0 USDT**  allocated into the inventory position. However exact amounts might change with Uniswap pool state changes. The helper contract will make sure to create two 1-to-1 limit orders for the remaining funds. During the initial simulations, this action resulted in **15 USDT → 15 BOB** limit order being created.

Once the limit order is filled, swapped tokens will be automatically and atomically added into the existing inventory position. This will happen asynchronously following proposal execution.&#x20;

See [additional verification](gp-10-reallocate-previous-kyberswap-inventory.md#additional-verification) for simulation examples.

**Action 4**

Approve **38,190.381903 USDC** (6 decimals) to the BobSwap [`0x15729Ac1795Fa02448a55D206005dC1914144a9F`](https://etherscan.io/address/0x15729Ac1795Fa02448a55D206005dC1914144a9F) contract for conversion to BOB.

**Action 5**

Convert **38,190.381903 USDC** (6 decimals) into **38,190 BOB** (18 decimals) through BobSwap [`0x15729Ac1795Fa02448a55D206005dC1914144a9F`](https://etherscan.io/address/0x15729Ac1795Fa02448a55D206005dC1914144a9F). A commission of **0.381903 USDC** is paid for this swap to BobSwap.

The action is executed by calling `buy` on the BobSwap contract. [`0x15729Ac1795Fa02448a55D206005dC1914144a9F`](https://etherscan.io/address/0x15729Ac1795Fa02448a55D206005dC1914144a9F)

**Action 6**

Remove **2,000,000 BOB** (18 decimals) from prior Kyberswap BOB/USDC 0.008% inventory (s_end to null address_).

Part of the removed funds effectively come from **Action 5.**

{% hint style="info" %}
**Note:** The inventory position use tick range: `[-276325, -276323]`, as **BOB** has 18 decimals and **USDT** has 6 decimals
{% endhint %}

## BNB Smart Chain

Transaction [#9](https://app.safe.global/transactions/queue?safe=bnb:0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8) in the Safe on BNB Chain contains 6 actions:

**Action 1**

Remove **1,000,000 BOB** (18 decimals) from prior Kyberswap BOB/BUSD 0.008% inventory (s_end to Null address_).

**Action 2**

Approve **2,000,000** **BOB** (18 decimals) for inventory allocation into Uniswap V3 BOB/USDT 0.01% inventory pair through the helper contract counterparty [`0x0eF655F7Cee3D430302BC7D3d491aF295CB40401`](https://bscscan.com/address/0x0eF655F7Cee3D430302BC7D3d491aF295CB40401)

**Action 3**

Approve **108,200 USDC** (6 decimals) for inventory allocation into Uniswap V3 BOB/USDC 0.01% inventory pair through the helper contract counterparty. [`0x525b4E120dDC602fF055Aa86803acD7D71F0c753`](https://bscscan.com/address/0x525b4E120dDC602fF055Aa86803acD7D71F0c753)

**Action 4**

Approve **1,891,800 BOB** (18 decimals) for inventory allocation into Uniswap V3 BOB/USDC 0.01% inventory pair through the helper contract counterparty [`0x525b4E120dDC602fF055Aa86803acD7D71F0c753`](https://bscscan.com/address/0x525b4E120dDC602fF055Aa86803acD7D71F0c753)

**Action 5**

Mint part of the inventory BOB/USDT position through the helper contract counterparty. The action is executed by calling `mint` on the helper contract [`0x0eF655F7Cee3D430302BC7D3d491aF295CB40401`](https://bscscan.com/address/0x0eF655F7Cee3D430302BC7D3d491aF295CB40401)

During the initial proposal simulations, this action results in all **2,000,000 BOB + 0 USDT** being allocated into inventory position. However exact amounts might change with Uniswap pool state changes. Helper contract will make sure to create two 1-to-1 limit orders for the remaining funds.

Once the limit order is filled, swapped tokens will be automatically and atomically added into the existing inventory position. This will happen asynchronously after the proposal execution. See [Additional verification](https://www.notion.so/Additional-verification-c1147c20bc474ac186d23cf40eb62840) for simulation example.

**Action 6**

Mint part of the inventory BOB/USDC position through the helper contract counterparty. The action is executed by calling `mint` on the helper contract [`0x525b4E120dDC602fF055Aa86803acD7D71F0c753`](https://bscscan.com/address/0x525b4E120dDC602fF055Aa86803acD7D71F0c753)

During the initial proposal simulations, this action results in all **1,891,800 BOB + 7,435 USDC** being allocated into inventory position. However exact amounts might change with Uniswap pool state changes. The helper contract will make sure to create two 1-to-1 limit orders for the remaining funds. During the initial proposal simulations, this action resulted in **100,765 USDC → 100,765 BOB** limit order being created.

Once the limit order is filled, swapped tokens will be automatically and atomically added into the existing inventory position. This will happen asynchronously after the proposal execution.&#x20;

See [additional verification](gp-10-reallocate-previous-kyberswap-inventory.md#additional-verification) for the simulation example.

{% hint style="info" %}
**Note:** Both inventory positions use tick range: `[-1, 1]`, as both tokens have 18 decimals
{% endhint %}

## Additional verification

Inventory LPs validity can be verified using the following simulation test -[https://gist.github.com/k1rill-fedoseev/8537cc9a3f1753b0d579e1af662834bb](https://gist.github.com/k1rill-fedoseev/8537cc9a3f1753b0d579e1af662834bb)

Verify logic of helper contracts facilitating inventory minting and limit orders execution:

* Mainnet BOB/USDT inventory minter [`0xCDAD0ad4DD1F614a6502043Ef546e447b25Ffb99`](https://etherscan.io/address/0xCDAD0ad4DD1F614a6502043Ef546e447b25Ffb99)
* BNB BOB/USDT inventory minter - [`0x0eF655F7Cee3D430302BC7D3d491aF295CB40401`](https://bscscan.com/address/0x0eF655F7Cee3D430302BC7D3d491aF295CB40401)
* BNB BOB/USDC inventory minter - [`0x525b4E120dDC602fF055Aa86803acD7D71F0c753`](https://bscscan.com/address/0x525b4E120dDC602fF055Aa86803acD7D71F0c753)

{% hint style="info" %}
Extra notes on Uniswap-related math: [Uniswap V3 Math Nuances](https://www.notion.so/Uniswap-V3-Math-Nuances-d84c06bbe5f748129cab1aadcc9c1467)
{% endhint %}

