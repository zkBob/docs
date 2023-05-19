---
description: BOB collateralization module
---

# BobSwap

BobSwap (also called BobVault) is a unique AMM designed to issue BOB from inventory into the circulating supply via stable-only swaps.

BobSwap does not have it's own UI, but is integrated into [1inch exchange](https://app.1inch.io/) on Ethereum and Polygon. Those interested in swapping USD-pegged assets (USDC, USDT or DAI) to BOB can simply visit 1inch and enter their desired swap. BobSwap is optimized to provide lower fees than many other available trading routes and will be used when it provides the best swap rate.

Current volume and other statistics related to BobSwap are available in Dune analytics (scroll to the bottom of the page to BobVault) [https://dune.com/zkbob/zkbob](https://dune.com/zkbob/zkbob)

{% hint style="info" %}
**BobSwap on Polygon**

* Contract: [`0x25E6505297b44f4817538fB2d91b88e1cF841B54`](https://polygonscan.com/address/0x25e6505297b44f4817538fb2d91b88e1cf841b54)
* Deployed on: 20.02.23 as per [GP 3](bob-governance-and-inventory/protocol-governance/gp-3-enable-bobvault-bobswap-for-public-use.md)

\
**BobSwap on Ethereum**

* Contract: [0x15729Ac1795Fa02448a55D206005dC1914144a9F](https://etherscan.io/address/0x15729Ac1795Fa02448a55D206005dC1914144a9F)
* Deployed on: 20.02.23 as per [GP5](bob-governance-and-inventory/protocol-governance/gp-5-enable-bobvault-bobswap-on-ethereum-mainnet.md)
{% endhint %}

## BobSwap parameters

Each collateral in BobSwap includes the following dynamic parameters. See [GP3](bob-governance-and-inventory/protocol-governance/gp-3-enable-bobvault-bobswap-for-public-use.md) and [GP5](bob-governance-and-inventory/protocol-governance/gp-5-enable-bobvault-bobswap-on-ethereum-mainnet.md) for specifics related to the deployments on Polygon and Ethereum mainnet.

1. **price** - amount of collateral with value equal to **1 BOB** (18 decimals)
2. **inFee** - proportional fee for buying BOB with given collateral (18 decimals, 1e18 = 100%)
3. **outFee** - proportional fee for selling BOB for given collateral (18 decimals, 1e18 = 100%)
4. **yield** - optional implementation contract for earning yield through lending markets (AAVE)
5. **buffer** - Collateral buffer for tokens to be kept outside of the yield-earning market. This reduces the frequency of deposit/withdraw operations and lowers expected value of the swap transaction gas fee.
6. **dust** - amount of collateral tokens that cannot be withdrawn as a farmed revenue, designed to account for unexpected rounding errors within the yield protocol and accrued permanent losses (if any).

## Optional Yield Implementation

This feature is currently enabled on Polygon and disabled on Ethereum mainnnet. When activated, a portion of the stable assets locked in the BobSwap contract are loaned to AAVE to generate additional revenue for the protocol.&#x20;

There is a buffer of each stable coin kept within the contract to support small stable swaps. If a single swap request is greater than the buffer, a call is made to the AAVE protocol to remove the necessary collateral and return it to the requester in one transaction.

Yield implementation may be activated on mainnet and/or undergo parameter updates in the future via a governance process.

