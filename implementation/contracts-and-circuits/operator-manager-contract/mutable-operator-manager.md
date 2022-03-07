---
description: The simple operator manager with relayer change support
---

# Mutable Operator Manager

This is a simple operator manager with single operator support which can be changed by the contract owner. There are no limits to the frequency at which operators can be changed. The Mutable operator manager contract also holds an operator URL address. It is used by clients to determine the current relayer's endpoint.

The initial operator address and URL address is set using the contract constructor:

```solidity
constructor(address _addr, string memory _endpoint);
```

The Mutable operator manager has the following functions (along with the [protocol](./) implementation):

```solidity
function setOperator(address _addr, string memory _endpoint) external onlyOwner;
```

It can only be invoked by the contract owner.To provide unlimited access to the Pool  set the `_addr` parameter to `address(0)` and any string (preference for an empty string `""`) for `_endpoint`.

To get the current operator URL use the following function:

```solidity
function operatorURI() external view returns(string memory)
```

This routine returns an empty string `""` when access to the Pool is granted for any sender.

### Source and Deployment data

* The contract source code: [MutableOperatorManager.sol](https://github.com/zkBob/pool-evm-single-l1/blob/main/contracts/manager/MutableOperatorManager.sol)
* Mainnet contract address: _TBD_
* Testnet contract address: [0x78E276E79d026BDE5FD37df1c04554Ca9C993Ab4](https://kovan.etherscan.io/address/0x78E276E79d026BDE5FD37df1c04554Ca9C993Ab4)
