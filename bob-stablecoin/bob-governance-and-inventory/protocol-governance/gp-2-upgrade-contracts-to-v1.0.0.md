---
description: GP 2
---

# GP 2: Upgrade Contracts to v1.0.0

The following changes were made as a result of the [Security Audit conducted by ChainSecurity](https://chainsecurity.com/security-audit/zkbob-smart-contracts/) and published on January 5, 2023.&#x20;

{% hint style="success" %}
* GP #2
* Timestamp: Jan-10-2023 11:29:05 AM +UTC
* Tx: [0x755e2e240563b151e96b9bb52721e8361e1782697b092f32bb9fc23a8797cfb2](https://polygonscan.com/tx/0x755e2e240563b151e96b9bb52721e8361e1782697b092f32bb9fc23a8797cfb2)
{% endhint %}

The transaction contained 6 actions described below.

## 1) `BobToken` contract upgrade

* `BobToken` contract\
  [0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B](https://polygonscan.com/address/0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B)
* New implementation contract\
  [0x525b4E120dDC602fF055Aa86803acD7D71F0c753](https://polygonscan.com/address/0x525b4E120dDC602fF055Aa86803acD7D71F0c753#code).

The upgrade uses the `upgradeToAndCall` method (the selector is `0x4f1ef286`) and is combined with the `DOMAIN_SEPARATOR` call (the selector is `0x3644e515`). The method call is only used in tandem with Tenderly to check that the domain separator is not being changed from the old implementation to the new one during the upgrade.

## 2) `BobVault` contract upgrade

* `BobVault` contract\
  [0x25E6505297b44f4817538fB2d91b88e1cF841B54](https://polygonscan.com/address/0x25E6505297b44f4817538fB2d91b88e1cF841B54))
* New implementation contract [0xd96587Eaa3CD5957EeC567df6BdF0B816792D125](https://polygonscan.com/address/0xd96587Eaa3CD5957EeC567df6BdF0B816792D125#code)&#x20;

Applied with the `upgradeTo` call (the selector is `0x3659cfe6`).

## 3) `zkBobPool` contract upgrade

* `zkBobPool` contract [0x72e6B59D4a90ab232e55D4BB7ed2dD17494D62fB](https://polygonscan.com/address/0x72e6B59D4a90ab232e55D4BB7ed2dD17494D62fB)&#x20;
* New implementation contract [0x4b8c0B14AA7CB5a7cFF3546415bBDCAcd7C75a2E](https://polygonscan.com/address/0x4b8c0B14AA7CB5a7cFF3546415bBDCAcd7C75a2E#code)

Applied with the `upgradeTo` call (the selector is `0x3659cfe6`).

{% hint style="info" %}
Note: the zkBobPool implementation contract introduces new events which are emitted when the pool parameters are being setup/changed. The next three actions are required to emit the events for the current set of parameters. These events can be displayed later through an analytics dashboard.
{% endhint %}

## 4) Update relayer management address

The `setOperatorManager` method was called from the `zkBobPool` contract (the selector is `0xc41100fa`). The method emits the event `UpdateOperatorManager` with the contract address responsible for management of the pool operators (relayers). The value set in the pool contract is [0x8aeb89d5c689c2cf373fe8b56c7a0cd5bdc74ce6](https://polygonscan.com/address/0x8aeb89d5c689c2cf373fe8b56c7a0cd5bdc74ce6#code), so the event emitted the same value.

## 5) Reset limits for tier 0 in `zkBobPool` contract

The `setLimits` method was called from the `zkBobPool` contract (the selector is `0x54b59153`). The method emits the event `UpdateLimits` with the limits configuration for accounts belonging to [tier 0](../../../zkbob-overview/deposit-and-withdrawal-limits.md#tier-example). The current limits for the tier 0 set in the pool contract are:

```
tvlCap: 1'000'000 BOB 
dailyDepositCap: 300'000 BOB 
dailyWithdrawalCap: 100'000 BOB
dailyUserDepositCap: 10'000
depositCap: 10'000 BOB
```

## 6) Reset limits for tier 1 in `zkBobPool` contract

The `setLimits` method was called from the `zkBobPool` contract (the selector is `0x54b59153`). The method emits the event `UpdateLimits` with the limits configuration for accounts belonging to [tier 1](../../../zkbob-overview/deposit-and-withdrawal-limits.md#tier-example). The current limits for the tier 1 set in the pool contract are:

```
tvlCap: 1'000'000 BOB 
dailyDepositCap: 300'000 BOB 
dailyWithdrawalCap: 100'000 BOB
dailyUserDepositCap: 100'000
depositCap: 100'000 BOB
```

## Additional Verification for Updates&#x20;

To simplify the check that the new implementations were deployed with the same parameters as the current implementations, [this shell script](https://gist.github.com/k1rill-fedoseev/28a593b75cd2e34eb37534ede4ed0dc0) can be used. Here is the output from the first part of the script:

```
Old implementations:
BobToken: 0x98DB3A72BeF2145A8F8d8B94F81317341Af2b08C
BobVault: 0x15B8C75c024acba8c114C21F42eb515A762c0014
ZkBobPool: 0x85afa00f38aD5F353C2B80985407b8E8A27eA38f
New implementations:
BobToken: 0x525b4E120dDC602fF055Aa86803acD7D71F0c753
BobVault: 0xd96587Eaa3CD5957EeC567df6BdF0B816792D125
ZkBobPool: 0x4b8c0B14AA7CB5a7cFF3546415bBDCAcd7C75a2E
Checking static fields:

BobTokenOld.DOMAIN_SEPARATOR() == 0xde8d39718fa34d2ebac775c3e965466635eaf72920c6ea519f1d49359b1068a8
BobTokenNew bytecode contains 0xde8d39718fa34d2ebac775c3e965466635eaf72920c6ea519f1d49359b1068a8 1 times
BobTokenOld.name() == BOB
BobTokenNew.name() == BOB
BobTokenOld.symbol() == BOB
BobTokenNew.symbol() == BOB
BobTokenOld.decimals() == 18
BobTokenNew.decimals() == 18

BobVaultOld.bobToken() == 0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B
BobVaultNew.bobToken() == 0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B

ZkBobPoolOld.pool_id() == 0
ZkBobPoolNew.pool_id() == 0
ZkBobPoolOld.token() == 0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B
ZkBobPoolNew.token() == 0xB0B195aEFA3650A6908f15CdaC7D92F8a5791B0B
ZkBobPoolOld.transfer_verifier() == 0x51585f5Af7B5f0bbf7F91fE8919fbfF362A2fd95
ZkBobPoolNew.transfer_verifier() == 0x51585f5Af7B5f0bbf7F91fE8919fbfF362A2fd95
ZkBobPoolOld.tree_verifier() == 0x82907eAeB25D248dC82033E45b00A3E012Ba2d0D
ZkBobPoolNew.tree_verifier() == 0x82907eAeB25D248dC82033E45b00A3E012Ba2d0D
```

This script also allows you to verify delta between old and new implementations. This can also be reviewed using the links below:

* BobToken -[https://diffy.org/diff/3da4f5fc7cdad](https://diffy.org/diff/3da4f5fc7cdad)
* BobVault -[https://diffy.org/diff/83a53285564f2](https://diffy.org/diff/83a53285564f2)
* zkBobPool -[https://diffy.org/diff/e938d5d7039f5](https://diffy.org/diff/e938d5d7039f5)
