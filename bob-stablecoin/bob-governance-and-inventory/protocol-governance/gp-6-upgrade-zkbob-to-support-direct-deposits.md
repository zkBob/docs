# GP 6: Upgrade zkBob to support direct deposits

{% hint style="success" %}
The proposal has been confirmed and executed by [https://polygonscan.com/tx/0xf2c0a7e661691354fc9bf01ff4e00a3d1ab515afc4b0da3305c7d7e90f47519f](https://polygonscan.com/tx/0xf2c0a7e661691354fc9bf01ff4e00a3d1ab515afc4b0da3305c7d7e90f47519f)
{% endhint %}

### Introduction to direct deposits

Direct deposits allow anyone to interact with zkBob protocol by submitting deposits directly to zk addresses.

Direct deposits are subject to the newly introduced limits at the time of submission

* **dailyUserDirectDepositCap** - limit on the amount for daily direct deposits submitted by a single user
* **directDepositCap** - limit on the amount of a single direct deposit

Each direct deposit is subject to a submission fee at the time of its submission:

* **directDepositFee** - direct deposit fee

Each direct deposit left unprocessed by the relayer for a certain amount of time can be refunded in full by the user:

* **directDepositTimeout** - configured direct deposit refund timeout

{% hint style="info" %}
Learn more about Direct Deposit functionality and how to use in our [hackathon instructions](../../../resources/hackathons/zkbob-direct-deposits.md).
{% endhint %}

### Proposal objective

Upgrade existing zkBob pool with the support for direct deposits using the following configuration:

1. **dailyUserDirectDepositCap** - 10,000 **BOB** (18 decimals)
2. **directDepositCap** - 1,000 **BOB** (18 decimals)
3. **directDepositFee** - 0.1 **BOB** (18 decimals)
4. **directDepositTimeout** - 24 hours ↔ 86,400 seconds

The module for direct deposits is deployed in a separate contract [0x668c5286eAD26fAC5fa944887F9D2F20f7DDF289](https://polygonscan.com/address/0x668c5286eAD26fAC5fa944887F9D2F20f7DDF289). It owner is configured to the governance multisig ([0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8](https://polygonscan.com/address/0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8)). See [Additional verification](https://www.notion.so/Additional-verification-70d2b873ad8f4c479cda335044fbcc14) for verification. The direct deposits module address is hardcoded into the new zkBob pool implementation contract proposed for upgrade.

The upgrade also adds a new snark verifier for direct deposit batch verification - [0x9a7B4198065efE631a962e737bDfE1f44f2CB3EE](https://polygonscan.com/address/0x9a7B4198065efE631a962e737bDfE1f44f2CB3EE)

The snark verifier for transfers is redeployed to reflect changes in the transfer verification snark - [0xA86C511832eAd78d30ad49711874a9F3a1dfb840](https://polygonscan.com/address/0xA86C511832eAd78d30ad49711874a9F3a1dfb840)

The snark verifier for tree updates is left unchanged and is reused from the previous deployment - [0x82907eAeB25D248dC82033E45b00A3E012Ba2d0D](https://polygonscan.com/address/0x82907eAeB25D248dC82033E45b00A3E012Ba2d0D)

### Proposal breakdown

The corresponding transaction in the governance safe is [transaction #26](https://app.safe.global/matic:0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8/transactions/tx?id=multisig\_0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8\_0x24c9789d8f5718b6e3bb8f6ce9e97493f0685e91f07f5d8b8bd0e583436dfe44). The transaction contains 3 actions:

#### Action 1

zkBobPool contract upgrade [`0x72e6B59D4a90ab232e55D4BB7ed2dD17494D62fB`](https://polygonscan.com/address/0x72e6B59D4a90ab232e55D4BB7ed2dD17494D62fB). The new implementation [`0x0eDcE5CAf830c6b845503001D8378b0d4F3b89bB`](https://polygonscan.com/address/0x0eDcE5CAf830c6b845503001D8378b0d4F3b89bB) is applied through the `upgradeTo` call (the selector is `0x3659cfe6`).

#### Action 2

&#x20;`setLimits` call (the selector is `0xe8fd02e4`) from the zkBobPool contract [`0x72e6B59D4a90ab232e55D4BB7ed2dD17494D62fB`](https://polygonscan.com/address/0x72e6B59D4a90ab232e55D4BB7ed2dD17494D62fB). The method is called to update limits related to direct deposits in tier `0`. The current limits for the tier `0` set in the pool contract are:

```
Cap: 1'000'000 BOB
dailyDepositCap: 300'000 BOB
dailyWithdrawalCap: 100'000 BOB
dailyUserDepositCap: 10'000 BOB
depositCap: 10'000 BOB
dailyUserDirectDepositCap: 10'000 BOB
directDepositCap: 1'000 BOB
```

The event is emitted with the same value.

#### Action 3

&#x20;`setLimits` call (the selector is `0xe8fd02e4`) from the zkBobPool contract [`0x72e6B59D4a90ab232e55D4BB7ed2dD17494D62fB`](https://polygonscan.com/address/0x72e6B59D4a90ab232e55D4BB7ed2dD17494D62fB). The method is called to update limits related to direct deposits in tier `1`. The current limits for the tier `1` set in the pool contract are:

```
tvlCap: 1'000'000 BOB
dailyDepositCap: 300'000 BOB
dailyWithdrawalCap: 100'000 BOB
dailyUserDepositCap: 100'000 BOB
depositCap: 100'000 BOB
dailyUserDirectDepositCap: 10'000 BOB
directDepositCap: 1'000 BOB
```

The event is emitted with the same value.

### Additional verification

Diff between previous and new implementations of `ZkBobPool` -[https://diffy.org/diff/e74278e64eab5](https://diffy.org/diff/e74278e64eab5) (auto-generated by [https://github.com/zkBob/zkbob-contracts/actions/runs/4250762810](https://github.com/zkBob/zkbob-contracts/actions/runs/4250762810))

Configuration of proposed contracts can be checked using the following commands:

```coq
$ cast call --rpc-url https://rpc.ankr.com/polygon 0x0eDcE5CAf830c6b845503001D8378b0d4F3b89bB 'pool_id() (uint24)'
0

$ cast call --rpc-url https://rpc.ankr.com/polygon 0x0eDcE5CAf830c6b845503001D8378b0d4F3b89bB 'token() (address)'
0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B

$ cast call --rpc-url https://rpc.ankr.com/polygon 0x0eDcE5CAf830c6b845503001D8378b0d4F3b89bB 'direct_deposit_queue() (address)'
0x668c5286eAD26fAC5fa944887F9D2F20f7DDF289

$ cast call --rpc-url https://rpc.ankr.com/polygon 0x0eDcE5CAf830c6b845503001D8378b0d4F3b89bB 'transfer_verifier() (address)'
0xA86C511832eAd78d30ad49711874a9F3a1dfb840

$ cast call --rpc-url https://rpc.ankr.com/polygon 0x0eDcE5CAf830c6b845503001D8378b0d4F3b89bB 'tree_verifier() (address)'
0x82907eAeB25D248dC82033E45b00A3E012Ba2d0D

$ cast call --rpc-url https://rpc.ankr.com/polygon 0x0eDcE5CAf830c6b845503001D8378b0d4F3b89bB 'batch_deposit_verifier() (address)'
0x9a7B4198065efE631a962e737bDfE1f44f2CB3EE


$ cast call --rpc-url https://rpc.ankr.com/polygon 0x668c5286eAD26fAC5fa944887F9D2F20f7DDF289 'pool() (address)'
0x72e6B59D4a90ab232e55D4BB7ed2dD17494D62fB

$ cast call --rpc-url https://rpc.ankr.com/polygon 0x668c5286eAD26fAC5fa944887F9D2F20f7DDF289 'token() (address)'
0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B

$ cast call --rpc-url https://rpc.ankr.com/polygon 0x668c5286eAD26fAC5fa944887F9D2F20f7DDF289 'pool_id() (uint24)'
0

$ cast call --rpc-url https://rpc.ankr.com/polygon 0x668c5286eAD26fAC5fa944887F9D2F20f7DDF289 'owner() (address)'
0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8

$ cast call --rpc-url https://rpc.ankr.com/polygon 0x668c5286eAD26fAC5fa944887F9D2F20f7DDF289 'admin() (address)'
0xd4a3D9Ca00fa1fD8833D560F9217458E61c446d8

$ cast call --rpc-url https://rpc.ankr.com/polygon 0x668c5286eAD26fAC5fa944887F9D2F20f7DDF289 'implementation() (address)'
0x7883cfA8D367c433985fa320B4491489e9D3F6cD

$ cast call --rpc-url https://rpc.ankr.com/polygon 0x668c5286eAD26fAC5fa944887F9D2F20f7DDF289 'directDepositTimeout() (uint256)'
86400

$ cast call --rpc-url https://rpc.ankr.com/polygon 0x668c5286eAD26fAC5fa944887F9D2F20f7DDF289 'directDepositFee() (uint256)'
100000000
```
