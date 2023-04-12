# GP 5: Enable BobVault (BobSwap) on Ethereum Mainnet

{% hint style="success" %}
The proposal has been confirmed and executed by [https://etherscan.io/tx/0x1e33247389a04b8ffea082267821a9ccf2d79826812035d1256cb60b477bc270](https://etherscan.io/tx/0x1e33247389a04b8ffea082267821a9ccf2d79826812035d1256cb60b477bc270)
{% endhint %}

See [GP#3 ](gp-3-enable-bobvault-bobswap-for-public-use.md)for a description of BobVault.

## Proposal objective

In order to pursue further expansion, increase brand awareness and explore more integration options, we propose to enable **BobVault** on Ethereum Mainnet.

BobVault deployed on Ethereum Mainnet differs from the original audited version in that it includes more stricter limits for max collateral balance. The diff of changes can be found [HERE](https://github.com/zkBob/zkbob-contracts/compare/c78a75c06aa43c708fa8422c8ceab7ea06e038d6...5202aed484df76ced3a79bea2b693ffbf45103f2).

The contract was pre-deployed at [0x15729Ac1795Fa02448a55D206005dC1914144a9F](https://etherscan.io/address/0x15729Ac1795Fa02448a55D206005dC1914144a9F) on 20.02.23 from commit [ada425fbb6f29a50d26e89956204fb8b2b32b8d6](https://github.com/zkBob/zkbob-contracts/tree/ada425fbb6f29a50d26e89956204fb8b2b32b8d6). The collaterals were configured as described, owner of the BobVault was set to the governance multisig ([0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8](https://etherscan.io/address/0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8)) after configuration. See [Additional verification](https://www.notion.so/Additional-verification-962dc66f98634005996cbbaaccb1e744) for verification.

For the purpose of Mainnet deployment, the internal Bob protocol risk-assessment team approved the **BOB** issuance limit through BobVault to **2,000,000 BOB**, alongside with the following collateral configuration:

**USDC:**

1. **price** - 1 (6 decimals)
2. **inFee** - 0.001% (18 decimals)
3. **outFee** - 0.01% (18 decimals)
4. **yield** - `address(0)` - yield earning disabled
5. **buffer** - 0 USDC (6 decimals)
6. **dust** - \*\*\*\*0 USDC (6 decimals)
7. **maxBalance** - `type(uint128).max` - unrestricted
8. **maxInvested** - 0 USDC (6 decimals)

**USDT:**

1. **price** - 1 (6 decimals)
2. **inFee** - 0.001% (18 decimals)
3. **outFee** - 0.01% (18 decimals)
4. **yield** - `address(0)` - yield earning disabled
5. **buffer** - 0 USDT (6 decimals)
6. **dust** - \*\*\*\*0 USDT (6 decimals)
7. **maxBalance** - 1,000,000 USDT (6 decimals)
8. **maxInvested** - 0 USDT (6 decimals)

**DAI:**

1. **price** - 1 (18 decimals)
2. **inFee** - 0.001% (18 decimals)
3. **outFee** - 0.01% (18 decimals)
4. **yield** - `address(0)` - yield earning disabled
5. **buffer** - 0 DAI (18 decimals)
6. **dust** - \*\*\*\*0 DAI (18 decimals)
7. **maxBalance** - 1,000,000 DAI (18 decimals)
8. **maxInvested** - 0 DAI (18 decimals)

The main goal behind choosing such parameters - allow BobVault to compete with existing **BOB** pools on Uniswap. e.g. current slippage for swapping USDC → BOB on Uniswap V3 pool USDC/BOB is 0.001%, for swapping BOB → USDC is 0.019%

### Proposal breakdown

The corresponding transaction in the governance safe is[ transaction #10](https://app.safe.global/eth:0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8/transactions/tx?id=multisig\_0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8\_0x7098c6594535272e35904aa4065d040d08cbfe4cf3a482a84b284f30c7245c5e). The transaction contains 1 action:

#### Action 1

Allocate **2,000,000 BOB** (18 decimals) to the BobVault contract ([0x15729Ac1795Fa02448a55D206005dC1914144a9F](https://etherscan.io/address/0x15729Ac1795Fa02448a55D206005dC1914144a9F)) by generating **BOB** token inventory. The action is executed by calling `mint` on the **BOB** token contract [`0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B`](https://etherscan.io/address/0xb0b195aefa3650a6908f15cdac7d92f8a5791b0b#code)

### Additional verification

Existing configuration parameters for collaterals can be checked by calling the  `collateral(address)` function in the BobVault contract:

```coq
$ cast call --rpc-url https://rpc.ankr.com/eth 0x15729Ac1795Fa02448a55D206005dC1914144a9F 'owner() (address)'
0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8

$ cast call --rpc-url https://rpc.ankr.com/eth 0x15729Ac1795Fa02448a55D206005dC1914144a9F 'admin() (address)'
0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8

$ cast call --rpc-url https://rpc.ankr.com/eth 0x15729Ac1795Fa02448a55D206005dC1914144a9F 'collateral(address) (uint128 balance,uint128 buffer,uint96 dust,address yield,uint128 price,uint64 inFee,uint64 outFee,uint256 maxBalance,uint256 maxInvested)' 0xA0b86991c6218b36c1d19D4a2e9Eb0cE3606eB48
0
0
0
0x0000000000000000000000000000000000000000
1000000
10000000000000
100000000000000
340282366920938463463374607431768211455
0

$ cast call --rpc-url https://rpc.ankr.com/eth 0x15729Ac1795Fa02448a55D206005dC1914144a9F 'collateral(address) (uint128 balance,uint128 buffer,uint96 dust,address yield,uint128 price,uint64 inFee,uint64 outFee,uint256 maxBalance,uint256 maxInvested)' 0xdAC17F958D2ee523a2206206994597C13D831ec7
0
0
0
0x0000000000000000000000000000000000000000
1000000
10000000000000
100000000000000
1000000000000
0

$ cast call --rpc-url https://rpc.ankr.com/eth 0x15729Ac1795Fa02448a55D206005dC1914144a9F 'collateral(address) (uint128 balance,uint128 buffer,uint96 dust,address yield,uint128 price,uint64 inFee,uint64 outFee,uint256 maxBalance,uint256 maxInvested)' 0x6B175474E89094C44Da98b954EedeAC495271d0F
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
