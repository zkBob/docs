---
description: GP 3
---

# GP 3: Enable BobVault for Public Use

Changes were approved following the security audit and [contracts upgrade to v1.0.0](gp-2-upgrade-contracts-to-v1.0.0.md).&#x20;

{% hint style="success" %}
* GP #3
* Timestamp: Jan-11-2023 06:30:54 PM +UTC
* Tx: [0xb29d804f5d2324a458dbbaff2c5da7d5e73c286bf42891f5816b030dfac119bc](https://polygonscan.com/tx/0xb29d804f5d2324a458dbbaff2c5da7d5e73c286bf42891f5816b030dfac119bc)&#x20;
{% endhint %}

The transaction included 6 actions categorized in the [proposal breakdown section](gp-3-enable-bobvault-for-public-use.md#proposal-breakdown).

## Introduction to BobVault

BobVault [`0x25E6505297b44f4817538fB2d91b88e1cF841B54`](https://polygonscan.com/address/0x25e6505297b44f4817538fb2d91b88e1cf841b54) is a module for issuing BOB collateralised with other USD-pegged assets.

BobVault has received substantial testing using **USDC** and **USDT** as collaterals along with their passive investments into **AAVE**. BobVault was initially funded for **1,000 BOB** for testing purposes. This governance proposal reimburses the testing team with that amount.

Each collateral in BobVault includes the following dynamic parameters:

1. **price** - amount of collateral with value equal to **1 BOB** (18 decimals)
2. **inFee** - proportional fee for buying BOB with given collateral (18 decimals, 1e18 = 100%)
3. **outFee** - proportional fee for selling BOB for given collateral (18 decimals, 1e18 = 100%)
4. **yield** - optional implementation contract for earning yield through lending markets (e.g. AAVE)
5. **buffer** - amount of buffer for collateral tokens to be kept outside of yield-earning market. This reduces the frequency of deposit/withdraw operations and lowers expected value of the swap transaction gas fee.
6. **dust** - amount of collateral tokens that cannot be withdrawn as a farmed revenue, designed to account for unexpected rounding errors within the yield protocol and accrued permanent losses (if any).

## Proposal objective

After the completion of the security audit and upgrade of all contracts in the prior governance proposal [Upgrade of BOB Protocol contracts to the release 1.0.0](gp-2-upgrade-contracts-to-v1.0.0.md), the Bob protocol management team approved an increase of the **BOB** issuance limits through BobVault to **1,000,000 BOB**, along with the following collateral configuration:

**USDC:**

1. **price** - 1 (6 decimals)
2. **inFee** - ~~0.01%~~ → 0.008% (18 decimals)
3. **outFee** - 0.01% (18 decimals)
4. **yield** - [`0x59cc168654Dbb7f6874115bf47Ac7312ceCdB6de`](https://polygonscan.com/address/0x59cc168654Dbb7f6874115bf47Ac7312ceCdB6de) - yield earning implementation through AAVE v3 Polygon deployment
5. **buffer** - ~~100 USDC~~ → 10,000 USDC (6 decimals)
6. **dust** - ~~0.001 USDC~~ → 1 USDC (6 decimals)

**USDT:**

1. **price** - 1 (6 decimals)
2. **inFee** - 0.1% (18 decimals)
3. **outFee** - 0% (18 decimals)
4. **yield** - [`0x59cc168654Dbb7f6874115bf47Ac7312ceCdB6de`](https://polygonscan.com/address/0x59cc168654Dbb7f6874115bf47Ac7312ceCdB6de) - yield earning implementation through AAVE v3 Polygon deployment
5. **buffer** - ~~100 USDT~~ → 10.000 USDT (6 decimals)
6. **dust** - ~~0.001 USDT~~ → 1 USDT (6 decimals)

The main goal for these parameters is to allow the BobVault to start slowly acquiring more **USDC** collateral as it migrates from other sources (e.g. Uniswap) and starts earning additional yield.

This is expected to happen organically over time, as buying **BOB** with **USDC** becomes a bit cheaper through BobVault than via other means, while selling **BOB** for **USDC** costs approximately the same as through other means.

**USDC** is expected to be a dominant BobVault collateral, as it is listed with more favorable terms compared to the configuration used for **USDT**. This might change over time, depending on future governance proposals.

## Proposal breakdown

The corresponding transaction in the BOB governance safe is [transaction #23](https://app.safe.global/matic:0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8/transactions/tx?id=multisig\_0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8\_0x16dea760a7f8da340fb16c0bd11d8b9f2afc613603d467c1b1558dc469cbd179).

### Action 1

Call `setCollateralFees` (selector `0xd2794f63`) to update fees for USDC [`0x2791Bca1f2de4661ED88A30C99A7a9449Aa84174`](https://polygonscan.com/token/0x2791bca1f2de4661ed88a30c99a7a9449aa84174) collateral in BobVault:

1. inFee: 0.01% → **0.008%** (18 decimals)
2. outFee: **0.01%** (left unchanged, 18 decimals)

### Action 2

Call `updateCollateralYield` (selector `0x20d22739`) to update yield parameters for USDC [`0x2791Bca1f2de4661ED88A30C99A7a9449Aa84174`](https://polygonscan.com/token/0x2791bca1f2de4661ed88a30c99a7a9449aa84174) collateral in BobVault, which is invested in AAVE:

1. buffer: 100 USDC → **10,000 USDC** (6 decimals)
2. dust: 0.001 USDC → **1 USDC** (6 decimals)

### Action 3

Call `updateCollateralYield` (selector `0x20d22739`) to update yield parameters for USDT [`0xc2132D05D31c914a87C6611C10748AEb04B58e8F`](https://polygonscan.com/token/0xc2132d05d31c914a87c6611c10748aeb04b58e8f) collateral in BobVault, which is invested in AAVE:

1. buffer: 100 USDT → **10,000 USDT** (6 decimals)
2. dust: 0.001 USDT → **1 USDT** (6 decimals)

### Action 4

Mint **1,000,000 BOB** (18 decimals) to governance safe [`0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8`](https://polygonscan.com/address/0xd4a3d9ca00fa1fd8833d560f9217458e61c446d8) for allocation to BobVault. The action is executed by calling `mint` on the BOB token contract [`0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B`](https://polygonscan.com/address/0xb0b195aefa3650a6908f15cdac7d92f8a5791b0b#code)`.`

### Action 5

Allocate **999,000 BOB** (18 decimals) to the BobVault contract [`0x25E6505297b44f4817538fB2d91b88e1cF841B54`](https://polygonscan.com/address/0x25e6505297b44f4817538fb2d91b88e1cf841b54)by making a BOB ERC20 `transfer` from the governance safe to the BobVault contract. The action is executed on the BOB token contract [`0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B`](https://polygonscan.com/address/0xb0b195aefa3650a6908f15cdac7d92f8a5791b0b#code)

### Action 6

Refund the BOB testing team with **1,000 BOB** (18 decimals) for [initial test funding](https://polygonscan.com/tx/0x63641a42799c242f1c323a9759667825f50df724c7ee6d8c267fc257e8def97e) of the BobVault contract [`0x25E6505297b44f4817538fB2d91b88e1cF841B54`](https://polygonscan.com/address/0x25e6505297b44f4817538fb2d91b88e1cf841b54).

Refund is made by executing a BOB ERC20 `transfer` from the governance safe to the Bob protocol team EOA address: [`0x02BF3258D6024B2B34fD7D21F225Db6CDA939E76`](https://polygonscan.com/address/0x02bf3258d6024b2b34fd7d21f225db6cda939e76). The action is executed on the BOB token contract [`0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B`](https://polygonscan.com/address/0xb0b195aefa3650a6908f15cdac7d92f8a5791b0b#code).

## Additional verification

Existing configuration parameters for collaterals can be checked by calling the `collateral(address)` function in the BobVault contract:

{% code overflow="wrap" %}
```bash
$ cast call  --rpc-url https://rpc.ankr.com/polygon 0x25E6505297b44f4817538fB2d91b88e1cF841B54 'collateral(address) (uint128 balance,uint128 buffer,uint96 dust,address yield,uint128 price,uint64 inFee,uint64 outFee)' 0xc2132D05D31c914a87C6611C10748AEb04B58e8F
10377731
100000000
1000
0x59cc168654Dbb7f6874115bf47Ac7312ceCdB6de
1000000
1000000000000000
0
$ cast call  --rpc-url https://rpc.ankr.com/polygon 0x25E6505297b44f4817538fB2d91b88e1cF841B54 'collateral(address) (uint128 balance,uint128 buffer,uint96 dust,address yield,uint128 price,uint64 inFee,uint64 outFee)' 0x2791Bca1f2de4661ED88A30C99A7a9449Aa84174
8302667
100000000
1000
0x59cc168654Dbb7f6874115bf47Ac7312ceCdB6de
1000000
100000000000000
100000000000000
```
{% endcode %}

