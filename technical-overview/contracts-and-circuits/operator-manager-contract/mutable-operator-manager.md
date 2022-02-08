---
description: The simple operator manager with relayer change support
---

# Mutable Operator Manager

It's just a simple operator manager with a single operator support which can be changed by the contract owner. There are no limits for operator changing frequency. The Mutable operator manager contract also holds an operator URL address. It's used by clients to determine current relayer's endpoint.

The initial operator address and URL address sets with the contract constructor:

```solidity
constructor(address _addr, string memory _endpoint);
```

So the Mutable operator manager has the following functions (along with the [protocol](./) implementation):

```solidity
function setOperator(address _addr, string memory _endpoint) external onlyOwner;
```

It can be invoked by the contract owner only. If you want to provide unlimited access to the Pool please set `address(0)` for `_addr` parameter and any string (preferred a void string `""`) for `_endpoint`.

To get the current operator URL use the following function:

```solidity
function operatorURI() external view returns(string memory)
```

This routine will return a void string `""` when access to the Pool will granted for the any sender.

### Source and Deployment data

The contract source code: [MutableOperatorManager.sol](https://github.com/zkBob/pool-evm-single-l1/blob/main/contracts/manager/MutableOperatorManager.sol)

Mainnet contract address:&#x20;

Testnet contract address: [0x78E276E79d026BDE5FD37df1c04554Ca9C993Ab4](https://kovan.etherscan.io/address/0x78E276E79d026BDE5FD37df1c04554Ca9C993Ab4)
