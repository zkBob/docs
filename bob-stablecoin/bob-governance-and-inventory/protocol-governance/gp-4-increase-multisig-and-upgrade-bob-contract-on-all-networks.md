---
description: GP 4
---

# GP 4: Increase Multisig & Upgrade BOB contract on all networks

The BOB token contract was upgraded on the Polygon Network with [GP 2](gp-2-upgrade-contracts-to-v1.0.0.md). In GP 4, updates to the BOB token contract are carried over to Ethereum, Optimism, and BNB chain. In addition, a new signer is added to the BOB SAFE on each chain, which now requires 4 of 7 signatures to execute any proposal.

On Polygon, 1,000,000 BOB was also allocated to the BobVault, extending the issuance limit to 3,000,000 BOB.

{% hint style="success" %}
The proposal has been confirmed and executed on:&#x20;

* [Polygon](https://polygonscan.com/tx/0xd3ded6606bf47934d1fadb7e3c9561139b65c5cfed9ca8a1ad3ca2386f1935c3)
* [Ethereum Mainnet](https://etherscan.io/tx/0xe6daa3cb92b9b710c403c628ef871db70ea4bf41aa23f080222548feb6cee01d)
* [Optimism](https://optimistic.etherscan.io/tx/0x177ba2bda4ff8d1795755efe3cf0cf60773fa73a31cb73bbd249c9856349d749)
* [BNB Smart Chain](https://bscscan.com/tx/0x74797fa21d43c57eb16531458d3fd1d37da85570a63d17dca5442548a594c1f1)
{% endhint %}

## Proposal breakdown

Since the proposal consists of changes on different networks, there are 4 separate transactions, one on each network.

### Polygon

Transaction [#25](https://app.safe.global/matic:0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8/transactions/tx?id=multisig\_0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8\_0x09c53c7747e6d7321a137a83106b430c730a78c1250d0e22b3972971078533c2) in the Safe on Polygon contains 2 actions:

**Action 1**

Allocate additional **1.000.000 BOB** (18 decimals) to the BobVault contract [`0x25E6505297b44f4817538fB2d91b88e1cF841B54`](https://polygonscan.com/address/0x25e6505297b44f4817538fb2d91b88e1cf841b54) by making a minting 1.000.000 BOB to the BobVault contract. The action is executed by calling `mint` on the BOB token contract [`0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B`](https://polygonscan.com/address/0xb0b195aefa3650a6908f15cdac7d92f8a5791b0b#code)

**Action 2**

Add new owner [`0x813399e5b08Bb50b038AA7dF6347b6AF2D161828`](https://poanetwork.slack.com/archives/C04J40C09RQ/p1675709177285239?thread\_ts=1675345855.524239\&cid=C04J40C09RQ) to the BOB Policy Safe and increase the signatures thresholds to `4`. The action is executed by calling `addOwnerWithThreshold` on the Policy Safe contract [`0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8`](https://app.safe.global/matic:0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8)

### Ethereum

Transaction [#9](https://app.safe.global/eth:0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8/transactions/tx?id=multisig\_0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8\_0xc30ecd0cc9d61b1ac05650fd785e69a8c414e07e0a71edd74d986c83ef21ce02) in the Safe on Ethereum contains 2 actions:

**Action 1**

The BobToken contract upgrade [`0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B`](https://etherscan.io/address/0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B). The new implementation is [`0x4BF3C45E35f51a79261Db75236D4D9b717175505`](https://etherscan.io/address/0x4BF3C45E35f51a79261Db75236D4D9b717175505). The upgrade is made by using `upgradeToAndCall` and it is combined with the call of `DOMAIN_SEPARATOR` (the selector is `0x3644e515`) -- the method call is only to be used in pair with Tenderly to check that the domain separator is not being changing from the old implementation to the new one during the upgrade. The old domain separator is `0x89ae8e5c4b66ead9633eda9b816caf7be1b63c83da93250c795d803856f7c588`.

**Action 2**

Add new owner [`0x813399e5b08Bb50b038AA7dF6347b6AF2D161828`](https://poanetwork.slack.com/archives/C04J40C09RQ/p1675709177285239?thread\_ts=1675345855.524239\&cid=C04J40C09RQ)to the BOB Policy Safe and increase the signatures thresholds to `4`. The action is executed by calling `addOwnerWithThreshold` on the Policy Safe contract [`0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8`](https://app.safe.global/eth:0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8).

### Optimism

Transaction [#4](https://app.safe.global/oeth:0x14fc6a1a996A2EB889cF86e5c8cD17323bC85290/transactions/tx?id=multisig\_0x14fc6a1a996A2EB889cF86e5c8cD17323bC85290\_0x56edb470362d38c1379fdc389dc6eb7eb6b3b51c9f3e3e0945e6df3c27112ffc) in the Safe on Optimism contains 2 actions:

**Action 1**

The BobToken contract upgrade [`0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B`](https://optimistic.etherscan.io/address/0xb0b195aefa3650a6908f15cdac7d92f8a5791b0b). The new implementation is [`0x82907eAeB25D248dC82033E45b00A3E012Ba2d0D`](https://optimistic.etherscan.io/address/0x82907eAeB25D248dC82033E45b00A3E012Ba2d0D). The upgrade is made by using `upgradeToAndCall` and it is combined with the call of `DOMAIN_SEPARATOR` (the selector is `0x3644e515`). For reference, the old domain separator is `0xb23bf3c5aee6b73a93c5f441104927f0b7cd5fc945e7a1142b91792e9f9b72f7`.

**Action 2**

Add new owner [`0x813399e5b08Bb50b038AA7dF6347b6AF2D161828`](https://poanetwork.slack.com/archives/C04J40C09RQ/p1675709177285239?thread\_ts=1675345855.524239\&cid=C04J40C09RQ)to the BOB Policy Safe and increase the signatures thresholds to `4`. The action is executed by calling `addOwnerWithThreshold` on the Policy Safe contract ([`0x14fc6a1a996A2EB889cF86e5c8cD17323bC85290`](https://app.safe.global/oeth:0x14fc6a1a996A2EB889cF86e5c8cD17323bC85290)).

### BNB Smart Chain

Transaction [#6](https://app.safe.global/bnb:0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8/transactions/tx?id=multisig\_0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8\_0xdfb7b73a00720c91d1334fa893407d0af3dcb93caaf44f0459ea9879ca3033bc) in the Safe on BSC contains 2 actions:

**Action 1**

The BobToken contract upgrade [`0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B`](https://bscscan.com/address/0xb0b195aefa3650a6908f15cdac7d92f8a5791b0b). The new implementation is [`0xe9082b12bb1ff20e8749cd5ef9bd2b29c5ef5695`](https://bscscan.com/address/0xe9082b12bb1ff20e8749cd5ef9bd2b29c5ef5695). The upgrade is made by using `upgradeToAndCall` and it is combined with the call of `DOMAIN_SEPARATOR` (the selector is `0x3644e515`). For reference, the old domain separator is `0x6b959b12abe54c05b628f48312e1fa44953373c582433e9d3fb922ff7673eaf1`.

**Action 2**

Add new owner [`0x813399e5b08Bb50b038AA7dF6347b6AF2D161828`](https://poanetwork.slack.com/archives/C04J40C09RQ/p1675709177285239?thread\_ts=1675345855.524239\&cid=C04J40C09RQ) to the BOB Policy Safe and increase the signatures thresholds to `4`. The action is executed by calling `addOwnerWithThreshold` on the Policy Safe contract [`0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8`](https://app.safe.global/bnb:0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8).



