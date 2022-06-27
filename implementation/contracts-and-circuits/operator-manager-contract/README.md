---
description: Manages relayers access to the Pool
---

# Operator Manager Contract

{% hint style="info" %}
The **operator** is a native chain address which interacts with the Pool contract. In general the relayer or a standalone user can become the operator. In most cases the operator is a relayer.
{% endhint %}

The operator manager contract delimits access to the Pool. Transactions should be included in the Merkle tree strictly in a serial manner. The relayer node (or a user in case of direct Pool interaction) should calculate Merkle tree proof (zkSNARK) before sending a transaction. But the transaction will revert if the Merkle tree has changed during this calculation. If several relayers send transactions simultaneously collisions will appear and the transaction will be unsuccessful (along with spent gas fees).

To prevent this case we restrict Pool interactions using the Operator Manager contract. The Operator manager contract has two mandatory methods:

```solidity
function is_operator() external view returns(bool);
```

This routine returns true when the transaction origin sender can interact with the Pool currently.

```solidity
function operator() external view returns(address);
```

This function returns a current operator address (native chain). The are two extra cases for the `operator` function:

* There are several operators allowed to interact with Pool at this time (e.g. primary and reserve operators). In this case the `operator` function should return any of these addresses.
* The are no limits for Pool interaction (anybody can send transactions to the Pool). The `operator` function should returns `address(0)`

### Source and Deployment data

* The contract interface source code: [IOperatorManager.sol](https://github.com/zkBob/pool-evm-single-l1/blob/main/contracts/manager/interfaces/IOperatorManager.sol)
* For the contract implementation please refer to the [actual operator manager page](mutable-operator-manager.md#source-and-deployment-data)
