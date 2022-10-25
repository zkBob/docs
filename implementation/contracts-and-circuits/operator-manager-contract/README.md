---
description: Manages relayers access to the Pool
---

# Operator Manager Contract

{% hint style="info" %}
The **operator** is a native chain address which interacts with the Pool contract. In general the relayer or a standalone user can become the operator. In most cases the operator is a relayer.
{% endhint %}

The Operator Manager contract organizes and limits operators access to the Pool. Transactions should be appended to the Merkle tree strictly in a serial manner. The relayer node (or a user in case of direct Pool interaction) should calculate a Merkle tree proof (zkSNARK) before sending a transaction.&#x20;

However, the transaction will revert if the Merkle tree has changed during this calculation. If several relayers send transactions simultaneously collisions will appear and the transaction will be unsuccessful (along with spent gas fees).

To prevent this case we restrict Pool interactions using the Operator Manager contract. The Operator manager contract has three methods:

#### 1) `isOperator`

```solidity
function isOperator(address _addr) external view returns (bool);
```

Returns true when the transaction origin sender is the operator and can interact with the Pool.

#### 2) `isOperatorFeeReceiver`

```solidity
function isOperatorFeeReceiver(address _operator, address _addr) external view returns (bool);
```

Checks if the primary operator is also the fee receiver. There are two operator accounts. The first (\_operator) sends service transactions, the second (\_feeReceiver) receives fees and covers expenses. **These should not be the same account.**

#### 3) `operatorURI`

```solidity
function operatorURI() external view returns (string memory);
```

This string URI identifier for the Operator (typically the URL endpoint of the  relayer).

### Source and Deployment data

* The contract interface source code: [IOperatorManager.sol](https://github.com/zkBob/zkbob-contracts/blob/master/src/interfaces/IOperatorManager.sol)
* For the contract implementation please refer to the [actual operator manager page](mutable-operator-manager.md#source-and-deployment-data)
