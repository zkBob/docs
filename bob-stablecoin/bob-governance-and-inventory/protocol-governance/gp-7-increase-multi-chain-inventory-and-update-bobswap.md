# GP 7: Increase Multi-chain Inventory and Update BobSwap

{% hint style="success" %}
The proposal has been confirmed and executed on:&#x20;

* [Polygon](https://app.safe.global/transactions/tx?safe=matic:0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8\&id=multisig\_0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8\_0x69c289067c244b3e97109ec12398bd038ed315b42f4c6b1cd604ef9841bfbb1b)
* [Ethereum Mainnet](https://app.safe.global/transactions/tx?safe=eth:0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8\&id=multisig\_0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8\_0x1e542201cb4b4d35decc3bc81a88648a2cd71f485c34f5b05e3f0e9df87a6ff8)
* [Optimism](https://app.safe.global/transactions/tx?safe=oeth:0x14fc6a1a996A2EB889cF86e5c8cD17323bC85290\&id=multisig\_0x14fc6a1a996A2EB889cF86e5c8cD17323bC85290\_0x742c1a75d5d50489cf52ba91a4c2d8ba650a9e658c8aba10c2005da913d3935c)
* [BNB Smart Chain](https://app.safe.global/transactions/tx?safe=bnb:0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8\&id=multisig\_0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8\_0x2703b1c4b438117e4a9a9411e2634e343eee4b189c7cbdaac4c7e04585e758de)
* [Arbitrum One](https://app.safe.global/transactions/tx?safe=arb1:0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8\&id=multisig\_0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8\_0x07ab34ef7448f6ca0daff72685eda80ef6c54ba112a7f7b39d9e1f4725d2cf7a)
{% endhint %}

## Proposal Objectives

Goals of the proposal include further expansion (new BobSwap instances on Optimism, BNB Chain, and Arbitrum), increased brand awareness, and additional integration options. Several new inventory pools along with BobSwap (note: BobVault is the contract name and referred to as such below) allowance increases were proposed and accepted by the governance board.&#x20;

{% hint style="success" %}
Following the successful proposal, overall total supply increased **+32m BOB** (**20.5m** → **52.5m**)**.**
{% endhint %}

#### Polygon (9.5m → 11.5m)

1. Increase BobVault issuance allowance from **3,000,000 BOB** → **5,000,000 BOB**

#### Ethereum Mainnet (9m → 16m)

1. Increase BobSwap issuance allowance from **2,000,000 BOB** → **5,000,000 BOB**
2. Allocate **2,000,000 BOB** to **BOB/USDC 0.008%** inventory position on Kyberswap
3. Allocate **2,000,000 BOB** to **BOB/USDT 0.008%** inventory position on Kyberswap

#### Optimism (1m → 8m)

1. Allocate **5,000,000 BOB** to a new deployment of BobVault
2. Allocate **2,000,000 BOB** to **BOB/USDC 0.01%** inventory position on Uniswap V3

#### BNB Chain (1m → 10m)

1. Allocate **5,000,000 BOB** to a new deployment of BobVault
2. Allocate **2,000,000 BOB** to **BOB/USDC 0.008%** inventory position on Kyberswap
3. Allocate **2,000,000 BOB** to **BOB/USDT 0.008%** inventory position on Kyberswap

#### Arbitrum (0m → 7m)

1. Allocate **5,000,000 BOB** to a new deployment of BobVault
2. Allocate **2,000,000 BOB** to **BOB/USDC 0.01%** inventory position on Uniswap V3

{% hint style="info" %}
Newly deployed BobVault instances mirror latest Mainnet deployment, with the exception of changes in used collateral token addresses, see [GP 5](gp-5-enable-bobvault-bobswap-on-ethereum-mainnet.md) for reference.
{% endhint %}

{% hint style="success" %}
This proposal also enables BOB token contract deployed on Arbitrum. Governance on Arbitrum was also set up using the same 4/7 policy Safe with the same address - [0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8](https://app.safe.global/home?safe=arb1:0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8)
{% endhint %}

## **Transaction Details**

<details>

<summary>Polygon</summary>

Transaction [#27](https://app.safe.global/matic:0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8/transactions/tx?id=multisig\_0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8\_0x69c289067c244b3e97109ec12398bd038ed315b42f4c6b1cd604ef9841bfbb1b) in the Safe on Polygon contains 1 action:

**Action 1**

Allocate additional **2,000,000 BOB** (18 decimals) to the BobVault contract [`0x25E6505297b44f4817538fB2d91b88e1cF841B54`](https://polygonscan.com/address/0x25e6505297b44f4817538fb2d91b88e1cf841b54)by minting **2,000,000 BOB** to the BobVault contract. The action is executed by calling `mint` on the BOB token contract [`0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B`](https://polygonscan.com/address/0xb0b195aefa3650a6908f15cdac7d92f8a5791b0b#code)

</details>

<details>

<summary>Ethereum Mainnet</summary>

Transaction [#11](https://app.safe.global/eth:0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8/transactions/tx?id=multisig\_0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8\_0x1e542201cb4b4d35decc3bc81a88648a2cd71f485c34f5b05e3f0e9df87a6ff8) in the Safe on Mainnet contains **9** actions:

**Action 1**

Allocate additional **3,000,000 BOB** (18 decimals) to the BobVault contract [`0x15729Ac1795Fa02448a55D206005dC1914144a9F`](https://etherscan.io/address/0x15729ac1795fa02448a55d206005dc1914144a9f) by minting **3,000,000 BOB** to the BobVault contract. The action is executed by calling `mint` on the BOB token contract [`0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B`](https://etherscan.io/address/0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B).

**Action 2**

Mint **\~4,000,000 BOB** (18 decimals) to governance safe [`0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8`](https://etherscan.io/address/0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8)for further allocation into 2 inventory positions on Kyberswap. The action is executed by calling `mint` on the BOB token contract [`0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B`](https://etherscan.io/address/0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B).

_Note: Minting amount is slightly less than **4,000,000 BOB** to avoid leftover wei amount due to truncation errors._

**Action 3**

Approve **BOB** for usage in Kyberswap Position Manager Contract [`0x2B1c7b41f6A8F2b2bc45C3233a5d5FB3cD6dC9A8`](https://etherscan.io/address/0x2B1c7b41f6A8F2b2bc45C3233a5d5FB3cD6dC9A8). The action is executed by calling `approve` on the BOB token contract [`0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B`](https://etherscan.io/address/0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B).

**Action 4**

Approve 1 wei of **USDT** for usage in Kyberswap Position Manager Contract [`0x2B1c7b41f6A8F2b2bc45C3233a5d5FB3cD6dC9A8`](https://etherscan.io/address/0x2B1c7b41f6A8F2b2bc45C3233a5d5FB3cD6dC9A8). The action is executed by calling `approve` on the USDT token contract [`0xdAC17F958D2ee523a2206206994597C13D831ec7`](https://etherscan.io/token/0xdac17f958d2ee523a2206206994597c13d831ec7).

**Action 5**

Approve 1 wei of **USDC** for usage in Kyberswap Position Manager Contract [`0x2B1c7b41f6A8F2b2bc45C3233a5d5FB3cD6dC9A8`](https://etherscan.io/address/0x2B1c7b41f6A8F2b2bc45C3233a5d5FB3cD6dC9A8). The action is executed by calling `approve` on the USDC token contract [`0xA0b86991c6218b36c1d19D4a2e9Eb0cE3606eB48`](https://etherscan.io/token/0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48).

**Action 6**

Create and initialize pool **0.008% BOB/USDT** pool on Kyberswap. The action is executed by calling `createAndUnlockPoolIfNecessary` on the Kyberswap Position Manager contract [`0x2B1c7b41f6A8F2b2bc45C3233a5d5FB3cD6dC9A8`](https://etherscan.io/address/0x2B1c7b41f6A8F2b2bc45C3233a5d5FB3cD6dC9A8).

**Action 7**

Mint Kyberswap **0.008% BOB/USDT** inventory position using **\~2,000,000 BOB**. The action is executed by calling `mint` on the Kyberswap Position Manager contract [`0x2B1c7b41f6A8F2b2bc45C3233a5d5FB3cD6dC9A8`](https://etherscan.io/address/0x2B1c7b41f6A8F2b2bc45C3233a5d5FB3cD6dC9A8).

_Used tick range: `[-276325, -276323]`, as **BOB** has 18 decimals and **USDT** has 6 decimals_

**Action 8**

Create and initialize pool **0.008% USDC/BOB** pool on Kyberswap. The action is executed by calling `createAndUnlockPoolIfNecessary` on the Kyberswap Position Manager contract [`0x2B1c7b41f6A8F2b2bc45C3233a5d5FB3cD6dC9A8`](https://etherscan.io/address/0x2B1c7b41f6A8F2b2bc45C3233a5d5FB3cD6dC9A8).

**Action 9**

Mint Kyberswap **0.008% USDC/BOB** inventory position using **\~2,000,000 BOB**. The action is executed by calling `mint` on the Kyberswap Position Manager contract [`0x2B1c7b41f6A8F2b2bc45C3233a5d5FB3cD6dC9A8`](https://etherscan.io/address/0x2B1c7b41f6A8F2b2bc45C3233a5d5FB3cD6dC9A8).

_Used tick range: `[276323, 276325]`, as **USDC** has 6 decimals and **BOB** has 18 decimals_

</details>

<details>

<summary>Optimism</summary>

Transaction [#5](https://app.safe.global/oeth:0x14fc6a1a996A2EB889cF86e5c8cD17323bC85290/transactions/tx?id=multisig\_0x14fc6a1a996A2EB889cF86e5c8cD17323bC85290\_0x742c1a75d5d50489cf52ba91a4c2d8ba650a9e658c8aba10c2005da913d3935c) in the Safe on Optimism contains 4 actions:

**Action 1**

Allocate **5,000,000 BOB** (18 decimals) to the BobVault contract [`0x8aEb89D5C689C2cf373Fe8b56c7A0cD5BDc74CE6`](https://optimistic.etherscan.io/address/0x8aeb89d5c689c2cf373fe8b56c7a0cd5bdc74ce6) by minting **5,000,000 BOB** to the BobVault contract. The action is executed by calling `mint` on the BOB token contract [`0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B`](https://optimistic.etherscan.io/address/0xb0b195aefa3650a6908f15cdac7d92f8a5791b0b).

**Action 2**

Mint **\~2,000,000 BOB** (18 decimals) to governance safe [`0x14fc6a1a996A2EB889cF86e5c8cD17323bC85290`](https://optimistic.etherscan.io/address/0x14fc6a1a996a2eb889cf86e5c8cd17323bc85290) for further allocation into 2 inventory positions on Uniswap V3. The action is executed by calling `mint` on the BOB token contract [`0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B`](https://optimistic.etherscan.io/address/0xb0b195aefa3650a6908f15cdac7d92f8a5791b0b).

_Minting amount is slightly less than **2,000,000 BOB** to avoid leftover wei amount due to truncation errors._

**Action 3**

Create and initialize pool **0.01% USDC/BOB** pool on Uniswap V3. The action is executed by calling `createAndInitializePoolIfNecessary` on the Uniswap V3 Position Manager contract [`0xC36442b4a4522E871399CD717aBDD847Ab11FE88`](https://optimistic.etherscan.io/address/0xC36442b4a4522E871399CD717aBDD847Ab11FE88).

**Action 4**

Mint Uniswap V3 **0.01% USDC/BOB** inventory position using **\~2,000,000 BOB**. The action is executed by calling `mint` on the Uniswap V3 Position Manager contract [`0xC36442b4a4522E871399CD717aBDD847Ab11FE88`](https://optimistic.etherscan.io/address/0xC36442b4a4522E871399CD717aBDD847Ab11FE88).

_Used tick range: `[276323, 276325]`, as **USDC** has 6 decimals and **BOB** has 18 decimals_

</details>

<details>

<summary>BNB Chain</summary>

Transaction [#7](https://app.safe.global/bnb:0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8/transactions/tx?id=multisig\_0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8\_0x2703b1c4b438117e4a9a9411e2634e343eee4b189c7cbdaac4c7e04585e758de) in the Safe on BNB Chain contains 8 actions:

**Action 1**

Allocate **5,000,000 BOB** (18 decimals) to the BobVault contract ([`0x61a57F1C82DA40e632C075D7812Af375Db23367c`](https://bscscan.com/address/0x61a57f1c82da40e632c075d7812af375db23367c)) by minting **5,000,000 BOB** to the BobVault contract. The action is executed by calling `mint` on the BOB token contract [`0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B`](https://bscscan.com/address/0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B).

**Action 2**

Mint **4,000,000 BOB** (18 decimals) to governance safe [`0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8`](https://bscscan.com/address/0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8) for further allocation into 2 inventory positions on Kyberswap. The action is executed by calling `mint` on the BOB token contract [`0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B`](https://bscscan.com/address/0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B).

**Action 3**

Approve 99996 wei of **USDT** for usage in Kyberswap Position Manager Contract [`0x2B1c7b41f6A8F2b2bc45C3233a5d5FB3cD6dC9A8`](https://bscscan.com/address/0x2B1c7b41f6A8F2b2bc45C3233a5d5FB3cD6dC9A8). The action is executed by calling `approve` on the USDT token contract [`0x55d398326f99059fF775485246999027B3197955`](https://bscscan.com/address/0x55d398326f99059ff775485246999027b3197955).

**Action 4**

Approve 99996 wei of **USDC** for usage in Kyberswap Position Manager Contract [`0x2B1c7b41f6A8F2b2bc45C3233a5d5FB3cD6dC9A8`](https://bscscan.com/address/0x2B1c7b41f6A8F2b2bc45C3233a5d5FB3cD6dC9A8). The action is executed by calling `approve` on the USDC token contract [`0x8AC76a51cc950d9822D68b83fE1Ad97B32Cd580d`](https://bscscan.com/address/0x8ac76a51cc950d9822d68b83fe1ad97b32cd580d).

**Action 5**

Create and initialize pool **0.008% USDT/BOB** pool on Kyberswap. The action is executed by calling `createAndUnlockPoolIfNecessary` on the Kyberswap Position Manager contract [`0x2B1c7b41f6A8F2b2bc45C3233a5d5FB3cD6dC9A8`](https://bscscan.com/address/0x2B1c7b41f6A8F2b2bc45C3233a5d5FB3cD6dC9A8).

**Action 6**

Mint Kyberswap **0.008% USDT/BOB** inventory position using **\~2,000,000 BOB**. The action is executed by calling `mint` on the Kyberswap Position Manager contract [`0x2B1c7b41f6A8F2b2bc45C3233a5d5FB3cD6dC9A8`](https://bscscan.com/address/0x2B1c7b41f6A8F2b2bc45C3233a5d5FB3cD6dC9A8).

_Used tick range: `[-1, 1]`, as both tokens have 18 decimals_

**Action 7**

Create and initialize pool **0.008% USDC/BOB** pool on Kyberswap. The action is executed by calling `createAndUnlockPoolIfNecessary` on the Kyberswap Position Manager contract [`0x2B1c7b41f6A8F2b2bc45C3233a5d5FB3cD6dC9A8`](https://bscscan.com/address/0x2B1c7b41f6A8F2b2bc45C3233a5d5FB3cD6dC9A8).

**Action 8**

Mint Kyberswap **0.008% USDC/BOB** inventory position using **\~2,000,000 BOB**. The action is executed by calling `mint` on the Kyberswap Position Manager contract [`0x2B1c7b41f6A8F2b2bc45C3233a5d5FB3cD6dC9A8`](https://bscscan.com/address/0x2B1c7b41f6A8F2b2bc45C3233a5d5FB3cD6dC9A8).

_Used tick range: `[-1, 1]`, as both tokens have 18 decimals_

</details>

<details>

<summary>Arbitrum One</summary>

Transaction [#1](https://app.safe.global/arb1:0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8/transactions/tx?id=multisig\_0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8\_0x07ab34ef7448f6ca0daff72685eda80ef6c54ba112a7f7b39d9e1f4725d2cf7a) in the Safe on Arbitrum contains 5 actions:

**Action 1**

Allocate **5,000,000 BOB** (18 decimals) to the BobVault contract [`0x72e6B59D4a90ab232e55D4BB7ed2dD17494D62fB`](https://arbiscan.io/address/0x72e6b59d4a90ab232e55d4bb7ed2dd17494d62fb) by minting **5,000,000 BOB** to the BobVault contract. The action is executed by calling `mint` on the BOB token contract [`0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B`](https://arbiscan.io/address/0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B).

**Action 2**

Mint **\~2,000,000 BOB** (18 decimals) to governance safe [`0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8`](https://arbiscan.io/address/0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8) for further allocation into 2 inventory positions on Uniswap V3. The action is executed by calling `mint` on the BOB token contract [`0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B`](https://arbiscan.io/address/0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B).

_Minting amount is slightly less than **2,000,000 BOB** to avoid leftover wei amount due to truncation errors._

**Action 3**

Approve **BOB** for usage in Uniswap V3 Position Manager Contract [`0xC36442b4a4522E871399CD717aBDD847Ab11FE88`](https://arbiscan.io/address/0xC36442b4a4522E871399CD717aBDD847Ab11FE88). The action is executed by calling `approve` on the BOB token contract [`0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B`](https://arbiscan.io/address/0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B).

**Action 4**

Create and initialize pool **0.01% BOB/USDC** pool on Uniswap V3. The action is executed by calling `createAndInitializePoolIfNecessary` on the Uniswap V3 Position Manager contract [`0xC36442b4a4522E871399CD717aBDD847Ab11FE88`](https://arbiscan.io/address/0xC36442b4a4522E871399CD717aBDD847Ab11FE88).

**Action 5**

Mint Uniswap V3 **0.01% BOB/USDC** inventory position using **\~2,000,000 BOB**. The action is executed by calling `mint` on the Uniswap V3 Position Manager contract [`0xC36442b4a4522E871399CD717aBDD847Ab11FE88`](https://arbiscan.io/address/0xC36442b4a4522E871399CD717aBDD847Ab11FE88).

_Used tick range: `[-276325, -276323]`, as **BOB** has 18 decimals and **USDC** has 6 decimals_

</details>

## Additional Verification

### Verify new BobVault deployments

### **Optimism**

```bash
$ cast call --rpc-url https://rpc.ankr.com/optimism 0x8aEb89D5C689C2cf373Fe8b56c7A0cD5BDc74CE6 'owner() (address)'
0x14fc6a1a996A2EB889cF86e5c8cD17323bC85290

$ cast call --rpc-url https://rpc.ankr.com/optimism 0x8aEb89D5C689C2cf373Fe8b56c7A0cD5BDc74CE6 'admin() (address)'
0x14fc6a1a996A2EB889cF86e5c8cD17323bC85290

$ cast call --rpc-url https://rpc.ankr.com/optimism 0x8aEb89D5C689C2cf373Fe8b56c7A0cD5BDc74CE6 'collateral(address) (uint128 balance,uint128 buffer,uint96 dust,address yield,uint128 price,uint64 inFee,uint64 outFee,uint256 maxBalance,uint256 maxInvested)' 0x7F5c764cBc14f9669B88837ca1490cCa17c31607
0
0
0
0x0000000000000000000000000000000000000000
1000000
10000000000000
100000000000000
340282366920938463463374607431768211455
0

$ cast call --rpc-url https://rpc.ankr.com/optimism 0x8aEb89D5C689C2cf373Fe8b56c7A0cD5BDc74CE6 'collateral(address) (uint128 balance,uint128 buffer,uint96 dust,address yield,uint128 price,uint64 inFee,uint64 outFee,uint256 maxBalance,uint256 maxInvested)' 0x94b008aA00579c1307B0EF2c499aD98a8ce58e58
0
0
0
0x0000000000000000000000000000000000000000
1000000
10000000000000
100000000000000
1000000000000
0
```

### BNB Chain

```bash
$ cast call --rpc-url https://rpc.ankr.com/bsc 0x61a57F1C82DA40e632C075D7812Af375Db23367c 'owner() (address)'
0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8

$ cast call --rpc-url https://rpc.ankr.com/bsc 0x61a57F1C82DA40e632C075D7812Af375Db23367c 'admin() (address)'
0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8

$ cast call --rpc-url https://rpc.ankr.com/bsc 0x61a57F1C82DA40e632C075D7812Af375Db23367c 'collateral(address) (uint128 balance,uint128 buffer,uint96 dust,address yield,uint128 price,uint64 inFee,uint64 outFee,uint256 maxBalance,uint256 maxInvested)' 0x8AC76a51cc950d9822D68b83fE1Ad97B32Cd580d
0
0
0
0x0000000000000000000000000000000000000000
1000000000000000000
10000000000000
100000000000000
340282366920938463463374607431768211455
0

$ cast call --rpc-url https://rpc.ankr.com/bsc 0x61a57F1C82DA40e632C075D7812Af375Db23367c 'collateral(address) (uint128 balance,uint128 buffer,uint96 dust,address yield,uint128 price,uint64 inFee,uint64 outFee,uint256 maxBalance,uint256 maxInvested)' 0x55d398326f99059fF775485246999027B3197955
0
0
0
0x0000000000000000000000000000000000000000
1000000000000000000
10000000000000
100000000000000
1000000000000000000000000
0
```

### Arbitrum

```bash
$ cast call --rpc-url https://rpc.ankr.com/arbitrum 0x72e6B59D4a90ab232e55D4BB7ed2dD17494D62fB 'owner() (address)'
0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8

$ cast call --rpc-url https://rpc.ankr.com/arbitrum 0x72e6B59D4a90ab232e55D4BB7ed2dD17494D62fB 'admin() (address)'
0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8

$ cast call --rpc-url https://rpc.ankr.com/arbitrum 0x72e6B59D4a90ab232e55D4BB7ed2dD17494D62fB 'collateral(address) (uint128 balance,uint128 buffer,uint96 dust,address yield,uint128 price,uint64 inFee,uint64 outFee,uint256 maxBalance,uint256 maxInvested)' 0xFF970A61A04b1cA14834A43f5dE4533eBDDB5CC8
0
0
0
0x0000000000000000000000000000000000000000
1000000
10000000000000
100000000000000
340282366920938463463374607431768211455
0

$ cast call --rpc-url https://rpc.ankr.com/arbitrum 0x72e6B59D4a90ab232e55D4BB7ed2dD17494D62fB 'collateral(address) (uint128 balance,uint128 buffer,uint96 dust,address yield,uint128 price,uint64 inFee,uint64 outFee,uint256 maxBalance,uint256 maxInvested)' 0xFd086bC7CD5C481DCC9C85ebE478A1C0b69FCbb9
0
0
0
0x0000000000000000000000000000000000000000
1000000
10000000000000
100000000000000
1000000000000
0
```

{% hint style="info" %}
Inventory LPs validity can be verified using the following simulation test - [https://gist.github.com/k1rill-fedoseev/c7ca38a4a0a1d1980c905e430fa86685](https://gist.github.com/k1rill-fedoseev/c7ca38a4a0a1d1980c905e430fa86685)
{% endhint %}
