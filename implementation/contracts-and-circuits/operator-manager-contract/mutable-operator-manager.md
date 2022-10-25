---
description: The simple operator manager with relayer change support
---

# Mutable Operator Manager

This is a simple operator manager with single operator support which can be changed by the contract owner. There are no limits to the frequency at which operators can be changed. The Mutable operator manager contract also holds an operator URL address. This is used by clients to determine the current relayer's endpoint.

The initial operator address, feeReceiver (a second operator responsible for receiving fees)  and URL address is set using the contract constructor:

```solidity
constructor(address _operator, address _feeReceiver, string memory _operatorURI)
```

The Mutable operator manager has the following functions (along with the [protocol](./) implementation):

```solidity
function setOperator(address _operator, address _feeReceiver, string memory _endpoint) external onlyOwner
```

It can only be invoked by the contract owner. To provide unlimited access to the Pool set the `_addr` parameter to `address(0)` and any string (preference for an empty string `""`) for `_endpoint`.

To get the current operator URL use the following function:

```solidity
function operatorURI() external view returns(string memory)
```

This routine returns an empty string `""` when access to the Pool is granted for any sender.

### Source and Deployment data

* The contract source code: [MutableOperatorManager.sol](https://github.com/zkBob/zkbob-contracts/blob/master/src/zkbob/manager/MutableOperatorManager.sol)
* [Contract Addresses](../../deployed-contracts.md)
